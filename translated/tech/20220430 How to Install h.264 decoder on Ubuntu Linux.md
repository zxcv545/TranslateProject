[#]: subject: "How to Install h.264 decoder on Ubuntu Linux"
[#]: via: "https://itsfoss.com/install-h-264-decoder-ubuntu/"
[#]: author: "Abhishek Prakash https://itsfoss.com/author/abhishek/"
[#]: collector: "lujun9972"
[#]: translator: "hwlife"
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

怎样在 Ubuntu Linux 安装 h.264 解码器
======

当你开始使用 [新安装的 Ubuntu 系统][1] 并尝试打开一个 MP4 文件进行播放时，它可能会显示一个错误，即：

_**播放这个文件要求 H.264 (高端类) 解码器 ， 但是没有安装。**_

![当播放特定媒体文件时，Ubuntu 的默认视频播放器会显示错误][2]

你可能会猜到这是怎么了。系统没有安装所需的多媒体解码器阻止了视频播放器不能播放视频文件。

所以，解决方案是什么？安装所需的解码器。怎么做呢？

我将讨论解决这个问题的三种方法：

  1. 只安装所需的解码器：它可能会让所需的文件播放但是一些其它格式的文件仍然会处在失去解码器的状态。
  2. 一次安装多种多媒体解码器：它会安装解码器之外，还会安装其它你不需要的软件包，类似微软的字体库一样。
  3. 安装一个不同的视频播放器：像 VLC 和 MPV 视频播放器默认状态下对解码器有更好的支持。对大多数常规视频文件来说，你不必分别安装它们。

如果你遵从我的建议，我建议你采用第二种和第三种方法。为什么？一会你就知道了。

### 在 Ubuntu Linux 获取 h264 解码器

这里我使用 Ubuntu Linux。第一和第三种方法应该适用于其它发行版，但是第二种方法不适用，因为所提到的包 (常常) 是 Ubuntu 所独有的。

#### 方法 1: 只安装所需的解码器 (不建议)

当你看到这个错误，它给你一个叫做 “在 Ubuntu 软件中心查找 ” 的选项。点击这个选项打开软件中心，可能显示(或不显示)一些软件包将会在你的系统上安装 h264 解码器。

![在 Ubuntu 软件中心可能提供 h264 解码器软件包][3]

软件包名可能听起来很相似但是需要带有“糟糕”设置的 GStreamer 多媒体解码器。检查软件包的描述。

或者,你可以使用这个命令在终端来安装软件包：

```

    sudo apt install gstreamer1.0-plugins-bad

```

如果你对终端不了解，请注意它将要求使用你的账户密码。**当你输入你的密码时，屏幕什么都不显示**。这是 Linux 的方式。你盲输密码然后按回车键。

一旦软件包安装完成，再次打开文件看看是否能够正常播放。

这可能对你有用，但是故事并未结束。你可能有其它格式的一些视频文件要求一些其它的 h264 解码器 或者其它解码器。

![其它的解码器播放视频你可能仍然有问题][4]

你可以像这样尝试安装更多的解码器：

```

    sudo apt install libavcodec-extra gstreamer1.0-plugins-ugly gstreamer1.0-libav

```

然而,在 Ubuntu 有一个 [ 安装多媒体解码器更加方便的方法 ][5] 并且在下一节我会展示给你。


####  方法 2: 安装所有多媒体解码器 (建议)  
  

Ubuntu 系统提供了一个名字叫做 ubuntu-restricted-extras 的原始软件包，由许多常规的音频和视频解码器以及像类似微软字体库那样无用的一些软件包组成。

安装这个软件包你将不用再担心多媒体解码器的问题了。

在 Ubuntu 打开终端并键入以下命令：

```

    sudo apt install ubuntu-restricted-extras

```

由于这个原始软件包包含类似微软字库那样用不到的一些多余的软件，你将不得不接受最终用户许可协议 (EULA) 。


![按下 tab 键 然后点击回车接受 EULA 协议][6]

下一屏可能类似以下这样。只按下 tab 键将会高亮显示选项。当正确的选项高亮显示时，按下回车键来确认你的选择。

![当高亮显示你正确的选项时，按下 tab 键，按回车键确认][7]

多媒体解码器安装完成，你应该能够播放 (大多数) 许多中媒体文件。你的音乐播放器能播放 MP3 文件，你的视频播放器能播放 MP4，MKV等等格式。

然而，这也不是故事的终点，至少对某些人来说。

为什么我要那样说？因为我已经注意到 Ubuntu 系统下的默认视频播放器，Totem，在播放某些视频格式文件时常常遇到问题。你会注意到突然你的系统主机发热，风扇狂转并且鼠标指针停止运行。

为什么？因为 Totem 播放器在视频解码方面占用了太多的处理器资源。

当你播放视频的时候你可以通过 top 命令 测试以下。查看名称为 totem 这个进程 (那是默认视频播放器的名字)。

![Ubuntu 默认的视频播放器, Totem, 可能消耗过多的必要的 CPU 资源][8]

你现在能够做什么？你的麻烦看起来永无止境，别担心。[在 Linux 上有更好的视频播放器][9] 并且它们能帮助你解决问题。

#### 方法 3: 安装一个更好的视频播放器 (建议)

在 Linux 有很多优秀的视频播放器。我发现它们好于默认的 Totem 视频播放器。

就我个人来说，那么多个我只喜欢这两个：VLC][10] 和 [MPV][11]。

VLC 是一个多功能且超级流行的额视频播放器。很可能你已经使用过 VLC 。

MPV 媒体播放器不是那么流行但是这个轻量级的程序播放视频文件是再合适不过了。

VLC 和 MPV 播放器都擅长处理多媒体解码器。你甚至不必分开来安装多媒体解码器。只需要 [安装 VLC][12] 或者 MPV ，你就能够播放各种格式的视频文件。

在软件中心也可以找到它：

![在 Ubuntu 软件中心 MPV 可用][13]

或者 使用命令行 [在 Ubuntu 安装 MPV][14]：

```

    sudo apt install mpv

```

现在你已经有了另一个视频播放器，你应该右键点击视频文件，选择新的视频播放器来打开。

或者，你可以[使其作为默认程序][15] 双击来播放视频文件。

### 对你有用吗?

我在这里没有说太多细节。我想阐述各种方法和它们每个的利弊。

你在 Ubuntu 处理好 h264 解码器的问题了吗？那种方法对你有用？

--------------------------------------------------------------------------------

via: https://itsfoss.com/install-h-264-decoder-ubuntu/

作者：[Abhishek Prakash][a]
选题：[lujun9972][b]
译者：[hwlife](https://github.com/hwlife)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/abhishek/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/install-ubuntu/
[2]: https://itsfoss.com/wp-content/uploads/2022/04/h264-decoder-error-ubuntu-800x241.png
[3]: https://itsfoss.com/wp-content/uploads/2022/04/h264-decoder-ubuntu-software-center-800x532.png
[4]: https://itsfoss.com/wp-content/uploads/2022/04/ac3-decoder-missing-ubuntu-800x251.png
[5]: https://itsfoss.com/install-media-codecs-ubuntu/
[6]: https://itsfoss.com/wp-content/uploads/2020/02/installing_ubuntu_restricted_extras.jpg
[7]: https://itsfoss.com/wp-content/uploads/2020/02/installing_ubuntu_restricted_extras_1.jpg
[8]: https://itsfoss.com/wp-content/uploads/2022/04/totem-consuming-more-cpu-ubuntu-800x454.webp
[9]: https://itsfoss.com/video-players-linux/
[10]: https://www.videolan.org/vlc/
[11]: https://mpv.io/
[12]: https://itsfoss.com/install-latest-vlc/
[13]: https://itsfoss.com/wp-content/uploads/2022/04/mpv-player-ubuntu-software-center-800x346.png
[14]: https://itsfoss.com/mpv-video-player/
[15]: https://itsfoss.com/change-default-applications-ubuntu/

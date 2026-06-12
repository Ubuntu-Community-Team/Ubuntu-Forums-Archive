---
title: "problem playing mp4 files"
date: 2022-09-27
forum: Ubuntu Development Version
---

### Post by Claus7 on 2022-09-27
Hello,

I do not know if you have noticed that mp4 files cannot be played properly. 

I tried using totem and the window opens momentarily and then it crushes, producing a bug which was filled using launchpad.
Using vlc, sound works ok, yet the screen is black. I installed also x264 package for vlc to no avail.
Ubuntu-restricted-extras package is installed in all these trials.
Installing mplayer it works only when invoked using terminal. The gui mplayer doesn't work.

Regards!

---

### Post by #&amp;thj^% on 2022-09-27
possibly this>>>:
```
sudo apt install gstreamer1.0-libav
```

---

### Post by Claus7 on 2022-09-27
Hello,

> **1fallen said:**
> possibly this>>>:
```
sudo apt install gstreamer1.0-libav
```

thank you for your response *1fallen*. This package is already installed in my system. The source package reported for that bug was: libgstreamer1.0-0 1.20.3-1. I think that those two are related.

Regards!

---

### Post by #&amp;thj^% on 2022-09-27
Did you report it then?
I'm sure jbicha would be interested.

---

### Post by mIk3_08 on 2022-09-28
> **Claus7 said:**
> Hello,

I do not know if you have noticed that mp4 files cannot be played properly. 

I tried using totem and the window opens momentarily and then it crushes, producing a bug which was filled using launchpad.
Using vlc, sound works ok, yet the screen is black. I installed also x264 package for vlc to no avail.
Ubuntu-restricted-extras package is installed in all these trials.
Installing mplayer it works only when invoked using terminal. The gui mplayer doesn't work.

Regards!
Please run the command below and paste the result here in thread wrap with code. Regards and cheers.
```
hostnamectl
```

---

### Post by SeijiSensei on 2022-09-28
> **Claus7 said:**
> I do not know if you have noticed that mp4 files cannot be played properly.

This, as a general statement, is simply not true. I've played many mp4 files on Ubuntu machines over the years. Are you saying this is a problem with 22.10?

mp4 is a "container," not a "codec." It's likely the stream you're trying to play employs an unusual video codec.

Since you said you had mplayer installed, please run

```
mplayer -identify /path/to/your/file.mp4
```

and see what gets reported for ID_VIDEO_CODEC and ID_AUDIO_CODEC.

Also, you should give mpv a try. It's a branch of the mplayer code. I haven't found anything it can't play.

---

### Post by Claus7 on 2022-09-28
Hello,

> **1fallen said:**
> Did you report it then?
I'm sure jbicha would be interested.

affirmative, it was reported the moment I faced it. Lately, reporting problems is working fine, and a bug is reported almost right away when one appears.

> **mIk3_08 said:**
> Please run the command below and paste the result here in thread wrap with code. Regards and cheers.
```
hostnamectl
```

Part of the output is just below. I'm not so sure how this might help, yet I have to admit that I wasn't aware of that command. I suppose that you wanted this info for the OS.
```
Icon name: computer
Operating System: Ubuntu Kinetic Kudu (development branch)
Kernel: Linux 5.19.0-15-generic
Architecture: x86-64
```

> **SeijiSensei said:**
> This, as a general statement, is simply not true. I've played many mp4 files on Ubuntu machines over the years. Are you saying this is a problem with 22.10?
Affirmative, I had to mention that this was about 22.10 development version in the first place.

> **SeijiSensei said:**
> mp4 is a "container," not a "codec." It's likely the stream you're trying to play employs an unusual video codec.

Since you said you had mplayer installed, please run

```
mplayer -identify /path/to/your/file.mp4
```

and see what gets reported for ID_VIDEO_CODEC and ID_AUDIO_CODEC.

Also, you should give mpv a try. It's a branch of the mplayer code. I haven't found anything it can't play.

mplayer plays the file just fine. I thought that vlc falls in that category as well: a player that plays almost everything. The result requested is the following:
ID_VIDEO_CODEC=ffh264
ID_AUDIO_CODEC=ffaac

Regards!

---

### Post by ipv2 on 2022-09-28
> **Claus7 said:**
> I thought that vlc falls in that category as well: a player that plays almost everything.

so did i but have replaced vlc with mpv today.

> **SeijiSensei said:**
> you should give mpv a try. I haven't found anything it can't play.

ever since 22.04 i started using the vlc snap but vlc gave me subtitle error on many files while mpv had no problem handling all those files & no subtitle errors.

---

### Post by mIk3_08 on 2022-09-29
> **Claus7 said:**
> 
Using vlc, sound works ok, yet the screen is black. I installed also x264 package for vlc to no avail.

In vlc, I also have experience this one. Have you seen any .vlc folder in your home directory? This is usually hide by default but you can view it by setting up your Nautilus/Files to show your hidden files. What I did is just I deleted the .vlc folder in my home directory/ .cache then setting up the vlc video output preferences.
preferences -> Videos -> output to OpenGL video output then
preferences -> Input/Codecs -> Hardware-accelerated decoding to Disable. 
From this. my vlc starts to play video as normal. Others also installed ubuntu-restricted-extras package. Regards and cheers

---

### Post by Claus7 on 2022-09-29
Hello,

> **ipv2 said:**
> so did i but have replaced vlc with mpv today.
ever since 22.04 i started using the vlc snap but vlc gave me subtitle error on many files while mpv had no problem handling all those files & no subtitle errors.

thank you, it worked really nice as mentioned.

> **mIk3_08 said:**
> In vlc, I also have experience this one. Have you seen any .vlc folder in your home directory? This is usually hide by default but you can view it by setting up your Nautilus/Files to show your hidden files. What I did is just I deleted the .vlc folder in my home directory/ .cache then setting up the vlc video output preferences.
preferences -> Videos -> output to OpenGL video output then
preferences -> Input/Codecs -> Hardware-accelerated decoding to Disable. 
From this. my vlc starts to play video as normal. Others also installed ubuntu-restricted-extras package. Regards and cheers

I searched about it and I do not have such a folder: .vlc. I searched a little bit more and I fould .local/share/vlc where I found the file ml.xspf.
I backed up this file, opened vlc, went to tools->preferences->video->output and changed it from automatic to OpenGL video output and changed also the Input/Codecs from automatic to disabled. I closed vlc, saw that a new ml.xspf file was created and tried to open this mp4 file without avail.

I will mark this thread as solved.
Regards!

---

### Post by iamjiwjr on 2022-09-30
gstreamer bad plugins

---

### Post by Claus7 on 2022-09-30
Hello,

> **iamjiwjr said:**
> gstreamer bad plugins
the ones that are installed in my system are:
gstreamer1.0-plugins-bad
libgstreamer1.0-plugins-bad1.0.-0 (just plain not the dev package though)

Regards!

---

### Post by bert.ram.aerts on 2022-10-03
See my VLC issue in [https://ubuntuforums.org/showthread.php?t=2479684](https://ubuntuforums.org/showthread.php?t=2479684)
The solution provided in this thread to put in VLC preferences video output to OpenGL and hardware acceleration to disable, does not work for me.
Do you have an nVIDIA graphics card and proprietary driver installed?

---

### Post by Claus7 on 2022-10-03
Hello,

> **bert.ram.aerts said:**
> See my VLC issue in [https://ubuntuforums.org/showthread.php?t=2479684](https://ubuntuforums.org/showthread.php?t=2479684)
The solution provided in this thread to put in VLC preferences video output to OpenGL and hardware acceleration to disable, does not work for me.
Do you have an nVIDIA graphics card and proprietary driver installed?

no, I'm using an intel graphics card. Thank you for your link to your thread: from there I found out that the problem I'm facing is indeed a bug and not my system related. As you have seen in this thread it is not only affecting vlc and the "solution" was to switch (at least for the time being) to mpv, which is working fine. 

Regards!

---


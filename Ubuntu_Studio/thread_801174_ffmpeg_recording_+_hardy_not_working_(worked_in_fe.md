---
title: "ffmpeg recording + hardy not working (worked in feisty)"
date: 2008-05-20
forum: Ubuntu Studio
---

### Post by jshayden on 2008-05-20
I frequently used the following in Feisty to record my screen and record from my webcam:

```
ffmpeg -f oss -i /dev/audio1 -f x11grab -s <width>x<height> -r 15 -i :0.0 blah.mpg

ffmpeg -f oss -i /dev/audio1 -f video4linux2 -s <width>x<height> -r 25 -sameq -i /dev/video0 blah.mpg
```

I get the following after installing Hardy:
```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
Unknown input or output format: oss
```

I believe that in Feisty I was simply using the ffmpeg version from the repositories.

Any ideas?

Thanks,
Josh

---

### Post by FakeOutdoorsman on 2008-05-20
The options names for ffmpeg change often.  It can be frustrating to keep up with them.
```
[frink@hedron]$ ffmpeg -formats | grep "audio grab"
DE audio_decive             audio grab and output
```
Seems "oss" is named "audio_device" in the Ubuntu repo version of ffmpeg.

---

### Post by jshayden on 2008-05-20
Ah, I see.  That is annoying.

That is working fine now:
```
Input #0, audio_device, from '/dev/audio':
  Duration: N/A, bitrate: N/A
  Stream #0.0: Audio: pcm_s16le, 44100 Hz, mono, 705 kb/s
```

It seems there is another, similar problem:
```
Unknown input or output format: x11grab
```

Thanks for the help...
Josh

---

### Post by FakeOutdoorsman on 2008-05-20
Looks like ffmpeg in the Ubuntu repos has been compiled without "--enable-x11grab        ".  You can try removing ffmpeg and installing ffmpeg from the [Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu") and look to see if ffmpeg is compiled with x11grab.  It will be listed with: configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab, etc. like in your example above.

If that doesn't work, refer to my tutorial on compiling ffmpeg on your own: [HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095").

---

### Post by jshayden on 2008-05-20
Hmm... I compiled from source, as suggested, adding some configuration options:

```
configuration: --enable-gpl --enable-postproc --enable-swscale --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libgsm --enable-libdc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-libx264 --enable-liba52 --enable-libamr-nb --enable-libamr-wb --enable-shared --enable-x11grab --enable-nonfree --prefix=/usr
```

However...
```
Input #0, oss, from '/dev/audio':
  Duration: N/A, start: 1211318230.660765, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, mono, 705 kb/s
Unknown input or output format: x11grab
```

Thanks again...
Josh

---

### Post by FakeOutdoorsman on 2008-05-20
I just recompiled ffmpeg from svn and it worked for me:
```
[frink@hedron ~]$ ffmpeg -f oss -i /dev/audio -f x11grab -s 320x240 -r ntsc -i :0.0 blah2.mpg
FFmpeg version SVN-r13202, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-libvorbis --enable-libtheora --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-pthreads --enable-libx264 --disable-ffserver --disable-ffplay --disable-ipv6 --disable-vhook --enable-x11grab
  libavutil version: 49.6.0
  libavcodec version: 51.57.0
  libavformat version: 52.13.0
  libavdevice version: 52.0.0
  built on May 20 2008 14:26:54, gcc: 4.3.0
Input #0, oss, from '/dev/audio':
  Duration: N/A, start: 1211323108.044455, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, mono, 705 kb/s
[x11grab @ 0x8458328]device: :0.0 -> display: :0.0 x: 0 y: 0 width: 320 height: 240
[x11grab @ 0x8458328]shared memory extension  found
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1211323108.499766, bitrate: 73654 kb/s
    Stream #1.0: Video: rawvideo, rgb32, 320x240, 73654 kb/s, 29.97 tb(r)
Output #0, mpeg, to 'blah2.mpg':
    Stream #0.0: Video: mpeg1video, yuv420p, 320x240, q=2-31, 200 kb/s, 29.97 tb(c)
    Stream #0.1: Audio: mp2, 44100 Hz, mono, 64 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
frame=  170 fps= 30 q=2.0 Lsize=     428kB time=5.6 bitrate= 621.8kbits/s    
video:380kB audio:44kB global headers:0kB muxing overhead 1.022972%
Received signal 2: terminating.
```

I'm not sure why it wouldn't be working for you.  What is the exact command you used?

---

### Post by jshayden on 2008-05-20
The command I'm using is the one from the original post.  I even tried yours; same result.  I'm recompiling with your exact configuration, just for the heck of it.  I'll post the results shortly.

Thanks,
Josh

---

### Post by jshayden on 2008-05-20
Same output with your configuration.  Very strange...


```
$ ffmpeg -f oss -i /dev/audio -f x11grab -s 320x240 -r ntsc -i :0.0 blah2.mpg
FFmpeg version SVN-r13202, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-libvorbis --enable-libtheora --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-pthreads --enable-libx264 --disable-ffserver --disable-ffplay --disable-ipv6 --disable-vhook --enable-x11grab
  libavutil version: 49.6.0
  libavcodec version: 51.57.0
  libavformat version: 52.13.0
  libavdevice version: 52.0.0
  built on May 20 2008 18:13:34, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, oss, from '/dev/audio':
  Duration: N/A, start: 1211325377.326888, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, mono, 705 kb/s
Unknown input or output format: x11grab
```

Josh

---

### Post by FakeOutdoorsman on 2008-05-20
This shouldn't be this hard, but ffmpeg can be confusing.  My Ubuntu has been so customized and beat up with multiple ffmpeg installs that it may not be the best system to test ffmpeg with.  I'm not sure what else to recommend except these:

[[Ffmpeg-user] Grabbing the X11 display]("http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2007-January/006542.html")
[[Ffmpeg-user] X11grab - how to enable ?]("http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2007-March/007266.html")
[How to Create a Screencast in Ubuntu]("http://ubuntu.wordpress.com/2006/06/08/how-to-create-a-screencast-in-ubuntu/") (old, but may be useful)

This first link mentions xlibs-dev, but I believe in Ubuntu that would be libx11-dev.  Make sure to "make distclean" in your ffmpeg folder before re-configuring/re-making your ffmpeg installation.  You can also try #ffmpeg irc channel, but they never seem to answer any questions.

Tomorrow or later tonight I'll try this in a stock Ubuntu installation in VirtualBox but I'm not sure if it will work in a virtual environment.

---

### Post by FakeOutdoorsman on 2008-05-21
I think I got this figured out.  ffmpeg will silently fail to incorproate x11grab when certain dev files are not installed.  I did the shotgun approach and installed a large number of packages.

I'm not sure which package made x11_grab_device show up, but I used the old package names from feisty that made up the defunct xlibs-dev.  If I were to guess first try installing these:
```
sudo aptitude install libx11-dev xlibs-static-dev x11proto-input-dev
```
  After "./configure --enable-gpl --enable-x11grab" ffmpeg should show:
```
Enabled indevs:
dv1394			v4l			x11_grab_device
oss			v4l2
```
If x11_grab_device doesn't show up still try carpet bombing it with then reconfigure ffmpeg:
```
sudo aptitude install libice-dev libsm-dev libx11-dev libxext-dev libxi-dev libxmu-dev libxmuu-dev libxpm-dev libxrandr-dev libxt-dev libxtrap-dev libxtst-dev libxv-dev x-dev zlib1g-dev
```
The command I used was:
```
ffmpeg -f x11grab -s 320x240 -r ntsc -i :0.0 testymctesterson.mpg
```
I would have preferred to been able to refine this apprach and figure out which packages are essential instead of this blunt force style.

---

### Post by jshayden on 2008-05-21
I was afraid that this approach would be the only way...
It worked wonderfully!

Thanks so much for all of the help!  I really appreciate it.

Josh

---

### Post by FakeOutdoorsman on 2008-05-21
No problem.  I've always wanted to figure out x11 grabbing with ffmpeg anyway.  I may use this thread as a reference for an Ubuntu howto on doing this once I figure out the correct packages.

---


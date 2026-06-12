---
title: "Winff Error"
date: 2008-12-31
forum: Ubuntu Studio
---

### Post by kevin11951 on 2008-12-31
the picture says it all:

---

### Post by kevin11951 on 2009-01-01
um... help?

---

### Post by FakeOutdoorsman on 2009-01-02
Give the output of:
```
ffmpeg -version
```
Also, what WinFF preset are you using?

---

### Post by kevin11951 on 2009-01-02
> **FakeOutdoorsman said:**
> Give the output of:
```
ffmpeg -version
```
Also, what WinFF preset are you using?

> ksoviero@ubuntu-studio:~$ ffmpeg -version
FFmpeg version UNKNOWN-svn15824+3:0.svn20081115-1ubuntu1+unstripped1~ppa1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn15824+3:0.svn20081115-1ubuntu1+unstripped1~ppa1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-libmp3lame --enable-libfaac --enable-libfaad --enable-libdirac --disable-encoder=libschroedinger --disable-decoder=libdirac --enable-gpl --enable-libxvid --enable-gpl --enable-libx264 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 3. 0 / 52. 3. 0
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 1. 0 /  0. 1. 0
  libswscale     0. 6. 1 /  0. 6. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec 30 2008 05:50:58, gcc: 4.3.2
FFmpeg UNKNOWN-svn15824+3:0.svn20081115-1ubuntu1+unstripped1~ppa1
libavutil     49.12. 0 / 49.12. 0
libavcodec    52. 3. 0 / 52. 3. 0
libavformat   52.23. 1 / 52.23. 1
libavdevice   52. 1. 0 / 52. 1. 0
libavfilter    0. 1. 0 /  0. 1. 0
libswscale     0. 6. 1 /  0. 6. 1
libpostproc   51. 2. 0 / 51. 2. 0


Trying to convert to AVI (16:9)

---

### Post by FakeOutdoorsman on 2009-01-02
The preset has an error.  It looks like you're using Jaunty and I'm not so I can't test this.  Open WinFF -> Edit -> Presets.  Find the XviD in AVI (16:9) preset and replace the preset command line with (don't forget to click "Save"):
```
-vcodec libxvid -vtag XVID -s 704x384 -aspect 16:9 -maxrate 1800k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +mv4+aic -trellis 1 -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -ab 128k -ac 2
```

---


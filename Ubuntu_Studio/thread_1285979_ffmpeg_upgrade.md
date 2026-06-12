---
title: "ffmpeg upgrade"
date: 2009-10-08
forum: Ubuntu Studio
---

### Post by hyperion1 on 2009-10-08
hi, 
I am trying to upgrade ffmpeg to the latest version 2009
I checked out the code from ffmpeg trunk. 
did 
./configure
./make
./make install 

but still ffmpeg -version says 
```

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 15:36:03, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
ffmpeg      SVN-rUNKNOWN
libavutil   3212032
libavcodec  3352064
libavformat 3344896


```
where as it should say,

```

ffmpeg -v
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.

```

any pointers please 
thanks, 
DJP

---

### Post by FakeOutdoorsman on 2009-10-08
This will get you on the right track:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]

---


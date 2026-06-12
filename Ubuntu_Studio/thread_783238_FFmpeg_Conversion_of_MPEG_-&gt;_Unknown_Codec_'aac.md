---
title: "FFmpeg Conversion of MPEG -&gt; Unknown Codec 'aac'"
date: 2008-05-05
forum: Ubuntu Studio
---

### Post by hansoffate on 2008-05-05
I am trying to convert an MPEG to MP4.  When I run FFMPEG this is what my output is

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
Input #0, mpeg, from '1003_20080117203000.mpg':
  Duration: 00:29:57.2, start: 0.289378, bitrate: 5191 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480, 6000 kb/s, 29.97 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
Unknown codec 'aac'
```

I searched the forum, and my problem seemed similar to this post [http://ubuntuforums.org/showthread.php?t=485200](http://ubuntuforums.org/showthread.php?t=485200)  
I tried apt-get install libavcodec0d but there is no package by that name.  However, I do have libavcodec1d already installed from the medibuntu repositories.

Any ideas?

Thanks,
Hans

:EDIT:  I double checked the repositories, and for some reason I had a gutsy repository in there.  I disabled it and reloaded synaptic.  I installed libavcodec-dev which seemed to fix the problem.

---


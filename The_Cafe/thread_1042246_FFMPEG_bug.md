---
title: "FFMPEG bug?"
date: 2009-01-17
forum: The Cafe
---

### Post by kevin11951 on 2009-01-17
When ever i try to use ffmpeg to convert anything i get this:

> ksoviero@ksoviero-laptop:~$ ffmpeg -aspect 16:9 -i '/home/ksoviero/Desktop/test.ogg' ~/Desktop/out.avi
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
[theora @ 0xb7d902f0]Theora bitstream version 30201
[theora @ 0xb7d902f0]344 bits left in packet 81
[theora @ 0xb7d902f0]7 bits left in packet 82
Input #0, ogg, from '/home/ksoviero/Desktop/test.ogg':
  Duration: 00:01:29.3, start: 0.057333, bitrate: 12502 kb/s
    Stream #0.0: Video: theora, yuv420p, 720x480 [PAR 40:33 DAR 20:11], 29.97 tb(r)
    Stream #0.1: Audio: vorbis, 48000 Hz, stereo, 499 kb/s
Output #0, avi, to '/home/ksoviero/Desktop/out.avi':
    Stream #0.0: Video: mpeg4, yuv420p, 720x480 [PAR 40:33 DAR 20:11], q=2-31, 200 kb/s, 29.97 tb(c)
    Stream #0.1: Audio: mp2, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[theora @ 0xb7d902f0]Theora bitstream version 30201
[theora @ 0xb7d902f0]344 bits left in packet 81
[theora @ 0xb7d902f0]7 bits left in packet 82
Press [q] to stop encoding



And it just sits like that endlessly, any fix for this besides re-installation of ubuntu?

INFO:
Im using ubuntu intrepid
32bit
standard ubuntu ffmpeg

---

### Post by saulgoode on 2009-01-17
Perhaps try the solutions proposed in [this bug report]("https://bugs.launchpad.net/medibuntu/+bug/269997")?

---

### Post by kevin11951 on 2009-01-17
running: 
```
sudo apt-get install libavcodec-unstripped-51 libavdevice-unstripped-52 libavutil-unstripped-49 libpostproc-unstripped-51 libswscale-unstripped-0
```

fixed it!

---


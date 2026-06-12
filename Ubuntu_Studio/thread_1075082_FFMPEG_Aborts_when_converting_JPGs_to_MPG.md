---
title: "FFMPEG Aborts when converting JPGs to MPG"
date: 2009-02-19
forum: Ubuntu Studio
---

### Post by mjbauer95 on 2009-02-19
Every time I run:```
ffmpeg -f image2 -i frames/IMG_01%02d.JPG -r 50 videos/video-4.mpg
```
to make a stop-motion FFMPEG errors with:

```
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, image2, from 'frames/IMG_01%02d.JPG':
  Duration: 00:00:03.9, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj422p, 2048x1536 [PAR 0:1 DAR 0:1], 25.00 tb(r)
Output #0, mpeg, to 'videos/video-4.mpg':
    Stream #0.0: Video: mpeg1video, yuv420p, 2048x1536 [PAR 0:1 DAR 0:1], q=2-31, 200 kb/s, 50.00 tb(c)
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=  196 fps=  8 q=31.0 Lsize=    4626kB time=3.9 bitrate=9717.0kbits/s    
video:443kB audio:0kB global headers:0kB muxing overhead 943.183665%
*** glibc detected *** ffmpeg: corrupted double-linked list: 0x099b47a0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7908454]
/lib/tls/i686/cmov/libc.so.6[0xb790a283]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb790a4b6]
/usr/lib/i686/cmov/libavutil.so.49(av_freep+0x16)[0xb7a69e36]
======= Memory map: ========
08048000-0805a000 r-xp 00000000 08:01 2877674    /usr/bin/ffmpeg
0805a000-0805b000 r--p 00011000 08:01 2877674    /usr/bin/ffmpeg
0805b000-0805c000 rw-p 00012000 08:01 2877674    /usr/bin/ffmpeg
0991d000-09b76000 rw-p 0991d000 00:00 0          [heap]
b4500000-b4521000 rw-p b4500000 00:00 0 
b4521000-b4600000 ---p b4521000 00:00 0 
b46d0000-b4ab5000 rw-p b46d0000 00:00 0 
b4b21000-b4f68000 rw-p b4b21000 00:00 0 
b4fae000-b66f9000 rw-p b4fae000 00:00 0 
b68f3000-b69c6000 rw-p b68f3000 00:00 0 
b6b67000-b6cf7000 rw-p b6b67000 00:00 0 
b6deb000-b726c000 rw-p b6deb000 00:00 0 
b72e2000-b72ef000 r-xp 00000000 08:01 3141478    /lib/libgcc_s.so.1
b72ef000-b72f0000 r--p 0000c000 08:01 3141478    /lib/libgcc_s.so.1
b72f0000-b72f1000 rw-p 0000d000 08:01 3141478    /lib/libgcc_s.so.1
b72f1000-b72f3000 rw-p b72f1000 00:00 0 
b72f3000-b72f7000 r-xp 00000000 08:01 2878009    /usr/lib/libXdmcp.so.6.0.0
b72f7000-b72f8000 rw-p 00003000 08:01 2878009    /usr/lib/libXdmcp.so.6.0.0
b72f8000-b72f9000 rw-p b72f8000 00:00 0 
b72f9000-b72fd000 r-xp 00000000 08:01 2878689    /usr/lib/libogg.so.0.5.3
b72fd000-b72fe000 r--p 00003000 08:01 2878689    /usr/lib/libogg.so.0.5.3
b72fe000-b72ff000 rw-p 00004000 08:01 2878689    /usr/lib/libogg.so.0.5.3
b72ff000-b7301000 r-xp 00000000 08:01 2877998    /usr/lib/libXau.so.6.0.0
b7301000-b7302000 rw-p 00001000 08:01 2877998    /usr/lib/libXau.so.6.0.0
b7302000-b7319000 r-xp 00000000 08:01 2878944    /usr/lib/libxcb.so.1.0.0
b7319000-b731a000 r--p 00016000 08:01 2878944    /usr/lib/libxcb.so.1.0.0
b731a000-b731b000 rw-p 00017000 08:01 2878944    /usr/lib/libxcb.so.1.0.0
b731b000-b731c000 r-xp 00000000 08:01 2878942    /usr/lib/libxcb-xlib.so.0.0.0
b731c000-b731d000 r--p 00000000 08:01 2878942    /usr/lib/libxcb-xlib.so.0.0.0
b731d000-b731e000 rw-p 00001000 08:01 2878942    /usr/lib/libxcb-xlib.so.0.0.0
b731e000-b7323000 r-xp 00000000 08:01 2878790    /usr/lib/libraw1394.so.8.2.0
b7323000-b7324000 r--p 00004000 08:01 2878790    /usr/lib/libraw1394.so.8.2.0
b7324000-b7325000 rw-p 00005000 08:01 2878790    /usr/lib/libraw1394.so.8.2.0
b7325000-b7326000 rw-p b7325000 00:00 0 
b7326000-b73ca000 r-xp 00000000 08:01 2877660    /usr/lib/libxvidcore.so.4.1
b73ca000-b73cb000 rw-p 000a3000 08:01 2877660    /usr/lib/libxvidcore.so.4.1
b73cb000-b743e000 rw-p b73cb000 00:00 0 
b743e000-b74c1000 r-xp 00000000 08:01 2877659    /usr/lib/libx264.so.59
b74c1000-b74c2000 rw-p 00082000 08:01 2877659    /usr/lib/libx264.so.59
b74c2000-b74c4000 rw-p b74c2000 00:00 0 
b74c4000-b74df000 r-xp 00000000 08:01 2878904    /usr/lib/libvorbis.so.0.4.0
b74df000-b74e0000 r--p 0001a000 08:01 2878904    /usr/lib/libvorbis.so.0.4.0
b74e0000-b74ee000 rw-p 0001b000 08:01 2878904    /usr/lib/libvorbis.so.0.4.0
b74ee000-b74f9000 r-xp 00000000 08:01 2878906    /usr/lib/libvorbisenc.so.2.0.3
b74f9000-b74fa000 r--p 0000a000 08:01 2878906    /usr/lib/libvorbisenc.so.2.0.3
b74fa000-b75e8000 rw-p 0000b000 08:01 2878906    /usr/lib/libvorbisenc.so.2.0.3
b75e8000-b7631000 r-xp 00000000 08:01 2878875    /usr/lib/libtheora.so.0.3.3
b7631000-b7633000 rw-p 00049000 08:01 2878875    /usr/lib/libtheora.so.0.3.3
b7633000-b7634000 rw-p b7633000 00:00 0 
b7634000-b7676000 r-xp 00000000 08:01 2877657    /usr/lib/libmp3lame.so.0.0.0
b7676000-b7677000 r--p 00042000 08:01 2877657    /usr/lib/libmp3lame.so.0.0.0
b7677000-b7679000 rw-p 00043000 08:01 2877657    /usr/lib/libmp3lame.so.0.0.0
b7679000-b76a9000 rw-p b7679000 00:00 0 
b76a9000-b76b5000 r-xp 00000000 08:01 2877193    /usr/lib/libgsm.so.1.0.12
b76b5000-b76b6000 rw-p 0000b000 08:01 2877193    /usr/lib/libgsm.so.1.0.12
b76b6000-b76f1000 r-xp 00000000 08:01 2877617    /usr/lib/libfaad.so.0.0.0
b76f1000-b76f2000 ---p 0003b000 08:01 2877617    /usr/lib/libfaad.so.0.0.0
b76f2000-b76f3000 r--p 0003b000 08:01 2877617    /usr/lib/libfaad.so.0.0.0
b76f3000-b76f6000 rw-p 0003c000 08:01 2877617    /usr/lib/libfaad.so.0.0.0
b76f6000-b7704000 r-xp 00000000 08:01 2875818    /usr/lib/libfaac.so.0.0.0
b7704000-b7705000 r--p 0000d000 08:01 2875818    /usr/lib/libfaac.so.0.0.0
b7705000-b7708000 rw-p 0000e000 08:01 2875818    /usr/lib/libfaac.so.0.0.0
b7708000-b7711000 r-xp 00000000 08:01 2877201    /usr/lib/liba52-0.7.4.so
b7711000-b7712000 rw-p 00008000 08:01 2877201    /usr/lib/liba52-0.7.4.so
b7712000-b7714000 rw-p b7712000 00:00 0 
b7714000-b7716000 r-xp 00000000 08:01 853359     /lib/tls/i686/cmov/libdl-2.8.90.so
b7716000-b7717000 r--p 00001000 08:01 853359     /lib/tls/i686/cmov/libdl-2.8.90.so
b7717000-b7718000 rw-p 00002000 08:01 853359     /lib/tls/i686/cmov/libdl-2.8.90.so
b7718000-b772c000 r-xp 00000000 08:01 2878956    /usr/lib/libz.so.1.2.3.3
b772c000-b772e000 rw-p 00013000 08:01 2878956    /usr/lib/libz.so.1.2.3.3
b772e000-b773b000 r-xp 00000000 08:01 2878013    /usr/lib/libXext.so.6.4.0
b773b000-b773d000 rw-p 0000c000 08:01 2878013    /usr/lib/libXext.so.6.4.0
b773d000-b7828000 r-xp 00000000 08:01 2879262    /usr/lib/libX11.so.6.2.0
b7828000-b7829000 r--p 000ea000 08:01 2879262    /usr/lib/libX11.so.6.2.0
b7829000-b782b000 rw-p 000eb000 08:01 2879262    /usr/lib/libX11.so.6.2.0
b782b000-b782c000 rw-p b782b000 00:00 0 
b782c000-b7858000 r-xp 00000000 08:01 2877220    /usr/lib/libdc1394.so.22.1.0
b7858000-b7859000 rw-p 0002b000 08:01 2877220    /usr/lib/libdc1394.so.22.1.0
b7859000-b7899000 rw-p b7859000 00:00 0 
b7899000-b79f1000 r-xp 00000000 08:01 853356     /lib/tls/i686/cmov/libc-2.8.90.so
b79f1000-b79f3000 r--p 00158000 08:01 853356     /lib/tls/i686/cmov/libc-2.8.90.so
b79f3000-b79f4000 rw-p 0015a000 08:01 853356     /lib/tls/i686/cmov/libc-2.8.90.so
b79f4000-b79f8000 rw-p b79f4000 00:00 0 
b79f8000-b7a0d000 r-xp 00000000 08:01 853370     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7a0d000-b7a0e000 r--p 00014000 08:01 853370     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7a0e000-b7a0f000 rw-p 00015000 08:01 853370     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7a0f000-b7a11000 rw-p b7a0f000 00:00 0 
b7a11000-b7a3c000 r-xp 00000000 08:01 2900974    /usr/lib/i686/cmov/libswscale.so.0.5.0
b7a3c000-b7a3d000 r--p 0002a000 08:01 2900974    /usr/lib/i686/cmov/libswscale.so.0.5.0
b7a3d000-b7a3e000 rw-p 0002b000 08:01 2900974    /usr/lib/i686/cmov/libswscale.so.0.5.0
b7a3e000-b7a62000 r-xp 00000000 08:01 853360     /lib/tls/i686/cmov/libm-2.8.90.so
b7a62000-b7a63000 r--p 00023000 08:01 853360     /lib/tls/i686/cmov/libm-2.8.90.so
b7a63000-b7a64000 rw-p 00024000 08:01 853360     /lib/tls/i686/cmov/libm-2.8.90.so
b7a64000-b7a6f000 r-xp 00000000 08:01 2900370    /usr/lib/i686/cmov/libavutil.so.49.6.0
b7a6f000-b7a70000 r--p 0000a000 08:01 2900370    /usr/lib/i686/cmov/libavutil.so.49.6.0
b7a70000-b7a71000 rw-p 0000b000 08:01 2900370    /usr/lib/i686/cmov/libavutil.so.49.6.0
b7a71000-b7a74000 rw-p b7a71000 00:00 0 
b7a74000-b7eca000 r-xp 00000000 08:01 2900391    /usr/lib/i686/cmov/libavcodec.so.51.50.0
b7eca000-b7ecb000 r--p 00455000 08:01 2900391    /usr/lib/i686/cmov/libavcodec.so.51.50.0
b7ecb000-b7ed1000 rw-p 00456000 08:01 2900391    /usr/lib/i686/cmov/libavcodec.so.51.50.0
b7ed1000-b7fc9000 rw-p b7ed1000 00:00 0 
b7fc9000-b8066000 r-xp 00000000 08:01 2900692    /usr/lib/i686/cmov/libavformat.so.52.7.0
b8066000-b8067000 r--p 0009c000 08:01 2900692    /usr/lib/i686/cmov/libavformat.so.52.7.0
b8067000-b806a000 rw-p 0009d000 08:01 2900692    /usr/lib/i686/cmov/libavformat.so.52.7.0
b806a000-b8072000 r-xp 00000000 08:01 2900969    /usr/lib/i686/cmov/libavdevice.so.52.0.0
b8072000-b8073000 r--p 00007000 08:01 2900969    /usr/lib/i686/cmov/libavdevice.so.52.0.0
b8073000-b8074000 rw-p 00008000 08:01 2900969    /usr/lib/i686/cmov/libavdevice.so.52.0.0
b808e000-b8090000 rw-p b808e000 00:00 0 
b8090000-b80aa000 r-xp 00000000 08:01 3140777    /lib/ld-2.8.90.so
b80aa000-b80ab000 r-xp b80aa000 00:00 0          [vdso]
b80ab000-b80ac000 r--p 0001a000 08:01 3140777    /lib/ld-2.8.90.so
b80ac000-b80ad000 rw-p 0001b000 08:01 3140777    /lib/ld-2.8.90.so
bfc98000-bfcad000 rwxp bffeb000 00:00 0          [stack]
Aborted

```

Is there a non crashing version of FFMPEG?

---

### Post by FakeOutdoorsman on 2009-02-20
You're using an ancient revision of FFmpeg.  Try compiling a recent svn FFmpeg.  There have been thousands of commits and many bug fixes since the release from the repository:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by mjbauer95 on 2009-02-20
I guess that's my problem but I'm pretty sure I was just using the version from the official repo.
I'm compiling it now.

---

### Post by FakeOutdoorsman on 2009-02-20
The version from the repo is the ancient version I was referring to.

---


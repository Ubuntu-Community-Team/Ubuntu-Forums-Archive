---
title: "[SOLVED] ffmpeg broken ..."
date: 2008-08-27
forum: Ubuntu Studio
---

### Post by vikrant82 on 2008-08-27
Hi,

ffmpeg on my system(Latest intrepid) seems to be broken. I have checked out, there are no open bugs for the same.

```
kx@Kx-VMZ:~/Desktop/Latest Movies - 11/meethegimp$ ffmpeg -i meetthegimp002.mp4 -b 300k test.mp4
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Aug 25 2008 20:05:43, gcc: 4.3.1
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'meetthegimp002.mp4':
  Duration: 00:08:58.6, start: 0.000000, bitrate: 223 kb/s
    Stream #0.0(und): Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 30.00 tb(r)
    Stream #0.1(und): Audio: mp4a / 0x6134706D, 44100 Hz, stereo
Output #0, mp4, to 'test.mp4':
    Stream #0.0(und): Video: 0x0000, yuv420p, 640x480 [PAR 1:1 DAR 4:3], q=2-31, 300 kb/s, 30.00 tb(c)
    Stream #0.1(und): Audio: 0x0000, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.0
```

I have tried compiling from scratch, various SVN versions, tried installing various debs.

I get this, dreaded "Unsupported codec for output stream #0.0" for most of videos. 

Mencoder works just fine. 

I have most needed codecs installed, and have tried building ffmpeg by enabling most other codecs as well(xvid, h264 etc).

I have no ideas how to go about this one.

---

### Post by Creative2 on 2008-08-27
have u tried with medibuntu package?
i can't see aac library in your configuration...so i think is that your problem

---

### Post by vikrant82 on 2008-08-27
Yes, I have tried medibuntu package. 

I have tried compiling with parameters:

```

./configure --enable-gpl --enable-libgsm --enable-postproc --enable-swscale --enable-pthreads --enable-liba52 --enable-libfaac --enable-libfaad --enable-libgsm --enable-libmp3lame --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab --disable-ffserver --disable-ffplay --enable-shared --disable-debug
```

Most of them result in 

```
Stream #0.0(und): Video: **0x0000,** .... 
```
and then, Unsupported codec for output stream #0.0

---

### Post by Creative2 on 2008-08-27
in your ffmpeg first code 

  configuration: --enable-gpl 
--enable-pp --enable-swscaler
 --enable-x11grab --prefix=/usr 
--enable-libgsm --enable-libtheora
 --enable-libvorbis --enable-pthreads 
--disable-strip --enable-libdc1394 
--disable-armv5te --disable-armv6 
--disable-altivec --disable-vis
 --enable-shared --disable-static

i can't see libfaac

untill running , in a terminal
ffmpeg 
you can't see libfaac it will not work

---

### Post by vikrant82 on 2008-08-27
Ok!

I tried compiling myself, But seems like there was some incompatibility with ffmpeg from svn and current libavcodec in intrepid. [get some undefined symbol error]

Anyways, I installed medibuntu version, still I am stuck with, "Unsupported codec for output stream #0.0"

```
kx@Kx-VMZ:~/Desktop/Latest Movies - 11/meethegimp$ ffmpeg -i meetthegimp002.mp4 -b 300k test.mp4
FFmpeg version UNKNOWN, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libdc1394 --enable-nonfree --enable-libamr-nb --enable-nonfree --enable-libamr-wb --enable-libmp3lame --enable-libfaac --enable-gpl --enable-libxvid --enable-gpl --enable-libx264 --enable-libfaadbin --enable-libfaad --enable-liba52 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Aug 14 2008 22:27:12, gcc: 4.3.1
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'meetthegimp002.mp4':
  Duration: 00:08:58.6, start: 0.000000, bitrate: 223 kb/s
    Stream #0.0(und): Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 30.00 tb(r)
    Stream #0.1(und): Audio: mp4a / 0x6134706D, 44100 Hz, stereo
File 'test.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'test.mp4':
    Stream #0.0(und): Video: 0x0000, yuv420p, 640x480 [PAR 1:1 DAR 4:3], q=2-31, 300 kb/s, 30.00 tb(c)
    Stream #0.1(und): Audio: 0x0000, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.0 
```

Here's ffmpeg info,

```
kx@Kx-VMZ:~/Desktop$ sudo aptitude show ffmpeg
Package: ffmpeg
State: installed
Automatically installed: no
Version: 3:0.svn20080206-11ubuntu1+medibuntu2
Priority: optional
Section: non-free/graphics
Maintainer: Medibuntu Packaging Team <admin@lists.medibuntu.org>
Uncompressed Size: 782k
Depends: libavcodec51 (>= 3:0.svn20080206-8) | libavcodec-unstripped-51 (>= 3:0.svn20080206-8), libavdevice52 (>= 3:0.svn20080206-8) | libavdevice-unstripped-52 (>=
         3:0.svn20080206-8), libavformat52 (>= 3:0.svn20080206-8) | libavformat-unstripped-52 (>= 3:0.svn20080206-8), libavutil49 (>= 3:0.svn20080206-8) | libavutil-unstripped-49
         (>= 3:0.svn20080206-8), libc6 (>= 2.7), libfreetype6 (>= 2.3.5), libimlib2, libsdl1.2debian (>= 1.2.10-1), libswscale0 (>= 3:0.svn20080206-8) | libswscale-unstripped-0 (>=
         3:0.svn20080206-8)
Description: multimedia player, server and encoder - Medibuntu package
 This package contains the ffplay multimedia player, the ffserver streaming server and the ffmpeg audio and video encoder. They support most existing file formats (AVI, MPEG, OGG,
 Matroska, ASF...) and encoding formats (MPEG, DivX, MPEG4, AC3, DV...). 
 
 This package is built with the "risky" option, to enable mp3/mp4/h264/amr support. Therefore, it is in Medibuntu as it might violate patents. 
 
 This package isn't supported by Ubuntu: DON'T REPORT BUGS TO UBUNTU! 
 
 Please report any bug to our bug tracker instead: 
 https://bugs.launchpad.net/medibuntu/+bugs
Homepage: http://ffmpeg.mplayerhq.hu/
```

---

### Post by brian_p on 2008-08-27
> **vikrant82 said:**
> 

Anyways, I installed medibuntu version, still I am stuck with, "Unsupported codec for output stream #0.0"

Using the same input file as you, with the same command but an older version of ffmpeg I had no problem. Which is no comfort to you, of course!

How about:

```
ffmpeg -i meetthegimp002.mp4 -vcodec copy test.mp4
```

---

### Post by vikrant82 on 2008-08-27
Noep, Still same thing, 

```
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'meetthegimp002.mp4':
  Duration: 00:08:58.6, start: 0.000000, bitrate: 223 kb/s
    Stream #0.0(und): Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 30.00 tb(r)
    Stream #0.1(und): Audio: mp4a / 0x6134706D, 44100 Hz, stereo
File 'test.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'test.mp4':
    Stream #0.0(und): Video: 0x0000, yuv420p, 640x480 [PAR 0:1 DAR 0:1], q=2-31, 30.00 tb(c)
    Stream #0.1(und): Audio: 0x0000, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1
```

This time its for stream #0.1

Googling just leads to some ffmpeg mails where they discuss some temporary problems with their nightly builds. Nothing much there too..

---

### Post by brian_p on 2008-08-27
> **vikrant82 said:**
> 

This time its for stream #0.1

Add

```
-acodec copy
```

---

### Post by vikrant82 on 2008-08-27
Ofcourse, that was going to work .. :)

```
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'meetthegimp002.mp4':
  Duration: 00:08:58.6, start: 0.000000, bitrate: 223 kb/s
    Stream #0.0(und): Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 30.00 tb(r)
    Stream #0.1(und): Audio: mp4a / 0x6134706D, 44100 Hz, stereo
File 'test.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'test.mp4':
    Stream #0.0(und): Video: 0x0000, yuv420p, 640x480 [PAR 0:1 DAR 0:1], q=2-31, 30.00 tb(c)
    Stream #0.1(und): Audio: 0x0000, 44100 Hz, stereo
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=16159 fps=4687 q=-1.0 Lsize=   14692kB time=538.6 bitrate= 223.5kbits/s    
video:12447kB audio:1937kB global headers:0kB muxing overhead 2.146656%

```

what is this 0x0000... Never seen this.

---

### Post by brian_p on 2008-08-27
> **vikrant82 said:**
> 

what is this 0x0000... Never seen this.

I think it is ffmpeg's way of saying it is clueless about what codec to use for encoding.

mp4 is a container format which will hold a variety of different codecs. Maybe your copy of the program has to be told with -vcodec and -acodec which codecs to use.

---

### Post by wesgarner on 2008-09-15
I was having the same trouble, so I submitted a bug report on Launchpad for Medibunutu Intrepid.. In less than a few hours they fixed it, and the newer version is available on the repo..

[URL="https://bugs.launchpad.net/bugs/269997"]
https://bugs.launchpad.net/bugs/269997[/URL]

---

### Post by vikrant82 on 2008-09-16
Yes, indeed its fixed with last ffpmeg updates.

Thanks for replying, I was keeping away from ffmpeg, afraid of dreaded 0x0000 codecs it tried to use.

Although I do wonder, why other people didn't experience it, if it was indeed a medibuntu problem.

---


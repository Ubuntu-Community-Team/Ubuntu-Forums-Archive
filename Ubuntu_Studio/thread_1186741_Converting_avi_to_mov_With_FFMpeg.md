---
title: "Converting avi to mov With FFMpeg"
date: 2009-06-13
forum: Ubuntu Studio
---

### Post by daemon3 on 2009-06-13
I'm having a little trouble converting a movie from AVI to MOV.  I can do it fine with other video files of the same format.  The video is almost an hour long, so I'm wondering if that has something to do with it.  I can playback the original AVI just fine.
This is what I type in the command line (and the output):
```
user@user-laptop /media/VERBATIM/Multimedia/Videos/ $ ffmpeg -i On\ Stage\ 01-29-09.avi -target ntsc-dv On\ Stage\ 01-29-09.mov 
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
[avi @ 0x838aac0]sample size (1) != block align (1024)

Seems stream 0 codec frame rate differs from container frame rate: 60.00 (60/1) -> 30.00 (30/1)
Input #0, avi, from 'On Stage 01-29-09.avi':
  Duration: 00:41:54.15, start: 0.000000, bitrate: 4219 kb/s
    Stream #0.0: Video: h264, yuv420p, 1280x720, 30 tbr, 30 tbn, 60 tbc
    Stream #0.1: Audio: adpcm_ms, 22050 Hz, mono, s16, 88 kb/s
File 'On Stage 01-29-09.mov' already exists. Overwrite ? [y/N] y
Output #0, dv, to 'On Stage 01-29-09.mov':
    Stream #0.0: Video: dvvideo, yuv411p, 720x480, q=2-31, 200 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[pcm_s16le @ 0x84acee0]Can't process DV frame #14877. Insufficient video data or severe sync problem.
```

This is what FFMpeg does every time.  It doesn't do this for other videos.  Thank you in advance.

---

### Post by igorzwx on 2009-06-13
**youtube avi to mov conversion**
[http://ubuntuforums.org/showthread.php?t=510604](http://ubuntuforums.org/showthread.php?t=510604)

[http://www.google.com/search?q=howto%20avi%20mov%20mencoder&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=howto%20avi%20mov%20mencoder&ie=UTF-8&oe=UTF-8)

Google may help!

---

### Post by daemon3 on 2009-06-16
That ubuntuforums link gave me code for mencoder.  I tried it, but only got the audio converted for Cinelerra and the video was dreadful for playback.

Still getting the same error it seems to happen on large files.  It seems to recursively print out a line like this:
```
frame=29814 fps= 29 q=0.0 size= 4192172kB time=1192.51 bitrate=28798.2kbits/s
```
and eventually spit something out like this:
```
av_interleaved_write_frame(): Error while opening file
```
The file is almost an hour long and is 1.3 GB.  Is the file too big for FFMpeg.
And yes, I have plenty of ram and plenty of disk space.

---


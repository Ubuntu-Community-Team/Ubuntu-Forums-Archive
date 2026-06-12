---
title: "How to strip video from audio"
date: 2009-05-09
forum: Ubuntu Studio
---

### Post by camper365 on 2009-05-09
I have a video file and I want just the audio.
What I want is to take pictures and put sound in the background, but the sound comes from a video. I don't want the video showing, just the audio.

---

### Post by FakeOutdoorsman on 2009-05-10
Show the output of:
```
ffmpeg -i inputfile.mp4
```

---

### Post by camper365 on 2009-05-10
```
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

Seems stream 1 codec frame rate differs from container frame rate: 30.00 (30/1) -> 15.00 (15/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Documents/Linux Presentation/cinelerra/video.mp4':
  Duration: 00:04:24.03, start: 0.000000, bitrate: 264 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 240x180, 15 tbr, 15 tbn, 30 tbc
At least one output file must be specified

```

---

### Post by FakeOutdoorsman on 2009-05-11
This command will copy the audio from the input file.  There is no encoding occuring here, just copying the stream:
```
ffmpeg -i video.mp4 -acodec copy output.aac
```
or
```
ffmpeg -i video.mp4 -acodec copy -vn output.mp4
```

---


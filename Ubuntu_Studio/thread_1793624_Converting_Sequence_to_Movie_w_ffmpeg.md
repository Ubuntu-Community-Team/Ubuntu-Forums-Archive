---
title: "Converting Sequence to Movie w/ ffmpeg"
date: 2011-06-29
forum: Ubuntu Studio
---

### Post by Geremia on 2011-06-29
I am trying to convert a sequence of images named anim0001.png, anim0002.png, anim0003.png, etc., to a movie with ffmpeg, but everytime I issue the command```
ffmpeg -f image2 -r 30 -i anim%04d.png out.mp4
```, I get a movie with only 2 frames. Why? Here's the full output:```
FFmpeg version 0.6.2-4:0.6.2-1ubuntu1, Copyright (c) 2000-2010 the Libav developers
  built on Mar 22 2011 15:55:04 with gcc 4.5.2
  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  **WARNING: library configuration mismatch**
  libavutil   configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6.2-1ubuntu2+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, image2, from 'anim%04d.png':
  Duration: 00:00:00.06, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: png, rgb24, 1280x720, 30 tbr, 30 tbn, 30 tbc
Output #0, mp4, to 'out.mp4':
  Metadata:
    encoder         : Lavf52.64.2
    Stream #0.0: Video: mpeg4, yuv420p, 1280x720, q=2-31, 200 kb/s, 30 tbn, 30 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=    2 fps=  0 q=2.0 Lsize=      93kB time=0.07 bitrate=11459.0kbits/s    
video:92kB audio:0kB global headers:0kB muxing overhead 0.819291%

```ffmpeg generally works fine for everything else. Thanks

---

### Post by jejeman on 2011-06-29
Command is good. See if the png files are named properly, without missing sequential numbers. Ffmepg can't handle missing files.

---

### Post by Geremia on 2011-06-29
> **jejeman said:**
> Command is good. See if the png files are named properly, without missing sequential numbers. Ffmepg can't handle missing files.Yes, that is exactly the problem! There were missing ones. I had to put them in sequence by running: ```
n=0; for i in *.png ; do mv -v "$i" sequenced/"$(printf "%04d" $n).png"; n=$(($n+1)); done
```, which moves them to a folder called "sequenced" and in sequence! So the "library configuration mismatch" warning didn't affect anything.

---


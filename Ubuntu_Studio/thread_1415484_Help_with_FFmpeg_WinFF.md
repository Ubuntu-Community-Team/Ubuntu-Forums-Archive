---
title: "Help with FFmpeg WinFF"
date: 2010-02-24
forum: Ubuntu Studio
---

### Post by toddbmobile on 2010-02-24
I have recently updated WinFF to the newest version in hopes of fixing the following problem below.  I sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update^Cnstall medibuntu-k to take advantage of medibumtu then I have installed ffmpeg libavcodec-extra-52. I also ran sudo apt-get install ubuntu-restricted-extras. I still cannot get WinFF to output my video. I tried to bold some areas in the dump below. Please help me.



 FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
[NULL @ 0x92599d0]Invalid and inefficient vfw-avi packed B frames detected
Input #0, avi, from '/home/mydir/Videos/mymoviename.avi':
  Duration: 01:35:55.48, start: 0.000000, bitrate: 1017 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x272 [PAR 1:1 DAR 40:17], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 32 kb/s
**Unable to find a suitable output format for '/dev/null'**
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
[NULL @ 0x955d9d0]Invalid and inefficient vfw-avi packed B frames detected
Input #0, avi, from '/home/mydir/Videos/mymoviename.avi':
  Duration: 01:35:55.48, start: 0.000000, bitrate: 1017 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x272 [PAR 1:1 DAR 40:17], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 32 kb/s
**Cannot read log file '/home/mydir/mymoviename.log-0.log' for pass-2 encoding: No such file or directory**
Press Enter to Continue


Also I this dump is from when I try using the Microsoft / Zune options from the drop down menus in WinFF.
The PSP option works fine. It is just the option to convert to Zune format.

---


---
title: "ffmpeg convert video with no picture"
date: 2008-07-29
forum: Ubuntu Studio
---

### Post by sapparod on 2008-07-29
I convert a video file from wmv to flv but the result ending with audio file without video layer. 

I executed 

> ffmpeg -i I.wmv -copyts -ar 44100 -s 320x240 ./III.flv

here are result  : 

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --prefix=/usr --libdir=/usr/lib --shlibdir=/usr/lib --mandir=/usr/share/man --enable-static --enable-shared --cc=i686-pc-linux-gnu-gcc --disable-mmx --disable-altivec --disable-debug --disable-audio-oss --disable-v4l --disable-v4l2 --disable-dv1394 --disable-network --disable-zlib --disable-opts --enable-libmp3lame --enable-libvorbis --enable-libogg --enable-libtheora --enable-libogg --enable-liba52 --enable-libxvid --enable-libogg --enable-libfaad --enable-libfaac --enable-libamr-nb --enable-libamr-wb --enable-gpl --enable-pp --disable-strip
  libavutil version: 49.4.0
  libavcodec version: 51.40.4
  libavformat version: 51.12.1
  built on Jul 29 2008 08:20:51, gcc: 3.4.6 

[COLOR="MediumTurquoise"]Seems stream 3 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 15.00 (15/1)[/COLOR]
Input #0, asf, from 'I.wmv':
  Duration: 00:01:43.9, start: 3.358000, bitrate: 275 kb/s
  Stream #0.0: Audio: wmav2, 8000 Hz, stereo, 12 kb/s
  Stream #0.1: Video: wmv1, 200x150, 1000.00 fps(r)
  Stream #0.2: Video: wmv1, 200x150, 1000.00 fps(r)
  Stream #0.3: Video: wmv1, yuv420p, 200x150, 15.00 fps(r)
PIX_FMT_YUV420P will be used as an intermediate format for rescaling
Output #0, flv, to './III.flv':
  Stream #0.0: Video: flv, yuv420p, 320x240, q=2-31, 200 kb/s, 15.00 fps(c)
  Stream #0.1: Audio: libmp3lame, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
frame=    0 fps=  0 q=0.0 Lsize=     871kB time=103.5 bitrate=  68.9kbits/s
[COLOR="PaleGreen"]video:0kB audio:809kB global headers:0kB muxing overhead 7.689094%[/COLOR]

Would you guys know how to solve this problem? 

Thanks.

---

### Post by Creative2 on 2008-07-29
fuoco tools 
winff
pytube
avidemux

---

### Post by FakeOutdoorsman on 2008-07-29
Your input video is showing one audio stream (Stream #0.0) and three video streams (0.1, 0.2, 0.3).  If you don't declare which streams you want to encode, FFmpeg will simply choose the first audio and first video streams it encounters.  You can use the -map option to tell FFmpeg which streams to encode:
```
ffmpeg -i I.wmv -copyts -ar 44100 -s 320x240 -map 0:0 -map 0:3 ./III.flv
```
This example should encode the audio stream (0:0), and the third video stream (0:3).  A good explaination of this is the [Mapping Channels]("http://howto-pages.org/ffmpeg/#map") section of [Using ffmpeg to manipulate audio and video files]("http://howto-pages.org/ffmpeg/").

---


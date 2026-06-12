---
title: "ffmpeg - time length difference when converting from avi to mpeg"
date: 2008-10-24
forum: Ubuntu Studio
---

### Post by yaplimin on 2008-10-24
I downloaded some video files from my digital camcorder to my computer. These are AVI files and are huge, 1 hour = ~13 Gb, and I want to convert them to mpeg files to save disk space. 

Having a small problem with using ffmpeg. This is the command I use on a test file:

```
ffmpeg -i y.AVI -target ntsc-dvd -b 9000000 -r 29 -s 720x480 -aspect 16:9 -acodec mp2 -ar 48000 -ab 224000 y.mpg
```

This is my output:
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:28:05, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, avi, from 'y.AVI':
  Duration: 00:00:32.2, start: 0.000000, bitrate: 29817 kb/s
  Stream #0.0: Video: dvvideo, yuv411p, 720x480, 29.97 fps(r)
  Stream #0.1: Audio: pcm_s16le, 32000 Hz, stereo, 1024 kb/s
Output #0, dvd, to 'y.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 720x480, q=2-31, 9000 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: mp2, 48000 Hz, stereo, 224 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=  967 q=2.0 Lsize=   37054kB time=32.2 bitrate=9417.5kbits/s    
video:35477kB audio:882kB global headers:0kB muxing overhead 1.910601%

In the conversion, the output file video and audio is good. The only problem I'm having is the time length of the mpeg file does not match the time length of the original file. For example, the original AVI file is 32 secs. long which is reported in its file properties and when the video file is played in MPlayer. 

However, the properties of the converted mpeg file shows it is 20 secs. When I play it in MPlayer it plays fine but the time counter shows that it is a 20 sec. clip.  The clip is actually still 32 seconds. long in real-time but the counter in MPlayer shows 20 secs. and it counts much slower.

I noticed that changing the bit rate setting in ffmpeg affects the counter. Shorter bit rates result in shorter times in the mpeg file. For low bit rates, the counter can show 0 seconds even though the file is playing.

I'm just expecting that the converted files should report the same time length as the original files.  I don't want my original 1 hour video files to show up as a 45 min. files after conversion. Again, in real-time the time lengths are the same. Just the time reported in MPlayer is different. 

Is this how ffmpeg normally works?  Am I doing something wrong in my conversion?  Do I have a wrong setting in the command I'm using?

Thanks.

---

### Post by justsomedude on 2008-10-24
> -r 29

There should be no reason to force a framerate, try it without.

The bit rate should have no effect on the counter.


EDIT:


Another thing:

```
-ar 48000
```

Never change the framerate or resample your audio unless you absolutely have to!

---

### Post by yaplimin on 2008-10-25
I've simplified the problem here. Just doing a simple AVI to mpg conversion with mostly default values.

```
ffmpeg -y -i y.AVI -target ntsc-dvd y.mpg
```

Results:

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:28:05, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, avi, from 'y.AVI':
  Duration: 00:00:32.2, start: 0.000000, bitrate: 29817 kb/s
  Stream #0.0: Video: dvvideo, yuv411p, 720x480, 29.97 fps(r)
  Stream #0.1: Audio: pcm_s16le, 32000 Hz, stereo, 1024 kb/s
Output #0, dvd, to 'y.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 720x480, q=2-31, 6000 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: ac3, 48000 Hz, stereo, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=  967 q=3.4 Lsize=   25990kB time=32.2 bitrate=6605.5kbits/s    
video:23664kB audio:1764kB global headers:0kB muxing overhead 2.208977%


The original AVI file is real-time 32 sec. long and the time counter shows 32 sec. No problem.

The resulting MPG file is real-time 32 sec. long BUT the time counter shows 20 sec.

Has anybody seen this before?  Has anybody done this conversion before and not have a different time counter values?

---


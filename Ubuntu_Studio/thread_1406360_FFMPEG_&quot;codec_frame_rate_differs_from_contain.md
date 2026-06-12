---
title: "FFMPEG &quot;codec frame rate differs from container frame rate&quot; error. Got an idea?"
date: 2010-02-13
forum: Ubuntu Studio
---

### Post by MetalMusicAddict on 2010-02-13
So I'm converting a VOB to x264. The VOB is 30fps but the resulting .mkv is 60fps. Forcing the rate with ***-r*** doesn't work either. This actually happens when I try to convert anything to x264. Got any ideas?

[U]My script:
[/U]```
[SIZE="1"]#!/bin/bash

for a in *.VOB
        do
                OUT=`echo "$a" | sed s/"\.VOB$"/"\.mkv"/g`
		ffmpeg -y -i "$a" -an -threads 2 -vcodec libx264 -deinterlace -b 1400k -bt 175k -r 30 -flags +loop+slice -coder ac -refs 1 -deblockalpha 0 -deblockbeta 0 -partitions +parti4x4+partp8x8+partb8x8 -me_method epzs -subq 1 -me_range 21 -cmp +chroma -bf 3 -b_strategy 1 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 5000k -bufsize 2M -cmp 1 -s 640x352 -aspect 16:9 -f matroska -pass 1 /dev/null

		ffmpeg -y -i "$a" -threads 2 -vcodec libx264 -deinterlace -b 1400k -bt 175k -r 30 -flags +loop+slice -coder ac -refs 5 -deblockalpha 0 -deblockbeta 0 -partitions +parti4x4+partp8x8+partb8x8 -me_method full -subq 6 -me_range 21 -cmp +chroma -bf 3 -b_strategy 1 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 5000k -bufsize 2M -cmp 1 -s 640x352 -aspect 16:9 -f matroska -acodec libmp3lame -ab 192k -ar 44100 -ac 2 -pass 2 "$OUT"

        done[/SIZE]
```

_Terminal output:_
```
[SIZE="1"]atm@dash:/media/Rip_Temp/VIDEO_TS$ sh dvd2mkv
FFmpeg version SVN-r21396, Copyright (c) 2000-2010 Fabrice Bellard, et al.
  built on Jan 23 2010 09:31:14 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 7. 0 / 50. 7. 0
  libavcodec    52.48. 0 / 52.48. 0
  libavformat   52.47. 0 / 52.47. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 9. 0 /  0. 9. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mpeg @ 0x9e2d380]max_analyze_duration reached

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (30000/1001)
Input #0, mpeg, from 'VTS_01_1.VOB':
  Duration: 01:11:16.17, start: 0.280633, bitrate: 12628 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], 9800 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
[libx264 @ 0x9e368f0]using SAR=44/45
[libx264 @ 0x9e368f0]using cpu capabilities: MMX2 SSE2Slow
[libx264 @ 0x9e368f0]profile Main, level 3.0
Output #0, matroska, to '/dev/null':
    Stream #0.0: Video: libx264, yuv420p, 640x352 [PAR 44:45 DAR 16:9], q=2-51, pass 1, 1400 kb/s, 1k tbn, 30 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame= 1946 fps= 73 q=-2.0 Lsize=       0kB time=64.90 bitrate=   0.0kbits/s[/SIZE]
```

---

### Post by LuridCinema on 2010-02-13
It looks like it went ahead and rendered ..correct ???

"
[SIZE=1]Press [q] to stop encoding"
frame= 1946 fps= 73 q=-2.0 Lsize=       0kB time=64.90 bitrate=   0.0kbits/s

When I see the above, it means it rendered a video.. did the video play ??

I get the same error sometimes and I get a video out...
[/SIZE]

---

### Post by MetalMusicAddict on 2010-02-14
> **LuridCinema said:**
> It looks like it went ahead and rendered ..correct ???

"
[SIZE=1]Press [q] to stop encoding"
frame= 1946 fps= 73 q=-2.0 Lsize=       0kB time=64.90 bitrate=   0.0kbits/s

When I see the above, it means it rendered a video.. did the video play ??

I get the same error sometimes and I get a video out...
[/SIZE]

Oh sure. It finishes and plays fine. Just @60fps. Twice what it should be.

---

### Post by LuridCinema on 2010-02-14
Have you tried the -r 29.97 as the frame rate switch ??? maybe that will work

---

### Post by MetalMusicAddict on 2010-02-14
> **LuridCinema said:**
> Have you tried the -r 29.97 as the frame rate switch ??? maybe that will work

Yup. :) Then it just says the framerate is 59.97. (or something)

---


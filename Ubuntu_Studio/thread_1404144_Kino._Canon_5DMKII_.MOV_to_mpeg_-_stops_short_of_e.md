---
title: "Kino. Canon 5DMKII .MOV to mpeg - stops short of end."
date: 2010-02-11
forum: Ubuntu Studio
---

### Post by wetinwales on 2010-02-11
Hi All
Running Karmic new install, 64bit, 4core. Installed ffmpeg-mt with Mplayer which plays 1920x1080 .MOV files good. Installed Kino and Cinelerra 4.1 Both working well. 
Kino DV device control and capture working well with Sony Mini DV DSR V10P. 
Cinelerra plays .MOV files (image only) and seems relatively stable - but will not accept the sound from .MOV (sowt codec not recognised??)

So...
use Kino to convert the Canon .MOV file (1920x1080) to MPEG. OK. I export audio only in Kino and apply to Cinelerra. Great. Perfect video/audio sync.

..BUT even though the MPEG video and audio are in perfect sync, the resulting MPEG stops short of the end of the original .MOV file by a proportion of the whole .MOV file. ie I am loosing the last part of ALL my shots! On a 9 minute take I am loosing the last 1min or so; viewed in Kino.

Can anyone tell me why Kino stops converting before of the end of the .MOV file?

---

### Post by LuridCinema on 2010-02-11
Have you installed all of the codecs / libraries in the below thread ?
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

it might get you what you need for cinelerra to accept the sound. I am able to get Cinelerra to handle sound from an .MOV file no probs here, 

BELOW are the properties of my .MOV file from my camera

```
ffmpeg -i 100_0013.MOV
FFmpeg version SVN-r21602, Copyright (c) 2000-2010 Fabrice Bellard, et al.
  built on Feb  1 2010 19:08:32 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 8. 0 / 50. 8. 0
  libavcodec    52.51. 0 / 52.51. 0
  libavformat   52.50. 0 / 52.50. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 9. 0 /  0. 9. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 0 codec frame rate differs from container frame rate: 119.88 (120000/1001) -> 59.94 (60000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '100_0013.MOV':
  Metadata:
    major_brand     : qt  
    minor_version   : 0
    compatible_brands: qt  
    comment         : KODAK Zx1 Pocket Video Camera
    comment-eng     : KODAK Zx1 Pocket Video Camera
  Duration: 00:00:16.34, start: 0.000000, bitrate: 14088 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 13927 kb/s, 59.94 fps, 59.94 tbr, 90k tbn, 119.88 tbc
    Stream #0.1(eng): Audio: aac, 48000 Hz, stereo, s16, 127 kb/s
At least one output file must be specified
```

---

### Post by wetinwales on 2010-02-11
Hi LuridCinema
Are you playing files from a 5DMKII ?
Are you using Cinelerra 4.1 ?

Thanks for the tutorial URL. Its great.

---

### Post by LuridCinema on 2010-02-11
No canon.. as you can see in the file info in the code above its from a Kodak Zx1

Im going to do more tuts on videos and using FOSS to create effects and edit videos

---

### Post by wetinwales on 2010-02-12
I realised that the Cinelerra 4.1 is for Jaunty. This may be the problem as the Viewer window will not accept files as well as the .mov sound channel.
So.. can I face all those hours taking the system back to full working Jaunty eh..!!

Thanks for your clues LuridCinema

---


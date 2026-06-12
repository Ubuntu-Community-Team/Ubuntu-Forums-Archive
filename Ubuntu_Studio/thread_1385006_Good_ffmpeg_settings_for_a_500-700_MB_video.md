---
title: "Good ffmpeg settings for a 500-700 MB video"
date: 2010-01-19
forum: Ubuntu Studio
---

### Post by MrSergeiMosin on 2010-01-19
I have a series of videos ranging between 450 and 700 MB. Problem is, they are in a wide variety of formats. I spend some time overseas for Uncle Sam and I am concerned about continued availability of the internet at my location. If I have to reinstall my x/k/ubuntu mish-mash I may or may not have the ability to regain the restricted extras. 

All of that leads up to this: I'm trying to use ffmpeg to convert all of my current videos into .ogv so I can play them on a fresh Ubuntu or Fedora install. My problem is that I always end up with crazy huge file sizes. ~150MB winds up closer to 500 after I convert. I dug around on google for a few days, but i cant seem to find specific settings to keep my output .ogv files between the same 450-700MB range. Has anybody else developed a setting for ffmpeg that can keep video output reasonable the source files all more or less look like this:


Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '********** ** ******.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42isom
    encoder         : HandBrake 0.9.3 2008112300
  Duration: 02:14:03.96, start: 0.000000, bitrate: 513 kb/s
    Stream #0.0(eng): Video: mpeg4, yuv420p, 512x224 [PAR 1:1 DAR 16:7], 350 kb/s, 24.65 fps, 24k tbr, 48k tbn, 24k tbc
    Stream #0.1(eng): Audio: aac, 48000 Hz, stereo, s16, 159 kb/s
    Stream #0.2(eng): Subtitle: text / 0x74786574

Size on that particular file is 492.8MB

---


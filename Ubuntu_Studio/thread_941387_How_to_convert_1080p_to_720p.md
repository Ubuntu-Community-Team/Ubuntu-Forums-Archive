---
title: "How to convert 1080p to 720p?"
date: 2008-10-08
forum: Ubuntu Studio
---

### Post by Aero-Z on 2008-10-08
Hi,

Is there a software which could do that in Ubuntu? The file format is mkv. Also if there is, then how exactly can I get this done?

Thanks

---

### Post by aeiah on 2008-10-09
things get complicated and time consuming when converting HD content, primerily because you need to keep a lot of the quality and because the filesizes are rather large. basically you first need to strip out the video and audio from the mkv. you dont need to do anything to the audio but you'll want to repackage it into a new .mkv later on once you've got a smaller video. you can use ffmpeg or mencoder to convert your video down to 720p. i dont know the settings off the top of my head, as things get very complicated for x264 content. this might work, for example, but i couldnt tell you what half of the flags do :p

```
ffmpeg -i <input video> -b 3000k -vcodec h264 -acodec copy -coder 1 -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -me hex -subq 5 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 <output video>.mp4
```
(from [http://bbs.archlinux.org/viewtopic.php?id=35836](http://bbs.archlinux.org/viewtopic.php?id=35836) )

and that wont even change the resolution, just the bitrate and various other bits and pieces to do with quality.

is there any reason why you cant just download a 720p version, or play the 1080p version?

---

### Post by Aero-Z on 2008-10-13
> **aeiah said:**
> things get complicated and time consuming when converting HD content, primerily because you need to keep a lot of the quality and because the filesizes are rather large. basically you first need to strip out the video and audio from the mkv. you dont need to do anything to the audio but you'll want to repackage it into a new .mkv later on once you've got a smaller video. you can use ffmpeg or mencoder to convert your video down to 720p. i dont know the settings off the top of my head, as things get very complicated for x264 content. this might work, for example, but i couldnt tell you what half of the flags do :p

```
ffmpeg -i <input video> -b 3000k -vcodec h264 -acodec copy -coder 1 -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -me hex -subq 5 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 <output video>.mp4
```
(from [http://bbs.archlinux.org/viewtopic.php?id=35836](http://bbs.archlinux.org/viewtopic.php?id=35836) )

and that wont even change the resolution, just the bitrate and various other bits and pieces to do with quality.

is there any reason why you cant just download a 720p version, or play the 1080p version?
Yea, I'm unable to get the 720p version. I thought that my PC might be weak if I play 1080p video in 720p screen because of on-the-fly resizing. I had few fps bumps but it worked out pretty ok.
Thanks for the reply :)

---


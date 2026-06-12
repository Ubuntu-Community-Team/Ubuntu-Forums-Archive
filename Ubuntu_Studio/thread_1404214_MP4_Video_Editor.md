---
title: "MP4 Video Editor?"
date: 2010-02-11
forum: Ubuntu Studio
---

### Post by ndmp on 2010-02-11
Hey guys!

Can anyone recommend a video editing application which lets you change the resolution of MP4s? I'm trying to convert one to watch on my HTC hero but the resolution is too high and it is mega choppy.

Thanks! :popcorn:

---

### Post by rylleman on 2010-02-11
You could try Handbrake or Avidemux.
[Or use my nautilus-script]("http://rylanderanimation.se/2009/10/12/convert-to-quicktime-player-compliant-movs/"), just alter resolution and size-settings and you got a handy converter.

---

### Post by fomaa on 2010-02-11
You can use ffmpeg.

---

### Post by FakeOutdoorsman on 2010-02-11
> **ndmp said:**
> Hey guys!

Can anyone recommend a video editing application which lets you change the resolution of MP4s? I'm trying to convert one to watch on my HTC hero but the resolution is too high and it is mega choppy.

Thanks! :popcorn:

I don't have one of these devices, so I'm unsure how picky it is, but you can try this FFmpeg command:
```
ffmpeg -i input.mp4 -acodec copy -vcodec libx264 -vpre hq -vpre ipod320 -crf 26 -s 320x240 -threads 0 output.mp4
```
Note that you will have to enable the libx264 encoder.  It's an easy procedure and is explained here:
[url=http://ubuntuforums.org/showthread.php?t=1117283]
HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg[/url]

---

### Post by ndmp on 2010-02-11
Thanks guys :)

---


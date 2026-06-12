---
title: "Convert AVI to Flash Video Format using ffmpeg"
date: 2008-06-18
forum: Ubuntu Studio
---

### Post by vital101 on 2008-06-18
Hey everyone,

I was wondering how I might go about converting an .avi file to a flash video format file.  I read that ffmpeg is capable of this, so I installed it and then read the man page.  I wasn't able to find anything about converting to this format.

Has anyone had any luck with this?  If so, how did you do it?

Thanks,
vital101

---

### Post by FakeOutdoorsman on 2008-06-18
Basic usage:
```
ffmpeg -i inputvideo.avi outputvideo.flv
```
Default values will be used for whatever you don't specify. Since I didn't supply a bitrate, such as -b 384k, it will use the default 200 kb/s.  If you get the error "flv does not support that sample rate, choose from (44100, 22050, 11025)", then use the "-ar" option with the appropriate sampling rate (44100, 22050, or 11025).

ffmpeg from the Ubuntu repos has not been compiled to support restricted codecs such as mp3 and aac.  You will need to use a third-party repository like [Medibuntu]("http://medibuntu.org"), [compile ffmpeg yourself]("http://ubuntuforums.org/showthread.php?t=786095"), or use another program such as mencoder.

---

### Post by Creative2 on 2008-06-18
hola' fuoco tools use ffmpeg

this is the fuoco command line 

ffmpeg -i INPUT -b 600k -r 30 -ab 128k -ar 44100 -s 640x480 -ac 2 -y OUTPUT

---

### Post by vikramjeet.singla on 2008-07-08
hi vital,
please refer to links below for more information:

[http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html](http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html)
[http://www.luar.com.hk/blog/?p=670](http://www.luar.com.hk/blog/?p=670)

enjoy ;)

---

### Post by timcredible on 2008-07-08
if you'd like a gui front end for ffmpeg, try winff, it's much easier than trying to figure out all the ffmpeg parameters.  although, if you don't set the parameter -sameq (same quality for the target as source), you may be very disappointed with the outcome.

---

### Post by Ms_Angel_D on 2008-09-09
> **timcredible said:**
> if you'd like a gui front end for ffmpeg, try winff, it's much easier than trying to figure out all the ffmpeg parameters.  although, if you don't set the parameter -sameq (same quality for the target as source), you may be very disappointed with the outcome.

Thanks a lot for this handy piece of info :)

---


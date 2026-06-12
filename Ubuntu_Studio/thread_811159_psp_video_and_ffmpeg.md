---
title: "psp video and ffmpeg"
date: 2008-05-28
forum: Ubuntu Studio
---

### Post by viniosity on 2008-05-28
I've gone through the forums and googled pretty extensively but I can't find a way to encode video for my psp using ffmpeg except in 320x240 or 368x208.  No other resolution combinations work (I've tried 352x480, 480x272, 480x270, 352x272, 352x276, etc etc)

Here's the command that works at 320x240 and 368x208:

```

ffmpeg -i 001_movie.m4v -f psp -r 29.97 -b 1000k -ar 24000 -ab 64k -s 320x240 M4V00021.MP4

```

Anyone able to do this at 480x272 or XXX by 272?

---

### Post by FakeOutdoorsman on 2008-05-29
According to Robert Swain, the PSP can handle 320×240 or up to 368×208.  Check his [PSP video guide]("http://rob.opendot.cl/index.php/useful-stuff/psp-video-guide/") for examples and more info.

---

### Post by viniosity on 2008-05-29
Actually, I finally got it figured out.  Wrote it up [on my blog]("http://www.urbanpuddle.com/articles/2008/05/29/a-quick-railscasts-to-psp-script").

---


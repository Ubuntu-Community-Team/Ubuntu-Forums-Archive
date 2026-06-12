---
title: "Script to aid in recording from webcam"
date: 2009-05-26
forum: Ubuntu Studio
---

### Post by RuarriS on 2009-05-26
Hello,

What I'm trying to accomplish is the following: 
[LIST][*]'d like to capture audio and video from my USB webcam (I'm about 75% there already)[*]create a script that is clickable and doesn't bring up that annoying dialog about running in terminal, displaying, or just running it...[*]And finally it should name the files according to the date (or atleast incrementally).

[/LIST]

So this is what I have so far to encode (ffmpeg and mencoder didn't work...something about mencoder seg faulting or floating point error). I got this from a site and mixed it with my own tinkering.

> gst-launch-0.10 v4l2src device=/dev/video1 ! video/x-raw-yuv,width=320,height=240,framerate=15/1 ! ffmpegcolorspace ! theoraenc quality=60 !  queue ! oggmux name=mux alsasrc device="hw:1,0" ! audiorate ! audio/x-raw-int,rate=16000,channels=1,depth=16 ! queue ! audioconvert ! vorbisenc !  mux. mux. ! queue ! filesink sync=true location=test.ogg qos=true

If anyone has tips to help me maximize the quality of the video or anything at all towards making a script, it would be appreciated.

---

### Post by Misantropo75 on 2009-12-03
How would i do this using autoaudiosrc?

Thanks!

---


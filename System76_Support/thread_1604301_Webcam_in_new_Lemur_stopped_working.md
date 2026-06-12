---
title: "Webcam in new Lemur stopped working"
date: 2010-10-23
forum: System76 Support
---

### Post by Azilie on 2010-10-23
Hi System76 & Community,

Just this week I got my new Lemur UltraThin running 10.10 and I'm quite pleased with it thus far. However, something has just gone wrong with my integrated webcam.  When I first got it (4 days ago) it worked fine and I took some pictures in Cheese.  Now, however, when I go into that program, it says "No device found: please refer to the help for further information."

And the help suggested I post in the Ubuntu Forums, so that's what I'm doing.

I'm a beginner with Linux/Unix, so I might need some steps you all think are basic spelled out for me, but I want to learn more about Linux so I'll just think of this as a chance to do that.

So far I've tried to see if something might be wrong with gstreamer.  Here's what came up when I ran gstreamer-properties:

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline3/GstV4lSrc:v4lsrc1]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline4/GstV4l2Src:v4l2src1:
system error: No such file or directory]


Any help would be much appreciated!

---

### Post by Azilie on 2010-10-24
I also meant to add that I did install a bunch of packages suggested by the updates yesterday. I suspect one of those may have interfered with the camera, but I'm not sure how to figure that out and check, and how to reverse that if necessary.

---

### Post by Flyers2391 on 2010-10-24
> **Azilie said:**
> I also meant to add that I did install a bunch of packages suggested by the updates yesterday. I suspect one of those may have interfered with the camera, but I'm not sure how to figure that out and check, and how to reverse that if necessary.

have you toggled the web cam off & on with fn+f10 ?

---

### Post by Azilie on 2010-10-24
Hey!  That did it!  So nice when it's something simple like that that I'd just overlooked.  Thanks, Flyers2391!

---

### Post by BigD77 on 2010-10-26
> **Flyers2391 said:**
> have you toggled the web cam off & on with fn+f10 ?


I am having similar problems with a Logitech web cam.  I tried fn+f10, and it opened up the CD tray.

---

### Post by isantop on 2010-10-26
Is this on a System76 laptop machine? If not, the hotkey may differ, and it probably won't turm on an external webcam anyway. You may need to consult the documentation for the webcam.

---


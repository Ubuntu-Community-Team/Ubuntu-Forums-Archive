---
title: "scaling video size down"
date: 2008-05-26
forum: Ubuntu Studio
---

### Post by Eman1955 on 2008-05-26
I'm using Mencoder to convert DVD to mpeg.  The following works fairly nicely, but produces too large a file, 1GB.  The scale command doesn't work so I know I'm doing something wrong there.  I want to scale it down from 720x480 to work on an Arcos video player and also to fit on a CD.  On the Windows side, I can use AnyDVD with cloneDVDMobile and get the video to size at 480x270 witha file size of around 700MB.  I know I can keep using AnyDVD, but would rather learn more about Linux and eventually deep 6 Windows.

mencoder dvd://-chapter 1-32 -vf scale=480:270, -o indy.avi -ovc lavc -lavcopts vcodec=mpeg4 -oac copy -ofps 25 of mpeg4

Any help out there?

---


---
title: "Playing video file kicks me to Login screen"
date: 2012-03-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by 1roxtar on 2012-03-19
I am not sure if some of you are experiencing this bug.  Everytime I try playing a local video file, it doesn't matter which player I use, it crashes and kicks me back to the Login screen.  I am using a Toshiba Satellite laptop with ATI video drivers.

---

### Post by xajeiw9I on 2012-03-20
This is a problem with the proprietary ATI driver (FGLRX). Try installing VLC and changing video output to something with "GL". Or uninstall FGLRX.

---

### Post by Procrustes on 2012-03-20
I found that upgrading to to the Catalyst driver 12.2 eliminated the crash to login screen on playing a vid bug

---

### Post by 1roxtar on 2012-03-20
Thank you.  I'll try your suggestions and post my results as well.

---

### Post by cariboo on 2012-03-20
> **1roxtar said:**
> Thank you.  I'll try your suggestions and post my results as well.

According to your signature, you are using an Nvidia graphics adapter, installing the ATI/AMD drivers, won't solve your problem.

---

### Post by 1roxtar on 2012-03-20
The computer in my signature is my desktop.  I am having this particular problem on my Toshiba laptop which uses ATI drivers.

---

### Post by ggx123qwe on 2012-03-20
Which version of fglrx will 12.04 ship with?

---

### Post by bcarlowise on 2012-03-21
> **1roxtar said:**
> I am not sure if some of you are experiencing this bug.  Everytime I try playing a local video file, it doesn't matter which player I use, it crashes and kicks me back to the Login screen.  I am using a Toshiba Satellite laptop with ATI video drivers.

I had the same problem on my laptop (which has an ATI video card) but I discovered the problem was not related to the video drivers but to missing codecs to play the video. Make sure the following gstreamer packages are installed and then try again:

GStreamer ffmpeg video plugin
GStreamer extra plugins
GStreamer plugins for aac,xvid,mpeg2,faad

---

### Post by Gregory Lee on 2012-03-21
Aside from youtube or other web videos, I can't play any videos without getting kicked out to the login window.  I've tried a number of different times with different video types, with all the video players I have -- always the same result.  I just tried again with an meg2 video.  Here are the gstreamer codec libraries on my system:
```
~# ls /usr/lib/gstreamer-0.10/
libfsfunnel.so         libfsrtcpfilter.so     libgnl.so         libgstffmpegscale.so  libgstmplex.so     libgstpython.so
libfsmsnconference.so  libfsrtpconference.so  libgstclutter.so  libgstffmpeg.so       libgstnice.so      libgstxvid.so
libfsrawconference.so  libfsvideoanyrate.so   libgstfaac.so     libgstmpeg2enc.so     libgstpostproc.so
```
I'm using the fglrx driver.

---

### Post by tista on 2012-03-22
Guys,

Then you'd better to go back to open-sourced driver "radeon/gallium" from fglrx to test them...

Regards,
Tista

---

### Post by Hreinsi on 2012-03-22
[http://pctrends.freeforums.org/ati-amd-catalyst-12-2-for-lts-xlt-2-t318.html](http://pctrends.freeforums.org/ati-amd-catalyst-12-2-for-lts-xlt-2-t318.html)

This fixed my prob playin videos

---

### Post by kaldor on 2012-03-22
It's probably a better idea to use the OSS driver during the development release anyway. Canonical can do little to nothing about Fglrx, so testing the default drivers should be priority.

Sometimes I wish that AMD would just kill off Catalyst for Linux and just focus all effort on the open source drivers so that they could progress a lot faster. Sadly, I doubt that would be possible due to the legal issues.

---


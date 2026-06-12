---
title: "vdpau still doesn't work in 12.10"
date: 2012-10-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by monkeybrain2012 on 2012-10-17
This bug apparently still hasn't been fixed in 12.10

[https://bugs.launchpad.net/unity/+bug/993397](https://bugs.launchpad.net/unity/+bug/993397)

Using mplayer/mplayer2 in full screen for 1080p still uses over 50% of cpu while it should have been around 10% with vdpau enabled. 

I have tried with all versions of nvidia drivers (Nvidia-current, current-updated and experimental) It seems to be a compiz bug.

---

### Post by pqwoerituytrueiwoq on 2012-10-17
mplayer is only using ~6% here (smplayer)
xubuntu + compiz
vsync is enabled in nvidia and ccsm 
unredirected fullscreen windows is checked
nvidia version 310.14

no change in cpu usage for fullscreen and not fulllscreen also the same as when i have compiz off

if it happens it is probably a issue with the unity plugin

video was 720x404 @ 24fps

---

### Post by bird1500 on 2012-10-18
There are issues both with the Nvidia driver and Unity/compiz.
Nvidia fixed their stuff with the beta 310.14 driver, so now we're waiting for Unity/compiz to fix their [bugs]("https://bugs.launchpad.net/compiz/+bug/1049214").

A few noteworthy fixes in [Nvidia 310.14 beta]("http://www.nvidia.com/object/linux-display-amd64-310.14-driver.html"):
> 
- Fixed an issue which affected the performance of moving windows of VDPAU applications when run in some composite managers.
- Improved performance and responsiveness of windowed OpenGL applications running inside a Unity session.
- Implemented workarounds for two Adobe Flash bugs by applying libvdpau  commit ca9e637c61e80145f0625a590c91429db67d0a40 to the version of  libvdpau  shipped with the NVIDIA driver.


---

### Post by james_xxx on 2012-10-18
I just finished upgrading to 12.10 a few minutes ago, and vdpau either is not working, or it is not working very well.

This is in Kubuntu.

Nvidia + vdpau has been screwed up at the beginning of each release (for me) for the last several Kubuntu releases.

Xorg-edgers has been my salvation every time.

Installing from the xorg-edgers PPA right at this moment. I really hope that fixes things.

---

### Post by james_xxx on 2012-10-18
For what it's worth, I thought I'd report back that after installing all updates from the xorg-edgers PPA, vdpau now seems to be working fine.

YMMV.

Whether or not this is the solution in every case, I have no idea.

---

### Post by funicorn on 2012-10-18
Never use it, and don't count on it. If you really need hard accl, use windows or macOS. Some may argue they can make vdpau work, it can not change the fact multimedia drivers & facilities sucks in linux though. It's easier to accept one shortage than to try various ways to make one sucking thing work.

---

### Post by shreepads on 2012-10-18
Try after disabling Compiz... Or using Mate...

---

### Post by james_xxx on 2012-10-18
funicorn,

I use it often, and rely on it heavily, as I'm not a Windows (or Mac) user.

It generally works just fine.

Personally, I think Linux is awesome for multimedia. Rarely do any problems arise. My experience has apparently been very different from yours.

---

### Post by funicorn on 2012-10-18
I'm sure it is NOT.
To enable hardware acceleration is complicated. Vdpau is one thing,  having an excellent video player to make use of it is another. I have  nvidia card and have nvidia-current installed. Does it support vdpau?  yes. I have vlc and mplayer/mplayer2 installed. Do they support vdpau  playing ? Theoretically yes. But when I play movies with mplayer using  vdpau codec, it prints out all kinds of crap and quit. If I use vlc,  vdpau is working, but cpu usage goes as high as 30%. If I use mplayer2,  vdpau is working, cpu usage is low, however everything goes lagging such  as moving a window.  

It's not perfect anyway, why not give myself a  break and just use ffmpeg codecs.

> **james_xxx said:**
> funicorn,
It generally works just fine.


---


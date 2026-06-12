---
title: "VLC showing green screen during video playback; Audio works fine"
date: 2013-06-30
forum: System76 Support
---

### Post by ChiefWOTJ on 2013-06-30
I'm having an issue with VLC, Dragon Player, and Kamoso (KDE Webcam) where all are displaying green screens.  This seems to be a display issue rather than a function issue; Webcam will take pictures, and I can listen to movies in VLC and Dragon.  VLC snapshot also works and will return a screenshot of the movie.  I was having this same issue in Ubuntu as well.  I've checked to make sure all my codecs are up to date, and the System76 driver seems to be functioning normally. 

This is more of an annoyance for me, as I don't watch many movies on my system, but I'd like to get it sorted.  Has anyone else run into this issue, and if so, how did you fix it?  Thanks very much!

System: Gazelle Professional (gazp9); Kubuntu 13.04; Intel HD Graphics 4600; IPS matte display

**Update**

Disabling accelerated video output in VLC solved the problem, and video plays without an issue.  In Kaffeine, editing the xine-config file to use the OpenGL video driver solved the problem.  I still have not found a solution for Kamoso; It still shows a green screen but pictures come out fine...not sure what the deal is with that.  I'll update the post again if I can get a solution.

---

### Post by phxpx on 2013-08-12
Install Intel Graphics Drivers: [https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2)
This solved my green screen problem.

---

### Post by ChiefWOTJ on 2013-08-16
> **phxpx said:**
> Install Intel Graphics Drivers: [https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2)
This solved my green screen problem.

That worked great, thanks very much!

---

### Post by ppedrok2 on 2013-10-09
> **phxpx said:**
> Install Intel Graphics Drivers: [https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2)
This solved my green screen problem.

:KS  Thank you! It solved also my green screen problems with VLC, Dragon, Skype... On Acer Aspire V3-772G

---


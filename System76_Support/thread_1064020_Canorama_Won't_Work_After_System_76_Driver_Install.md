---
title: "Canorama Won't Work After System 76 Driver Install"
date: 2009-02-08
forum: System76 Support
---

### Post by cmnorton on 2009-02-08
I have installed my System76 drivers. I have also installed canorama, but when I start it, I get an error saying Could not connect to video device /dev/video0 Check connection. What should I do to debug this?

---

### Post by ctsdownloads on 2009-02-08
Same experience here as it is likely due to it being something up with the application itself based on what I can tell. Same problem on my other PC, using 32bit Ubuntu 8.10 as well as on 8.10 64bit on my System76 notebook.

To be honest though, I never bothered with it when [Flash 10]("http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html") with [Ustream]("http://www.ustream.tv"), [WebcamStudio]("http://webcamstudio.wiki.sourceforge.net/Screenshots"), aMSN all see the webcam just fine as a v4l2 device. ;)

---

### Post by thomasaaron on 2009-02-09
What computers are you guys using?

Camorama only works with the older computers because it only supports the V4L format. 

Cameras on the newer computers support the V4L2 format. Software for these cameras are Cheese, Ekiga Softphone, Skype.

---

### Post by cmnorton on 2009-02-09
You've nailed the problem. I've got a Gazelle Ultra running 8.10. I'll print these instructions. Thanks.

---

### Post by ctsdownloads on 2009-02-09
> **thomasaaron said:**
> What computers are you guys using?

Camorama only works with the older computers because it only supports the V4L format. 

Cameras on the newer computers support the V4L2 format. Software for these cameras are Cheese, Ekiga Softphone, Skype.

Yeah, that sounds right (RE: v4l vs v4l2). Honestly, I have not used Camorama in ages myself. No reason to as WebcamStudio does SOOOOOOO much more. Works on both 32 and 64 bit Ubuntu, too.

---


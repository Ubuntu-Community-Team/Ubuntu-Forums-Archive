---
title: "AMD Catalyst 9.12 Linux Driver Released (great update)"
date: 2009-12-18
forum: The Cafe
---

### Post by Pasdar on 2009-12-18
We now have OpenGL 3.2 support, and I have gained considerable performance.

Videocard: ATI 4570

Linux 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 3.2.9232
OpenGL shading language version string: 1.50
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4

glxgears:
28570 frames in 5.0 seconds = 5714 FPS

This is nearly **three times** more than what I get with the 9.10/11 drivers, previously with the 9.10 drivers (the ones you get from the repositories):
10074 frames in 5.0 seconds = 2014 FPS

furthermore, I dont have the delay anymore when minimizing/maximizing from taskbar. There is still a very slight delay when maximizing window size from window size.

Video tearing still exists.

---

### Post by Excedio on 2009-12-18
Double thread:
 
[http://ubuntuforums.org/showthread.php?t=1358333](http://ubuntuforums.org/showthread.php?t=1358333)

---

### Post by Pasdar on 2009-12-18
I have to add that the huge increase in performance could be due to the fact that I now have 64bit kubuntu installed as opposed to the 32bit that I previously had with 9.10 drivers.

---

### Post by Pasdar on 2009-12-19
ATI has released a 9.12 hotfix that adds new stuff. I'll try it out and let you guys know.

Hotfix download: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/hotfix/Catalyst_9.12_Hotfix_Linux_8.682.2RC1_Dec15.zip](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/hotfix/Catalyst_9.12_Hotfix_Linux_8.682.2RC1_Dec15.zip)

More info: [http://blogs.amd.com/play/2009/12/17/ati-catalyst%E2%84%A2-9-12-driver-%E2%80%93-what%E2%80%99s-new/](http://blogs.amd.com/play/2009/12/17/ati-catalyst%E2%84%A2-9-12-driver-%E2%80%93-what%E2%80%99s-new/)

---

### Post by Pasdar on 2009-12-19
Okay, dont install the hotfix... it adds a stupid watermark to the left lower corner of your screen with "AMD: Testing use only, Unsupported hardware"... very annoying... though still going to check what it brings before I take it away.

---


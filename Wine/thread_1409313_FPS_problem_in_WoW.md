---
title: "FPS problem in WoW"
date: 2010-02-17
forum: Wine
---

### Post by Sirsteveo on 2010-02-17
So I have recently switched to ubuntu 9.1 just the other day I run dual boot with windows 7. I am a huge fanatic of world of warcraft, many people have been telling me how cool ubuntu is and how it makes games run better because there is not as much going on in the background. I run a NVIDIA GeForce 9800M GTS graphic card with 1gb of memory and real time 3d graphics. For some reason when i play WoW through wine I only have about 10fps, when i am in windows 7 I have about 60-100 fps depending on where im at but im never under 60fps. I have gone to System > Administration > Hardware Drivers and click on the one that is recommended for my video card. What am I doing wrong or what setting need to be changed to get my frame rate up when playing WoW?

---

### Post by Sirsteveo on 2010-02-18
/bump?

---

### Post by Riddl on 2010-02-18
Did you add this 
> SET gxAPI "OpenGL"

to your config.wtf file? The file can be found in WoW-folder/WTF/.

---

### Post by Sirsteveo on 2010-02-18
I added that, i will see how things go.

---


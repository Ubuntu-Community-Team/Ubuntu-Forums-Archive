---
title: "Linux devices in wine"
date: 2011-05-11
forum: Wine
---

### Post by Disco732 on 2011-05-11
Alright, I have got a question.
Is it possible for a windows application running through wine to access a Linux device? (like a webcam, or a capture card)
Im running Ubuntu 10.04LTS
Im running Wine 1.3
The Windows application is virtual Dub.
I can see the video stream in cheese webcam booth.
Anyone got an answer?

---

### Post by Disco732 on 2011-05-13
Anyone?

---

### Post by OrbJinzo on 2011-05-15
Yes but with some caveats. the hardware might be supported by windows and linux but cause of the way wine interacts with the kernel some things may not like being used in wine. USB headsets are notorious for this. I dont know about web cams as to I have a face radio :P.

---

### Post by dacha on 2011-05-16
Wine does support video4linux devices. Whether it presents them to Windows applications through the interface they want to see is a different question.

Does VirtualDub not see it? What errors do you get?

---


---
title: "Cannot get my logitech c510 webcam to work properly"
date: 2013-05-07
forum: Ubuntu Studio
---

### Post by Miora on 2013-05-07
Somehow Ubuntustudio does see the webcam in Google Hangout. Here I have crappy buzzy sound from the one I try to talk with (I would like that solved too), There is video from both sides, the other side is not hearing me.
Cheese doesn see anything and just shows a greyed out screen.
Skype starts up. Initially nothing works. There is no camera detected and no sound both ways. Setting pulse audio solves the incoming sound but no solution can be found for anything to do with getting my webcam to work. The webcam just sits there being inactive.
I kinda forgot what version of ubuntustudio I installed but it said something about upgrading during last updates. Can find that handy "about" button anywhere... But the Xfce is 4.8
And my webcam is a logitech c510. Always worked great in previous Ubuntu installs. 

Getting the webcam to work would be my main liberation from having to dualboot to windoze constantly.
Please, deliver me from the shackles of the evil windoze! :(

---

### Post by jejeman on 2013-05-07
Plug in the camera.
Give
```
lsusb
```

---

### Post by Miora on 2013-05-07
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:1042 Western Digital Technologies, Inc. 
Bus 001 Device 003: ID 046d:081d Logitech, Inc. HD Webcam C510
Bus 005 Device 002: ID 0461:0010 Primax Electronics, Ltd 
Bus 006 Device 004: ID 1c4f:0003 SiGma Micro HID controller

---

### Post by jejeman on 2013-05-07
Bus 001 Device 003: ID 046d:081d Logitech, Inc. HD Webcam C510

this camera should be  supported by Ubuntu.

Try guvcview.

---

### Post by Miora on 2013-05-07
It does indeed work in guvcview. Tnx.
It still sucks in cheese and skype.
I've fiddled a bit with the settings in google hangout and am waiting for my friend to test it with.
I think from the social things I find the hangout the most important.
At least it's nice to know that the system at least sees my webcam

---


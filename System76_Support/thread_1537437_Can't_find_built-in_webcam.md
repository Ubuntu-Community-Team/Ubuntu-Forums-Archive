---
title: "Can't find built-in webcam"
date: 2010-07-23
forum: System76 Support
---

### Post by andyharrington on 2010-07-23
I have a new System76 lemu1, with its 64-bit Ubuntu 10.4, which is supposed to have a built-in webcam.  

When I started cheese I got "No device found".  

When I run gstreamer-properties, video tab, Default input shows plug-in: Video for Linux 2(V4I2).  When I click test I get 'Cannot identify /dev/video0' and there is no /dev/video0 shown in the file system.

Where from here?

Andy

---

### Post by msrinath80 on 2010-07-23
Once again. Hit Fn+F10 to activate the webcam first. Then start cheese.

---

### Post by andyharrington on 2010-07-24
I had read the previous threads on webcams and pressed fn-f10.  That is not it.

---

### Post by msrinath80 on 2010-07-24
Very well. Then the next thing to do is reinstall the system76 drivers. I've noticed that whenever the kernel is updated, one should go and reinstall those drivers. Then the webcam continues functioning till the next kernel update when I have to do this again.

---


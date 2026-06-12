---
title: "Virtual box works on main monitor but fails to load in secondary monitor"
date: 2008-05-30
forum: Virtualisation
---

### Post by checksignalcable on 2008-05-30
Hi, i love hardy heron 8.04. Ive just gone crazy with linux and compiz fusion and all the windows xp inside each other with innotek's VB. Well tonight i connected my nvidia 8600 to an external monitor so i could run xp full screen on a second monitor down the desk, no back on the original monitor linux is fine, and Virtual box runs great. Of course i cant just drag it over cause linux is treating my second monitor as if it were another pc just 2 linux enviros in one pc and two monitors. I have 2 sets of keyboards and mice. So i can further innovate my productivity of course. So my problem is that the kernel module is not installed for this "second virtual physical linux box". This is the outcome on the second monitor

```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```

So what i am thinking is that the second monitor as well as using the same programs and stuff, its using like its own modules and stuff important like that. So if someone could guide me in installing the kernel module and just that ill be happy. i already have the program set up and working. but i need the module to be installed. Thanks, and ill be glad to answer any questions that will help you help me :guitar:

---

### Post by checksignalcable on 2008-05-30
Hey, i figured it out on my own, its the smae way as installing kernels for a single monitor. LOL

---


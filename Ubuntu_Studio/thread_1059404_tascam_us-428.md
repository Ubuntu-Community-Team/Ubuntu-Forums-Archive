---
title: "tascam us-428"
date: 2009-02-03
forum: Ubuntu Studio
---

### Post by simtaalo on 2009-02-03
has anyone succesfully set one of these up?

i'm having some difficulty

it shows up in the output of lsusb

```
lsusb
Bus 005 Device 003: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1604:8000 Tascam US-428 Audio/Midi Controller (without fw)
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

but this page says something about having to update firmware???

[http://www.langerland.de/linux/usx2y/install.html](http://www.langerland.de/linux/usx2y/install.html)

> firmware upload
Each US-x2y device needs two firmware uploads. The first firmware upload will be done by fxload and changes the USB Product ID if it's successful. In case of US-122 the ID changes from 8006 to 8007, in case of US-224 from 8004 to 8005 and in case of US-428 from 8000 to 8001. By the way, the ID can be controlled with the lsusb command (or by cat /proc/bus/usb/devices).
After that the second firmware upload will be done by the usx2yloader. The usx2yloader is part of the alsa-tools and the firmware files are part of the alsa-firmware package. 

So both packages are needed. If this loading step was also successful, the green USB LED is shining now.

Normally both loaders will be started by hotplug events without additional configuration before, just install all the software packages you need and it will work.
mixer and controller

The US-122 doesn't need a software mixer; it has a hardware mixer instead. Everything is only controllable by those hardware knobs. Applications like alsamixer are useless and such software mixers will fail.

But the US-224 and US-428 have controllers inside. They will be driven by us428control and that application is normally starting by an hotplug event. Well, the name us428control doesn't fit for the US-224, but nevertheless it should work fine. 

not sure what to do

---

### Post by simtaalo on 2009-02-04
by using the advice here
[http://www.astro.caltech.edu/~mcs/tascam_us122/index.html](http://www.astro.caltech.edu/~mcs/tascam_us122/index.html)

but substituting the "SYSFS{idProduct}" number with the ones given here [http://www.langerland.de/linux/usx2y/install.html](http://www.langerland.de/linux/usx2y/install.html)

and then running

```
us428control
```

i managed to get it working. i can now hear things when i use a program with jack. i do have massive problems with the latency though, its reading 40+ seconds and i'm also getting lots of crackling when using mixxx.

i also need to workout how to get all the different inputs/outputs working and the controls.

---


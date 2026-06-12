---
title: "Incomplete driver install: silver GV"
date: 2007-05-19
forum: System76 Support
---

### Post by Nangineer on 2007-05-19
I decided to give my silver Gazelle value a fresh install of Kubuntu 7.04. (I was using Ubuntu 7.04 previously). I installed the driver but after rebooting I noticed I still didn't have the proper widescreen resolution. I installed in a terminal and got this:

```
make -C /lib/modules/2.6.20-15-generic/build M=/opt/system76/system76-driver/src/tifm
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /opt/system76/system76-driver/src/tifm/tifm_core.o
/opt/system76/system76-driver/src/tifm/tifm_core.c:12:26:
error: linux/config.h: No such file or directory

make[2]: *** [/opt/system76/system76-driver/src/tifm/tifm_core.o] Error 1
make[1]: *** [_module_/opt/system76/system76-driver/src/tifm] Error 2

make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 2
FATAL: Error inserting tifm_core (/lib/modules/2.6.20-15-generic/tifm/tifm_core.ko): Invalid module format
Killed
```

That's the end of the output (I don't know how to copy the whole thing because not all of the output shows up in Konsole).

Please help.

---

### Post by thomasaaron on 2007-05-21
You may need to open a terminal and run:
sudo dpkg-reconfigure xserver-xorg to obtain the proper resolution settings.

If you need to, you can call System 76 support and I'll walk you through it.

Best,
Tom

---

### Post by Nangineer on 2007-05-23
I got my screen resolution fixed by installing 915resolution. Actually, my intent of this post was to help shed some light on why the driver has been failing to completely install. The driver still removes the master volume control as I mentioned previously. (So I'm running w/o the driver for now.)

(Also, I'm running Ubuntu again instead of Kubuntu.)

---

### Post by MorphWVUtuba on 2007-05-23
I have the same machine, got the same FATAL error, and am sick and tired of the driver killing my sound after I install it.  I didn't have the X problem, it actually fixed my resolution.  But I was having weird problems up until I decided to redo the machine.  Couldn't burn CDs/DVDs, and such.  So I did a low level format (DBAN quick wipe--zeros written to drive), and did a clean install of 7.04 from the desktop disk (my laptop originally came with 6.10).  Note that my machine DID have sound after the clean Feisty install.  I edited fstab to map my network shares, then downloaded the s76 driver, ran it, and rebooted.

NO.  SOUND.  SINCE.

I've run a restore from the driver, uninstalled the driver, still no sound.  This issue has been occuring for me ever since v1.95 of the driver.  It's ridiculous, aggravating, and unacceptable.  It's gonna take a lot to convince me to put the driver repo back in my sources.list, let alone let it touch my machine again.](*,)

---

### Post by thomasaaron on 2007-05-24
What a pain in the rear!

Could you please file a bug report on this at:
[http://launchpad.net/system76](http://launchpad.net/system76)

We'll try to reproduce it.
I'm not exactly sure what your model number is, but I'm not hearing of any other sound
bugs from the older Gazelles. 
When I get your bug report, I'll try to reproduce it, and if it is the driver, we'll make the appropriate
modifications.

Best,
Tom

---

### Post by MorphWVUtuba on 2007-05-24
Submitted:

[https://bugs.launchpad.net/system76/+bug/116726](https://bugs.launchpad.net/system76/+bug/116726)

---


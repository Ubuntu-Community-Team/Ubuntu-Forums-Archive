---
title: "Alsa Source compile problem"
date: 2011-12-10
forum: Ubuntu Studio
---

### Post by w1ngnut on 2011-12-10
Hi,

I'm trying to recompile the ALSA driver to add support for my USB MIDI interface.
I'm using the ubuntu alsa-source package to compile from but each time I run make I get the following error:

/lib/modules/3.0.0-13-generic/build/include/linux/gameport.h: In function ‘gameport_register_driver’:
/lib/modules/3.0.0-13-generic/build/include/linux/gameport.h:152:54: error: ‘KBUILD_MODNAME’ undeclared (first use in this function)
/lib/modules/3.0.0-13-generic/build/include/linux/gameport.h:152:54: note: each undeclared identifier is reported only once for each function it appears in
In file included from hwdep.c:1:0:
/usr/src/modules/alsa-driver/include/adriver.h: At top level:
/usr/src/modules/alsa-driver/include/adriver.h:1359:5: error: conflicting types for ‘is_power_of_2’
/lib/modules/3.0.0-13-generic/build/include/linux/log2.h:52:6: note: previous definition of ‘is_power_of_2’ was here
hwdep.c:25:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.

Does anybody know how I get the drivers to compile and install?

Thanks

Trevor

---

### Post by jejeman on 2011-12-11
Which alsa version? Which ubuntu version? Which kernel version?

---

### Post by w1ngnut on 2011-12-11
Hi,

Sorry about that..... Late night after a loooong day!

ALSA version 1.0.24
Kernel Version 3.0.0.13
Ubuntu Studio version 11.10

Cheers


Trevor

---

### Post by w1ngnut on 2011-12-14
Hi,

I am really disappointed that nobody has been able to help me resolve my problem.
I'm a big fan of Linux, most of my servers and desktops run on it, so I'm well aware of the problems you can run into when compiling source code from third party's.

What really annoys me is that I downloaded the source from Ubuntu and it does not compile. The Ubuntu Studio install is a vanilla one, straight out of the box as Ubuntu intended, yet their source doesn't compile.

How hard can it be guys to ship the source you used when compiling the stuff in the first place?

Yet another promising distro let down by niggling problems and I just don't have the time or the inclination to sort it out.

A real shame, but Ubuntu Studio has let me down at the first hurdle. :(
If I can't get it to support the hardware I have, without spending days or weeks trying make it all work together, then it is absolutely no use to me whatsoever.

Sorry

Trevor

---

### Post by jejeman on 2011-12-14
How are you adding that support, for youre hardware?

---

### Post by w1ngnut on 2011-12-14
Hi,

By adding an entry into the /usb/quirks-table.h file to allow alsa to recognise the device.
I've done it before with other usb devices, so I know it works.

The errors are related to missing header files, namely smp_lock.h
I always try to use the source supplied for the distro I'm running, so as to avoid problems like this.

Cheers

Trevor

---

### Post by jejeman on 2011-12-14
Have you try to submit your patch to alsa developers, so it get included in future versions, so you don't have to compile alsa anymore, and maybe help some other poeple with same device?

---

### Post by trulan on 2011-12-14
Ah, the Big Kernel Lock (aka smp_lock.h) strikes again.  I'm not sure what a reference to that would be doing in Ubuntu's alsa source, that header was removed from the kernel in 2.6.39.  And for a while before that, it was non-functional.  You should be able to just delete the reference to smp_lock.h and it should compile.  And you should probably also file a bug in Ubuntu against alsa-source so it can get fixed properly.

---

### Post by w1ngnut on 2011-12-16
Hi,

Thanks for that guys.

I'll let Ubuntu know about the bug and submit the patch to the alsa developers.

Cheers

Trevor

---


---
title: "Compiling drivers for Microdia web cam"
date: 2008-12-24
forum: The Cafe
---

### Post by Silvernail on 2008-12-24
I am trying to install my microdia USB camera. It is reconize by lsusb. But I have no drivers for it.

I have downloaded the drivers and am trying to compile them. It been 15 years since I did any C programs so I'm lost when an error pops up. Heres the screen when I type make.```
dave@gadabout:/usr/src/microdia-2008.09$ sudo make
[sudo] password for dave: 
make -C /lib/modules/2.6.24-21-generic/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
make[2]: *** No rule to make target `arch/x86/kernel/asm-offsets.c', needed by `arch/x86/kernel/asm-offsets.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [driver] Error 2
dave@gadabout:/usr/src/microdia-2
```
What am I missing and where do I find it.
Any information you have would be appreciated.
Dave

---

### Post by igknighted on 2008-12-25
You should move this to a support forum... the cafe is really just for small talk.

That said, is there a readme with the source?  It should have all the dependencies listed, make sure they are all installed.

---


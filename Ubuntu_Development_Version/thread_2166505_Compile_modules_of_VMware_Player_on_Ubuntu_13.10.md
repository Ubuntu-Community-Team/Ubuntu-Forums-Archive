---
title: "Compile modules of VMware Player on Ubuntu 13.10?"
date: 2013-08-09
forum: Ubuntu Development Version
---

### Post by volkerbradley on 2013-08-09
I followed the installation instructions located at [http://linuxg.net/how-to-install-vmware-player-on-ubuntu-13-10-raring-ringtail/](http://linuxg.net/how-to-install-vmware-player-on-ubuntu-13-10-raring-ringtail/)
The player installed but the modules won't compile.  The error message is:
/usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.10.0-6-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.8
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make -C /lib/modules/3.10.0-6-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.10.0-6-generic'
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driver.o
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:40:28: fatal error: linux/smp_lock.h: No such file or directory
 #include <linux/smp_lock.h>
                            ^
compilation terminated.
make[2]: *** [/tmp/vmware-root/modules/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.10.0-6-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmmon-only' 

Can you point me in the right direction?

---


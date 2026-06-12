---
title: "Unable to install VMware HGFS Tools on Ubuntu"
date: 2009-07-31
forum: Virtualisation
---

### Post by neetals on 2009-07-31
Host OS:  Windows Vista 64x
VMware Workstaion Version: 6.0.4-93057
Guest OS: Ubuntu Server OS Version 9.04

Problem:

Trying to find a suitable vmhgfs module for your running kernel.

None of the pre-built vmhgfs modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmhgfs module for
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmhgfs module.

Building the vmhgfs module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config9/vmhgfs-only'
make -C /lib/modules/2.6.28-14-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-14-server'
  CC [M]  /tmp/vmware-config9/vmhgfs-only/backdoor.o
  CC [M]  /tmp/vmware-config9/vmhgfs-only/backdoorGcc64.o
  CC [M]  /tmp/vmware-config9/vmhgfs-only/bdhandler.o
/tmp/vmware-config9/vmhgfs-only/bdhandler.c:15:27: error: asm/semaphore.h: No such file or directory
make[2]: *** [/tmp/vmware-config9/vmhgfs-only/bdhandler.o] Error 1
make[1]: *** [_module_/tmp/vmware-config9/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-14-server'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-config9/vmhgfs-only'
Unable to build the vmhgfs module.

The filesystem driver (vmhgfs module) is used only for the shared folder 
feature. The rest of the software provided by VMware Tools is designed to work 
independently of this feature.
If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ]

I have tried all the available solution but still facing the same problem. I can access the shared folder.

Please anybody can help me.

Thanks in advance.

Regards

Neetal

---


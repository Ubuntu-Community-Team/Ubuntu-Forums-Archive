---
title: "Unable to install VMware Server 1.0.8 on Ubuntu 8.10"
date: 2008-12-03
forum: Virtualisation
---

### Post by paragkalra on 2008-12-03
Hello Folks,

I am getting following error while installing 
 VMware Server 1.0.8 on Ubuntu 8.10
> 
Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-7-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:71:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

root@station3:# 


Please help.

---

### Post by bodhi.zazen on 2008-12-04
Please see the Virtualization mega thread at the top of these forums, there is a link on how to install VMWare server in the links on the mega thread (there is a reason it is a sticky).

---

### Post by Dedoimedo on 2008-12-04
Hello,

A few quick tips:

1. To compile, you need the gcc, make, kernel source and kernel headers. You can install them by running sudo apt-get install build-essential.

2. You may require the so-called any-any patch; run it before you invoke the vmware-install.pl script.
[http://communities.vmware.com/thread/26693](http://communities.vmware.com/thread/26693)

Dedoimedo

---

### Post by bodhi.zazen on 2008-12-04
> **Dedoimedo said:**
> Hello,

A few quick tips:

1. To compile, you need the gcc, make, kernel source and kernel headers. You can install them by running sudo apt-get install build-essential.

2. You may require the so-called any-any patch; run it before you invoke the vmware-install.pl script.
[http://communities.vmware.com/thread/26693](http://communities.vmware.com/thread/26693)

Dedoimedo

Take care with the any-any patch, it is a life saver, and I have used it ...

But it is a bit of a hack and will disable (or at least it did the last time I looked) bridging your wireless network card. The any-any update has not need necessary with (the kernels in) 8.04 or 8.10.

Take a look at the how-tos for 8.04 and 8.10 listed in the mega thread first.

---


---
title: "Problems Installing VMware Workstation 6.04.93057"
date: 2008-11-01
forum: Virtualisation
---

### Post by Arkhar on 2008-11-01
Hey all, 

I've been trying to install this Version of VMWare Workstation for a while. I'm getting the same errors on 32 bit and 64 bit versions of Ubuntu. I'm currently on Ubuntu 8.10 64bit. I run the install and get up to the part after it runs the config where it tries to compile the vmmon module. I'm sure I have all the right requirements as far as packages go. I have tried the VMware update any-any install as well, and I get similar errors when trying to build the module.

Any help would be hugely appreciated as I am trying to Virtualize so I don't have to boot into Windows at all. I must break myself free of my Microsoft Slave Chains!

** This is the error I recieve:**


What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-7-generic/build/include] 

Extracting the sources of the vmmon module.
Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config6/vmmon-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config6/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config6/vmmon-only/./include/x86.h:24,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:84:
/tmp/vmware-config6/vmmon-only/./include/x86paging.h:61:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/pda.h:8,
                 from include/asm/current.h:19,
                 from include/asm/processor.h:15,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config6/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:115:
/tmp/vmware-config6/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config6/vmmon-only/linux/driver.c:197: error: unknown field &#8216;nopage&#8217; specified in initializer
/tmp/vmware-config6/vmmon-only/linux/driver.c:198: warning: initialization from incompatible pointer type
/tmp/vmware-config6/vmmon-only/linux/driver.c: In function &#8216;LinuxDriver_Ioctl&#8217;:
/tmp/vmware-config6/vmmon-only/linux/driver.c:1801: error: too many arguments to function &#8216;smp_call_function&#8217;
make[2]: *** [/tmp/vmware-config6/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config6/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config6/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

root@chomp64:/home/dan/Desktop/VM/VMware Workstation 6.0.4.93057 Linux x64/vmware-distrib#

---

### Post by Arkhar on 2008-11-01
Nevermind this one folks, I picked up a newer version with a bundle installer and got it workin!

---


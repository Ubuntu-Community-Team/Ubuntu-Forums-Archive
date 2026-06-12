---
title: "How to install VMWare Server 2.0 RC2 in Ubuntu 8.10 Intrepid Ibex"
date: 2008-09-04
forum: Virtualisation
---

### Post by sanderstuurwold on 2008-09-04
Hello,

I can't install VMWare Server 2.0 RC2 on Ubuntu 8.10 Intrepid Ibex. Also tried with any-to-any 117.Message is:

Can anyone tell me / help me?

Message:

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-2-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.27-2-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-2-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/./include/x86.h:24,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:85:
/tmp/vmware-config2/vmmon-only/./include/x86paging.h:61:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config2/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:116:
/tmp/vmware-config2/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1831: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-2-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.

root@Blackadder:/home/sander#

---

### Post by True on 2008-09-04
Same thing for both Workstation 6.5 beta and Player. It looks like a kernel 2.6.27 thing so probably something for VMWare to resolve (my guess).

---

### Post by lwb4007d on 2008-09-04
[size=4]so nice.....[/size]============================================================[img]http://www.qzone.la/img/userup/0808/2GU30U016.jpg[/img]our wow power leveling site: [world of warcraft powerleveling](http://www.toppowerlevel.net) buy [world of warcraft powerleveling](http://www.swow-power-leveling.com) [world of warcraft powerleveling](http://www.yoyo-power-leveling.com) [world of warcraft powerleveling](http://www.wow-powerleveler.com) cheap [world of warcraft powerleveling](http://www.wow-power-leveling1.com)

---

### Post by dark_phantom on 2008-09-04
If I remember correctly it had to do with the installed version of gcc in Intrepid.  I really didn't pursued it further, at least that what I remember.

---

### Post by sanderstuurwold on 2008-09-10
"Bug" is confirmed
[https://bugs.launchpad.net/ubuntu/+bug/263837](https://bugs.launchpad.net/ubuntu/+bug/263837)

---

### Post by True on 2008-09-24
I've just noticed that the latest beta of VMWare 6.5 Workstation now runs on Intrepid. Nice..! 

The latest 2.0 server is:

Version 2.0.0 | 116503 - 09/23/08

So the same release date as Workstation. You may well find this too runs on Intrepid now.

---

### Post by sirsteven on 2008-10-01
The .bundle files for Player works great on 8.10. Initially, I couldn't get it to open or run, but after changing the permissions to allow executing the file the install proceeded wonderfully.

---

### Post by jett on 2008-10-05
a similar thing happens in VMware 1.0.7

---


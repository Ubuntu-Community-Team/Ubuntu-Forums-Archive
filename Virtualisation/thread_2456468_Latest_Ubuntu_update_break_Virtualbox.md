---
title: "Latest Ubuntu update break Virtualbox"
date: 2021-01-12
forum: Virtualisation
---

### Post by davehk on 2021-01-12
Hi,

I am running the version of VB provided with Ubuntu. This morning's software update has broken VB. WHen I try to start VB, it pops up a box telling me  that vboxdrv is not correctly installed and to reinstall Virtualbox-DKMS and then run modprobe vboxdrv. This fails with error message that it could not find a file. I completely removed VB and then tried to re-install, which resulted in the following:

 ```
Errors were encountered while processing:
 virtualbox-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up virtualbox-dkms (6.1.10-dfsg-1~ubuntu1.20.04.1) ...
Removing old virtualbox-6.1.10 DKMS files...

------------------------------
Deleting module version: 6.1.10
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-6.1.10 DKMS files...
Building for 5.8.0-36-generic
Building initial module for 5.8.0-36-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/virtualbox-dkms.0.crash'
Error! Bad return status for module build on kernel: 5.8.0-36-generic (x86_64)
Consult /var/lib/dkms/virtualbox/6.1.10/build/make.log for more information.
dpkg: error processing package virtualbox-dkms (--configure):
 installed virtualbox-dkms package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 virtualbox-dkms

```

Here is the crash report ( I tried twice):

```
ProblemType: Package
DKMSBuildLog:
 DKMS make.log for virtualbox-6.1.10 for kernel 5.8.0-34-generic (x86_64)
 Thu  7 Jan 14:40:44 GMT 2021
 make: Entering directory '/usr/src/linux-headers-5.8.0-34-generic'
   CC [M]  /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/linux/SUPDrv-linux.o
   CC [M]  /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/SUPDrv.o
   CC [M]  /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/SUPDrvGip.o
   CC [M]  /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/SUPDrvSem.o
   CC [M]  /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/SUPDrvTracer.o
   CC [M]  /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/SUPLibAll.o
   CC [M]  /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/r0drv/alloc-r0drv.o
   CC [M]  /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/r0drv/initterm-r0drv.o
   CC [M]  /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/r0drv/memobj-r0drv.o
   CC [M]  /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/r0drv/mpnotification-r0drv.o
   CC [M]  /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/r0drv/powernotification-r0drv.o
   CC [M]  /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/r0drv/linux/assert-r0drv-linux.o
 In file included from ./include/asm-generic/percpu.h:7,
                  from ./arch/x86/include/asm/percpu.h:556,
                  from ./arch/x86/include/asm/preempt.h:6,
                  from ./include/linux/preempt.h:78,
                  from ./include/linux/spinlock.h:51,
                  from /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/linux/../SUPDrvInternal.h:79,
                  from /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/linux/SUPDrv-linux.c:32:
 /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/linux/SUPDrv-linux.c: In function ‘supdrvOSChangeCR4’:
 /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/linux/SUPDrv-linux.c:760:38: error: ‘cpu_tlbstate’ undeclared (first use in this function); did you mean ‘cpuhp_state’?
   760 |     RTCCUINTREG uOld = this_cpu_read(cpu_tlbstate.cr4);
       |                                      ^~~~~~~~~~~~
 ./include/linux/percpu-defs.h:318:9: note: in definition of macro ‘__pcpu_size_call_return’
   318 |  typeof(variable) pscr_ret__;     \
       |         ^~~~~~~~
 /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/linux/SUPDrv-linux.c:760:24: note: in expansion of macro ‘this_cpu_read’
   760 |     RTCCUINTREG uOld = this_cpu_read(cpu_tlbstate.cr4);
       |                        ^~~~~~~~~~~~~
 /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/linux/SUPDrv-linux.c:760:38: note: each undeclared identifier is reported only once for each function it appears in
   760 |     RTCCUINTREG uOld = this_cpu_read(cpu_tlbstate.cr4);
       |                                      ^~~~~~~~~~~~
 ./include/linux/percpu-defs.h:318:9: note: in definition of macro ‘__pcpu_size_call_return’
   318 |  typeof(variable) pscr_ret__;     \
       |         ^~~~~~~~
 /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/linux/SUPDrv-linux.c:760:24: note: in expansion of macro ‘this_cpu_read’
   760 |     RTCCUINTREG uOld = this_cpu_read(cpu_tlbstate.cr4);
       |                        ^~~~~~~~~~~~~
 make[2]: *** [scripts/Makefile.build:290: /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/linux/SUPDrv-linux.o] Error 1
 make[2]: *** Waiting for unfinished jobs....
 make[1]: *** [scripts/Makefile.build:519: /var/lib/dkms/virtualbox/6.1.10/build/vboxdrv] Error 2
 make: *** [Makefile:1780: /var/lib/dkms/virtualbox/6.1.10/build] Error 2
 make: Leaving directory '/usr/src/linux-headers-5.8.0-34-generic'
DKMSKernelVersion: 5.8.0-34-generic
Date: Thu Jan  7 14:40:46 2021
DuplicateSignature: dkms:virtualbox-dkms:6.1.10-dfsg-1~ubuntu1.20.04.1:/var/lib/dkms/virtualbox/6.1.10/build/vboxdrv/linux/SUPDrv-linux.c:760:38: error: ‘cpu_tlbstate’ undeclared (first use in this function); did you mean ‘cpuhp_state’?
Package: virtualbox-dkms 6.1.10-dfsg-1~ubuntu1.20.04.1
PackageVersion: 6.1.10-dfsg-1~ubuntu1.20.04.1
SourcePackage: virtualbox
Title: virtualbox-dkms 6.1.10-dfsg-1~ubuntu1.20.04.1: virtualbox kernel module failed to build
```


I am unsure how to proceed, any help would be gratefully received.
Thanks.

---

### Post by davehk on 2021-01-12
Seems this is a known issue with no immediate solutions. Great :(

There's an open bug in Launchpad, number 1891916.

Current status - won't fix - that is completely unacceptable. Quite a row on Launchpad. Is it time to abandon Ubuntu for another distro?

---

### Post by ajgreeny on 2021-01-12
Two hopefully helpfull suggestions.

1. Boot to the 5.4 series kernel from grub which you will, I think have had at installation, if you're using 20.04; the 5.8.0-36 kernel you're using at present has known problems of may sorts so I suspect it will soon be replaced.

2. Use the version of VBox direct from the VBox website. Instructions there tell you how to enable their own repos  which currently have version 6.1.16. Follow the info in the section on Debian based distros. Remove all virtualbox packages you currently have installed before enabling those VNox repos, then install virtualbox-6.1 package.

---

### Post by davehk on 2021-01-12
Thanks. (1) was my first thought, but I don't have the 5.4 series kernel on my machine only the 2 most recent 5.8 versions, which is the default grub behaviour. I should probably change grub to keep more that 2 versions, but I can't remember how and I can't find the relevant article on the web.

Your (2) was my next option - so I've already done that and am now running again. I recall having to do the same thing a few years ago when an Ubuntu update broke Ubuntu's version of VB - so this is at least the second time they've done this sort of thing.

---


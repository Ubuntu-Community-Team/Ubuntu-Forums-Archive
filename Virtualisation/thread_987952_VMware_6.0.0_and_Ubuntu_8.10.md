---
title: "VMware 6.0.0 and Ubuntu 8.10"
date: 2008-11-20
forum: Virtualisation
---

### Post by geohei on 2008-11-20
Hi.

I'd like to install Ubuntu 8.10 server and desktop on a VMware 6.0.0 workstation.

Is this possible, or do I have to upgrade VMware?

Thanks

---

### Post by bodhi.zazen on 2008-11-20
Yes it is possible. Are you having problems ?

---

### Post by tony.research on 2008-12-10
It doesn't work on my pc, when I try to install it happens that:

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system

and then 
What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-9-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.27-9-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:48:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:170: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config0/vmmon-only/./include/x86.h:23,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/x86cpuid.h:381:1: warning: "BIT_MASK" redefined
In file included from include/linux/kernel.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:11:
include/linux/bitops.h:7:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/./include/x86.h:24,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/x86paging.h:61:1: warning: "PTE_PFN_MASK" redefined
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
In file included from /tmp/vmware-config0/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config0/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config0/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config0/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c:149: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:150: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1715: error: ‘struct mm_struct’ has no member named ‘dumpable’
/tmp/vmware-config0/vmmon-only/linux/driver.c:1726: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


if someone can help...
thanx
tony.research

---

### Post by bodhi.zazen on 2008-12-10
Follow the how-to for VMWare server (apply the patch).

If you still have problems with the vmmon module, follow teh patch on the vmmon

Links to both are in the mega thread ;)

---

### Post by TalioGladius on 2008-12-11
Find the latest any-any patch and run it at this point.


However, I'd recommend getting yourself a copy of VMWare Workstation 6.5.  The install procedure was infinitely simplified.  Plus you get cool new features like unity to play with.

---

### Post by billcondie on 2008-12-11
I really just need the Player,

But how do I install a BUNDLED or an RPM?

---

### Post by jake1017 on 2008-12-11
I am using 6.5 and recommend it.

Bundles are easy to install.

Open a terminal and change the directory to where the .bundle is then type

```
sudo sh (filename).bundle
```

---

### Post by billcondie on 2008-12-11
Thank you. I'm getting there!

But back to the drawing board.

I got it installed in wubi. Niow I've moved onto a HD install of Ubuntu 8.10

The file is on the desktop. Here's where I'm at:

bill@bill-desktop:~$ sudo sh VMware-Workstation-6.5.1-126130.i386.bundle
sh: Can't open VMware-Workstation-6.5.1-126130.i386.bundle

---

### Post by Willem V. on 2008-12-24
I've been there.

I found a post that handles this issue.

Fact is that you'll first have to set to the desktop

cd /home/yourusername/Desktop

---


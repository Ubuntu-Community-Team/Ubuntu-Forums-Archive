---
title: "VMware 6.5 D3D9 support?"
date: 2008-12-24
forum: Virtualisation
---

### Post by Bensky on 2008-12-24
So I have a game that uses GameGuard that won't work with Wine or anything. However, I just read something posted on a forum that states that D3D9 games now work with VMWare!

[http://www.elitepvpers.de/forum/cabal-guides-templates/139341-guide-multi-client-vmware-setup-any-game-pic-s-included.html](http://www.elitepvpers.de/forum/cabal-guides-templates/139341-guide-multi-client-vmware-setup-any-game-pic-s-included.html)

Has anyone had any luck getting games to work using this method? If so, how is the performance and what type of PC do you need to run games smoothly?

My PC:
1.7 ghz Pentium 4 (Single Core)
1 GB ram
ATI Radeon 9600 XT (128 MB)

---

### Post by Bensky on 2008-12-26
Bump. Does anyone know anything about this? :(

---

### Post by brinza on 2008-12-29
yes it is support cabal , but i tryid it from xp with vm on it.However i didn't managed to install VM on my ubuntu game idition :(.Here is my error



Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.27-9-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
CC [M] /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vmware.h:25,
from /tmp/vmware-config0/vmmon-only/linux/driver.c:48:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:170: error: conflicting types for &#8216;uintptr_t&#8217;
include/linux/types.h:40: error: previous declaration of &#8216;uintptr_t&#8217; was here
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
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:60: error: conflicting types for &#8216;poll_initwait&#8217;
include/linux/poll.h:65: error: previous declaration of &#8216;poll_initwait&#8217; was here
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13,
from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c:149: error: unknown field &#8216;nopage&#8217; specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:150: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function &#8216;LinuxDriver_Ioctl&#8217;:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1715: error: &#8216;struct mm_struct&#8217; has no member named &#8216;dumpable&#8217;
/tmp/vmware-config0/vmmon-only/linux/driver.c:1726: error: too many arguments to function &#8216;smp_call_function&#8217;
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

---

### Post by Bensky on 2008-12-31
Not sure what your problem is there - could it be because of the newer kernel? :\

Has anyone actually tested this successfully?

---


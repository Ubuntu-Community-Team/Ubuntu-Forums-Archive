---
title: "Problem compiling vmmon"
date: 2010-02-17
forum: Virtualisation
---

### Post by keith_emerson on 2010-02-17
Hey guys!

I was wondering if you could help me with this problem I'm having...

I've installed Vmware, and in the first run, it tries to compile the kernel tools, but it fails with the first one (vmmon). I ran the program through console so as to see where the problem was... It seems to be more complex than I thought.

Here's the log

> 
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make -C /lib/modules/2.6.31-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driver.o
In file included from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:31:
/tmp/vmware-root/modules/vmmon-only/./include/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vmware.h:38,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:99:
/tmp/vmware-root/modules/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vcpuset.h:103,
                 from /tmp/vmware-root/modules/vmmon-only/./include/modulecall.h:37,
                 from /tmp/vmware-root/modules/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:101:
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:460:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:551:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:640:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:729:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:816:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:903:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:986:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:1069:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:1313:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:1796:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86_64.h:39,
                 from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:103:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:103:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86_64.h:56:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:119:
/tmp/vmware-root/modules/vmmon-only/./common/hostif.h:53:7: warning: "WINNT_DDK" is not defined
/tmp/vmware-root/modules/vmmon-only/linux/driver.c: In function ‘LinuxDriverSyncCallOnEachCPU’:
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1423: error: too many arguments to function ‘smp_call_function’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘fsuid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘egid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘fsgid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:2007: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-root/modules/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
There's a conflict with the declaration of the same type in two different .h. How can I solve this without corrupting the installation? Can I delete one of those declarations? Which one?

Thanks a lot!

---

### Post by santonoff on 2010-03-08
Did you ever get a solution to your vmmon compile problem?  I'm trying to install vmware server on Ubuntu 9.1 and I'm getting the same error.  I can't find the error.  The only thing I can find is that in the file "compat_wait.h", the #define in the 2nd line is suspicious, but that file is created by vmware-config.pl.

---

### Post by keith_emerson on 2010-03-08
Never got a solution... Problem is still hanging

---

### Post by dcstar on 2010-03-08
> **keith_emerson said:**
> Never got a solution... Problem is still hanging

And you have the kernel patch installed?

---

### Post by keith_emerson on 2010-03-08
No..Same problem. It doesn't compile. It's strange cause it seems to be a code error (???)

---

### Post by dcstar on 2010-03-08
> **keith_emerson said:**
> No..Same problem. It doesn't compile. It's strange cause it seems to be a code error (???)

Do you have the appropriate kernel patch installed that is **required** for compiling VMware with current kernels - yes or no?

---

### Post by keith_emerson on 2010-03-09
No. I didn't patch it. Can I do it with vmware already installed?

---

### Post by dcstar on 2010-03-09
> **keith_emerson said:**
> No. I didn't patch it. Can I do it with vmware already installed?

Please read the threads at the top of this forum.

---

### Post by kelly7898 on 2010-03-11
Thank you for the post. 
Hi guys, Im a newbie. Nice to join this forum.

---


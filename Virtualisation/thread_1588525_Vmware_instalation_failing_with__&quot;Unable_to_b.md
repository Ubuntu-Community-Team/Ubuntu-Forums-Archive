---
title: "Vmware instalation failing with  &quot;Unable to build the vmmon module.&quot;"
date: 2010-10-05
forum: Virtualisation
---

### Post by nubber7 on 2010-10-05
Hello all can any one help me in installing vmware on Ubuntu?

I have the following config: 

$ uname -a
Linux ubuntu 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux
System 
using an intel quad core 64 bit processor. 
Using "VMware-server-2.0.2-203138.x86_64.tar.gz"

Always getting the following error. Any suggestions is appreciated. Tried different patches etc by googling but still not working. 


Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config6/vmmon-only'
make -C /lib/modules/2.6.32-24-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /tmp/vmware-config6/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config6/vmmon-only/linux/driver.c:31:
/tmp/vmware-config6/vmmon-only/./include/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config6/vmmon-only/./include/vmware.h:38,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:99:
/tmp/vmware-config6/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config6/vmmon-only/./common/vmx86.h:32,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:101:
/tmp/vmware-config6/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/processor.h:21,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config6/vmmon-only/./include/compat_module.h:27,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:26:
/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/msr-index.h:228:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config6/vmmon-only/./include/vcpuset.h:103,
                 from /tmp/vmware-config6/vmmon-only/./include/modulecall.h:37,
                 from /tmp/vmware-config6/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:101:
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:460:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:551:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:640:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:729:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:816:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:903:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:986:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:1069:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:1313:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:1796:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config6/vmmon-only/./include/vm_asm_x86_64.h:39,
                 from /tmp/vmware-config6/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:103:
/tmp/vmware-config6/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config6/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:103:
/tmp/vmware-config6/vmmon-only/./include/vm_asm_x86_64.h:56:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config6/vmmon-only/linux/driver.c:119:
/tmp/vmware-config6/vmmon-only/./common/hostif.h:53:7: warning: "WINNT_DDK" is not defined
/tmp/vmware-config6/vmmon-only/linux/driver.c: In function ‘LinuxDriverSyncCallOnEachCPU’:
/tmp/vmware-config6/vmmon-only/linux/driver.c:1423: error: too many arguments to function ‘smp_call_function’
/tmp/vmware-config6/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config6/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-config6/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config6/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘fsuid’
/tmp/vmware-config6/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config6/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘egid’
/tmp/vmware-config6/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config6/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘fsgid’
/tmp/vmware-config6/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config6/vmmon-only/linux/driver.c:2007: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config6/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config6/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config6/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.

---

### Post by nubber7 on 2010-10-05
Any one able to help? I am actively trying to resolve this issue.

---

### Post by 67GTA on 2010-10-05
[https://sites.google.com/site/lightrush/random-1/vmwareplayeronubuntulucidormaverickrunningkernel2635](https://sites.google.com/site/lightrush/random-1/vmwareplayeronubuntulucidormaverickrunningkernel2635)

---

### Post by nubber7 on 2010-10-05
["https://sites.google.com/site/lightr...ningkernel2635]("https://sites.google.com/site/lightrush/random-1/vmwareplayeronubuntulucidormaverickrunningkernel2635")"

The above link is showing information fro Vmware player. I am trying to install vmware server edition.

---

### Post by 67GTA on 2010-10-06
Sorry, I posted the wrong link. This is the one I meant to post. Was looking through Firefox history and grabbed it too quickly. [http://hmontoliu.blogspot.com/2010/04/installing-vmware-server-202-in-ubuntu.html](http://hmontoliu.blogspot.com/2010/04/installing-vmware-server-202-in-ubuntu.html) What exactly have you done so far? Just make sure the previous tweaks aren't interfering. I used this method last week.

---


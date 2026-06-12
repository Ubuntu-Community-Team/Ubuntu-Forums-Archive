---
title: "vmware server broke with 11.04 upgrade"
date: 2011-04-29
forum: Virtualisation
---

### Post by cpgeek on 2011-04-29
I had a working vmware server 2.0.2 setup on 10.10 (stock, up to date) and i just upgraded the machine to 11.04 which installed a new kernel (of course), but now vmware is broken.

when i run vmware-config, it tells me that it can't build the vmmon module for the current kernel despite having the appropriate headers installed and linked to the right place.

Does anybody have any ideas?

Thanks,

Cpgeek

P.S. FYI I'm using vmware-server as this is an aged box without vm-x (pentium 4 2.8ghz, 4gb ram.   i just use it as a web server testbed)

---

### Post by tinny on 2011-04-30
How did you get vmware server working on 10.10 in the first instance? I had to use this script [here]("http://radu.cotescu.com/how-to-install-vmware-server-ubuntu-fedora-opensuse/")

The script is meant to support kernel 2.6.35. I wonder if anyone has tried it with kernel 2.6.38 (Ubuntu 11.04)?

Im about to try it out now, will post back the results.

---

### Post by tinny on 2011-04-30
> **tinny said:**
> Im about to try it out now, will post back the results.

Nope doesn't work any more. :(

> 
name@mythubuntu:~/Desktop/raducotescu-vmware-server-linux-2.6.3x-kernel-71f8b66$ sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh 
You have VMware Server archive: 
	VMware-server-2.0.2-203138.i386.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-2.6.38-8-generic package...
You do have the build-essential package...
You do have the patch package...
Extracting the contents of VMware-server-2.0.2-203138.i386.tar.gz
Found .tar file for vmmon module
Found .tar file for vsock module
Found .tar file for vmci module
Found .tar file for vmnet module
Extracting .tar files in order to apply the patch...
Untarring /home/name/Desktop/raducotescu-vmware-server-linux-2.6.3x-kernel-71f8b66/vmware-server-distrib/lib/modules/source/vmmon.tar
Untarring /home/name/Desktop/raducotescu-vmware-server-linux-2.6.3x-kernel-71f8b66/vmware-server-distrib/lib/modules/source/vsock.tar
Untarring /home/name/Desktop/raducotescu-vmware-server-linux-2.6.3x-kernel-71f8b66/vmware-server-distrib/lib/modules/source/vmci.tar
Untarring /home/name/Desktop/raducotescu-vmware-server-linux-2.6.3x-kernel-71f8b66/vmware-server-distrib/lib/modules/source/vmnet.tar
Testing patch...
Creating some simlinks for the newer kernels...
ln: creating symbolic link `/usr/src/linux-headers-2.6.38-8-generic/include/linux/autoconf.h': File exists
ln: creating symbolic link `/usr/src/linux-headers-2.6.38-8-generic/include/linux/utsrelease.h': File exists
Applying patch...
Preparing new tar file for vmmon module
Preparing new tar file for vsock module
Preparing new tar file for vmci module
Preparing new tar file for vmnet module
Checking that the compiling will succeed...
Trying to compile vmmon module to see if it works
Performing make in /home/name/Desktop/raducotescu-vmware-server-linux-2.6.3x-kernel-71f8b66/vmware-server-distrib/lib/modules/source/vmmon-only
Using 2.6.x kernel build system.
In file included from /home/name/Desktop/raducotescu-vmware-server-linux-2.6.3x-kernel-71f8b66/vmware-server-distrib/lib/modules/source/vmmon-only/./common/vmx86.h:32:0,
                 from /home/name/Desktop/raducotescu-vmware-server-linux-2.6.3x-kernel-71f8b66/vmware-server-distrib/lib/modules/source/vmmon-only/linux/driver.h:29,
                 from /home/name/Desktop/raducotescu-vmware-server-linux-2.6.3x-kernel-71f8b66/vmware-server-distrib/lib/modules/source/vmmon-only/linux/driver.c:101:
/home/name/Desktop/raducotescu-vmware-server-linux-2.6.3x-kernel-71f8b66/vmware-server-distrib/lib/modules/source/vmmon-only/./include/x86msr.h:164:0: warning: "MSR_THERM2_CTL" redefined
/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/msr-index.h:244:0: note: this is the location of the previous definition
/home/name/Desktop/raducotescu-vmware-server-linux-2.6.3x-kernel-71f8b66/vmware-server-distrib/lib/modules/source/vmmon-only/linux/driver.c: In function ‘init_module’:
/home/name/Desktop/raducotescu-vmware-server-linux-2.6.3x-kernel-71f8b66/vmware-server-distrib/lib/modules/source/vmmon-only/linux/driver.c:426:15: error: ‘struct file_operations’ has no member named ‘ioctl’
make[2]: *** [/home/name/Desktop/raducotescu-vmware-server-linux-2.6.3x-kernel-71f8b66/vmware-server-distrib/lib/modules/source/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/home/name/Desktop/raducotescu-vmware-server-linux-2.6.3x-kernel-71f8b66/vmware-server-distrib/lib/modules/source/vmmon-only] Error 2
make: *** [vmmon.ko] Error 2
There is a problem compiling the vmmon module after it was patched. :(



---

### Post by majorpay on 2011-04-30
I have the exact same issue.  Just upgraded to 11.04 and it broke vmware server.  A quick Google search lands me here.  This is going to be a deal breaker for 11.04 if I can't get this installed, unless someone can suggest another VM server that can automatically start Windows hosts EASILY.  

Honestly, I have been sick to death with VMWare's implementation of server on Linux.  It is a miracle to get it up and running, and once you do, it's nothing short of a miracle to keep it that way.  I would go ESXI, but that doesn't even install (complains about the ethernet adapter - I've tried two including a gigabit pci card, and there has been no luck).

---

### Post by gabriele.puppis on 2011-05-01
Same problem here, and I need it urgently :(

---

### Post by alfredo.marchini on 2011-05-02
Hi,
I've got same problem here, but searching for in google I found a strange post in vmware site:

[http://communities.vmware.com/thread/304233](http://communities.vmware.com/thread/304233)

I think this patch makes something good, but is not sufficient...


If I compile without patch this is the output:

```

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config6/vmmon-only'
make -C /lib/modules/2.6.38-8-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
  CC [M]  /tmp/vmware-config6/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config6/vmmon-only/linux/driver.c:31:0:
/tmp/vmware-config6/vmmon-only/./include/compat_wait.h:78:13: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:72:13: note: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config6/vmmon-only/./include/vmware.h:38:0,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:99:
/tmp/vmware-config6/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config6/vmmon-only/./common/vmx86.h:32:0,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:101:
/tmp/vmware-config6/vmmon-only/./include/x86msr.h:164:0: warning: "MSR_THERM2_CTL" redefined
/usr/src/linux-headers-2.6.38-8-generic-pae/arch/x86/include/asm/msr-index.h:244:0: note: this is the location of the previous definition
In file included from /tmp/vmware-config6/vmmon-only/./include/vcpuset.h:103:0,
                 from /tmp/vmware-config6/vmmon-only/./include/modulecall.h:37,
                 from /tmp/vmware-config6/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:101:
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h: In function ‘Atomic_And’:
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h: In function ‘Atomic_Or’:
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h: In function ‘Atomic_Xor’:
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h: In function ‘Atomic_Add’:
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h: In function ‘Atomic_Sub’:
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h: In function ‘Atomic_Inc’:
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h: In function ‘Atomic_Dec’:
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h: At top level:
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config6/vmmon-only/./include/vm_basic_asm.h:46:0,
                 from /tmp/vmware-config6/vmmon-only/./include/rateconv.h:45,
                 from /tmp/vmware-config6/vmmon-only/./include/modulecall.h:40,
                 from /tmp/vmware-config6/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:101:
/tmp/vmware-config6/vmmon-only/./include/vm_basic_asm_x86.h:62:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_basic_asm_x86.h:177:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_basic_asm_x86.h:346:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_basic_asm_x86.h:453:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config6/vmmon-only/./include/vm_asm.h:43:0,
                 from /tmp/vmware-config6/vmmon-only/linux/driver.c:103:
/tmp/vmware-config6/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config6/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config6/vmmon-only/linux/driver.c:119:0:
/tmp/vmware-config6/vmmon-only/./common/hostif.h:53:7: warning: "WINNT_DDK" is not defined
/tmp/vmware-config6/vmmon-only/linux/driver.c: In function ‘init_module’:
/tmp/vmware-config6/vmmon-only/linux/driver.c:426:15: error: ‘struct file_operations’ has no member named ‘ioctl’
/tmp/vmware-config6/vmmon-only/linux/driver.c: In function ‘LinuxDriverSyncCallOnEachCPU’:
/tmp/vmware-config6/vmmon-only/linux/driver.c:1423:4: error: too many arguments to function ‘smp_call_function’
include/linux/smp.h:73:5: note: declared here
/tmp/vmware-config6/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config6/vmmon-only/linux/driver.c:1987:18: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-config6/vmmon-only/linux/driver.c:1987:35: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config6/vmmon-only/linux/driver.c:1988:11: error: ‘struct task_struct’ has no member named ‘fsuid’
/tmp/vmware-config6/vmmon-only/linux/driver.c:1988:29: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config6/vmmon-only/linux/driver.c:1989:18: error: ‘struct task_struct’ has no member named ‘egid’
/tmp/vmware-config6/vmmon-only/linux/driver.c:1989:35: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config6/vmmon-only/linux/driver.c:1990:11: error: ‘struct task_struct’ has no member named ‘fsgid’
/tmp/vmware-config6/vmmon-only/linux/driver.c:1990:29: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config6/vmmon-only/linux/driver.c:2007:7: error: too many arguments to function ‘smp_call_function’
include/linux/smp.h:73:5: note: declared here
make[2]: *** [/tmp/vmware-config6/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config6/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config6/vmmon-only'
Unable to build the vmmon module.

```

If I apply the patch:

```

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config7/vmmon-only'
make -C /lib/modules/2.6.38-8-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
  CC [M]  /tmp/vmware-config7/vmmon-only/linux/driver.o

In file included from /tmp/vmware-config7/vmmon-only/./common/vmx86.h:32:0,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.c:101:
/tmp/vmware-config7/vmmon-only/./include/x86msr.h:164:0: warning: "MSR_THERM2_CTL" redefined
/usr/src/linux-headers-2.6.38-8-generic-pae/arch/x86/include/asm/msr-index.h:244:0: note: this is the location of the previous definition
In file included from /tmp/vmware-config7/vmmon-only/./common/vmx86.h:32:0,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.c:101:
/tmp/vmware-config7/vmmon-only/./include/x86msr.h:164:0: warning: "MSR_THERM2_CTL" redefined
/usr/src/linux-headers-2.6.38-8-generic-pae/arch/x86/include/asm/msr-index.h:244:0: note: this is the location of the previous definition
  CC [M]  /tmp/vmware-config7/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config7/vmmon-only/linux/hostif.o
/tmp/vmware-config7/vmmon-only/linux/hostif.c:36:25: fatal error: compat_cred.h: No such file or directory
compilation terminated.
make[2]: *** [/tmp/vmware-config7/vmmon-only/linux/hostif.o] Error 1
make[1]: *** [_module_/tmp/vmware-config7/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config7/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.

```

The error is "compat_cred.h" but I don't found it anywhere...
Have you got any other idea?
Bye

---

### Post by alfredo.marchini on 2011-05-02
If I remove in 

vmmon-only/linux/hostif.c 

#include "compat_cred.h"

I get this error:

```


Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config8/vmmon-only'
make -C /lib/modules/2.6.38-8-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
  CC [M]  /tmp/vmware-config8/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config8/vmmon-only/./common/vmx86.h:32:0,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.c:101:
/tmp/vmware-config8/vmmon-only/./include/x86msr.h:164:0: warning: "MSR_THERM2_CTL" redefined
/usr/src/linux-headers-2.6.38-8-generic-pae/arch/x86/include/asm/msr-index.h:244:0: note: this is the location of the previous definition
In file included from /tmp/vmware-config8/vmmon-only/./common/vmx86.h:32:0,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.c:101:
/tmp/vmware-config8/vmmon-only/./include/x86msr.h:164:0: warning: "MSR_THERM2_CTL" redefined
/usr/src/linux-headers-2.6.38-8-generic-pae/arch/x86/include/asm/msr-index.h:244:0: note: this is the location of the previous definition
  CC [M]  /tmp/vmware-config8/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config8/vmmon-only/linux/hostif.o
In file included from /tmp/vmware-config8/vmmon-only/./common/vmx86.h:32:0,
                 from /tmp/vmware-config8/vmmon-only/./common/hostif.h:32,
                 from /tmp/vmware-config8/vmmon-only/linux/hostif.c:73:
/tmp/vmware-config8/vmmon-only/./include/x86msr.h:164:0: warning: "MSR_THERM2_CTL" redefined
/usr/src/linux-headers-2.6.38-8-generic-pae/arch/x86/include/asm/msr-index.h:244:0: note: this is the location of the previous definition
/tmp/vmware-config8/vmmon-only/linux/hostif.c: In function ‘HostIFFastClockThread’:
/tmp/vmware-config8/vmmon-only/linux/hostif.c:3463:4: error: implicit declaration of function ‘compat_cap_raise’
/tmp/vmware-config8/vmmon-only/linux/hostif.c: In function ‘HostIF_SetFastClockRate’:
/tmp/vmware-config8/vmmon-only/linux/hostif.c:3588:10: error: implicit declaration of function ‘compat_current_fsuid’
/tmp/vmware-config8/vmmon-only/linux/hostif.c:3595:10: error: implicit declaration of function ‘compat_cap_raised’
/tmp/vmware-config8/vmmon-only/linux/hostif.c:3599:13: error: implicit declaration of function ‘compat_cap_lower’
make[2]: *** [/tmp/vmware-config8/vmmon-only/linux/hostif.o] Error 1
make[1]: *** [_module_/tmp/vmware-config8/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config8/vmmon-only'
Unable to build the vmmon module.

```

---

### Post by alfredo.marchini on 2011-05-02
Ok... nothing good...
the patch I linked remap cap_* functions to compat_cap_*
and add the inclusion for compat_cred.h that should contain this functions... 
but it doesn't exist in vmmon headers... 
no way...

---

### Post by majorpay on 2011-05-03
I guess the moral of the story here is: if it's not broke, don't upgrade (or at least check the forums for early adopter horror stories).
 
I will either be rolling back or going with ESXI when my new network card comes in.

---

### Post by alfredo.marchini on 2011-05-03
READ THIS POST:

[http://ubuntuforums.org/showthread.php?p=10761345](http://ubuntuforums.org/showthread.php?p=10761345)

Anyway I finished to try, just today, virtualbox 4.0.
It works very well, but I think it's like vmware workstation.
I found also the procedure to convert vmware vmdk to virtualbox disk.
I used Vmware server as a workstation, so virtualbox is perfect for me. 
For production environments I also use esxi 4.1, vmware server is not secure, every time you need install a new kernel you risk to broke vmware, it's dangerous for production systems.

VMWare server is at end of life, I suggest you to use esxi 4.1, but you need compatible hardware.
You can covert vmdk vmware server disks to esxi disks.

---

### Post by majorpay on 2011-05-03
> **alfredo.marchini said:**
> READ THIS POST:

[http://ubuntuforums.org/showthread.php?p=10761345](http://ubuntuforums.org/showthread.php?p=10761345)

Anyway I finished to try, just today, virtualbox 4.0.
It works very well, but I think it's like vmware workstation.
I found also the procedure to convert vmware vmdk to virtualbox disk.
I used Vmware server as a workstation, so virtualbox is perfect for me. 
For production environments I also use esxi 4.1, vmware server is not secure, every time you need install a new kernel you risk to broke vmware, it's dangerous for production systems.

VMWare server is at end of life, I suggest you to use esxi 4.1, but you need compatible hardware.
You can covert vmdk vmware server disks to esxi disks.
You're my hero  :p...  

I am definitely going to ESXI assuming the network card fixes the install issue.  The problem with ESXI has less to do with implementing the system and more to do with how ridiculously picky about hardware it is.

They shouldn't EOL VMWare Server until ESXI can operate on the machines VMS does (they probably will anyway though).

---

### Post by tinny on 2011-05-04
Vmware server end of life, Really? 

Where can I read more about this? Link?

Cheers

---

### Post by alfredo.marchini on 2011-05-05
Is not official,
but if you see when was released the last version and follow all the patch history (always released bye the community, never by vmware team for the new kernels)...

If you search for "vmware server end of life" you will find many posts... nothing official, but a fact is that vmware doesn't release an upgrade since 2009-10-26...

I'm tired to be warned everytime I install a new kernel...
For my laptop I moved to virtualbox, works well and for server-based virtualization solution I buy a compatible server (HP-DELL-IBM-ECC.) and use ESXi that is a very good solution.

---

### Post by cmavr8 on 2011-05-06
Did you guys find any way to get over the problem?

I can't even uninstall vmware workstation! Or install a new version.

Also tried older kernel but it doesn't work...

More [here]("http://communities.vmware.com/message/1747650#1747650")

---

### Post by majorpay on 2011-05-06
> **cmavr8 said:**
> Did you guys find any way to get over the problem?

I can't even uninstall vmware workstation! Or install a new version.

Also tried older kernel but it doesn't work...

More [here]("http://communities.vmware.com/message/1747650#1747650")

Honestly, I bought an Intel Pro 1000/gt off of Ebay to get ESXI working and ditched VMWare Server entirely.  If you have any interest in ESXI, it will typically run on just about anything, but 99% of the errors you find are related to the network card at the initial install.

If you absolutely need a GUI front end running on your server, obviously this is not an option, but if not, it runs better and will give you less headaches in the long run.

---

### Post by cmavr8 on 2011-05-06
Thanks but I'm not running ESXI or server but Workstation. The problem is the same (with player, too) so I replied here...

Could I run ESXi on my PC and use it as a workstation (even without GUI)?

---

### Post by majorpay on 2011-05-06
> **cmavr8 said:**
> Thanks but I'm not running ESXI or server but Workstation. The problem is the same (with player, too) so I replied here...

Could I run ESXi on my PC and use it as a workstation (even without GUI)?

Unfortunately ESXI has no visible front end aside from some minor configuration options, so I don't think that's what you'd be looking for.

Had you tried this solution: [http://ubuntuforums.org/showthread.php?p=10761345](http://ubuntuforums.org/showthread.php?p=10761345) ?

---

### Post by majorpay on 2011-05-06
Specifically referring to this post: 
> **sirusdv said:**
> Saw a bunch of people like myself have been  having issues getting vmware-server to compile / install after upgrading  to natty so I created a new patch set for for the raducotescu script.

Follow the following guide 

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

But before executing the vmware-server-2.0.x-kernel-2.6.3x-install.sh  script extract the attached file and overwrite the one that comes with  the package. 

You should now be able to build all the modules and complete installation.

---

### Post by majorpay on 2011-05-06
And if you want workstation, I'd try this:

[http://www.nalinmakar.com/2011/04/27/vmware-workstation-7-1-4-ubuntu-11-04-and-unity/](http://www.nalinmakar.com/2011/04/27/vmware-workstation-7-1-4-ubuntu-11-04-and-unity/)

---

### Post by cmavr8 on 2011-05-13
> **majorpay said:**
> And if you want workstation, I'd try this:

[http://www.nalinmakar.com/2011/04/27/vmware-workstation-7-1-4-ubuntu-11-04-and-unity/](http://www.nalinmakar.com/2011/04/27/vmware-workstation-7-1-4-ubuntu-11-04-and-unity/)
Thanks, tried it, doesn't work for me...

I'll try installing vmware server, using this "guide": [http://ubuntuforums.org/showpost.php?p=10809061&postcount=12](http://ubuntuforums.org/showpost.php?p=10809061&postcount=12)

---

### Post by cmavr8 on 2011-05-13
Didn't work but [THIS]("http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=38") worked! Manually uninstalled worstation...

Thanks for the effort!

---


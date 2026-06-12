---
title: "VMWare Server and Intrepid...Sure I ain't the only one"
date: 2008-10-31
forum: Virtualisation
---

### Post by Radioman991 on 2008-10-31
Figure the forums are gonna be busy this week, but there is the issue

Fresh install of Intrepid, and installing VMWare Server.  When I go to configure VMWare, I get the following

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/x86.h:24,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:53:
/tmp/vmware-config0/vmmon-only/./include/x86paging.h:61:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:16:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:84:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c:171: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:172: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:175: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:176: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘__LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1781: error: too many arguments to function ‘smp_call_function’
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

I am missing something somewhere.  Any input appreciated

---

### Post by dcstar on 2008-10-31
> **Radioman991 said:**
> Figure the forums are gonna be busy this week, but there is the issue

**Fresh install of Intrepid**, and installing VMWare Server.  When I go to configure VMWare, I get the following
.........
I am missing something somewhere.  Any input appreciated

Install the **build-essential** package.

---

### Post by sgrover on 2008-11-02
The problem is not a lack of build-essential.  I am running into this same issue, and have build-essential installed.  

If it helps, my box is an upgrade of 64bit Hardy.

---

### Post by ExampleDotCom on 2008-11-03
Oops I got my threads confused and thought this was about workstation.  Anyway if having this same problem on workstation the reason is using 6.0.5 instead of 6.5.0, see:

[http://communities.vmware.com/message/1080146]("http://communities.vmware.com/message/1080146")

...but it looks like Server isn't patched yet.

---

### Post by bodhi.zazen on 2008-11-03
See this sticky : [http://ubuntuforums.org/showthread.php?t=966070](http://ubuntuforums.org/showthread.php?t=966070)

---


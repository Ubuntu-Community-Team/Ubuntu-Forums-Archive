---
title: "VMware Workstation 6.0.4, Build 93057 not compiling on 2.6.24-21-generic"
date: 2008-08-25
forum: Virtualisation
---

### Post by luh3417 on 2008-08-25
Hi has anyone come across a fix for this or do I need to wait for new bug fixed kernel and run prior kernel in meantime?





one of the pre-built vmmon modules for VMware Player is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-21-generic/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.24-21-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:83:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:170: error: conflicting types for &#8216;uintptr_t&#8217;
include/linux/types.h:40: error: previous declaration of &#8216;uintptr_t&#8217; was here
In file included from /tmp/vmware-config1/vmmon-only/./include/x86.h:23,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:84:
/tmp/vmware-config1/vmmon-only/./include/x86cpuid.h:383:1: warning: "BIT_MASK" redefined
In file included from include/linux/kernel.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:11:
include/linux/bitops.h:7:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config1/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config1/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:84:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config1/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:84:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: error: conflicting types for &#8216;poll_initwait&#8217;
include/linux/poll.h:65: error: previous declaration of &#8216;poll_initwait&#8217; was here
/tmp/vmware-config1/vmmon-only/linux/driver.c:198: warning: initialisation from incompatible pointer type
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by jpkotta on 2008-08-26
You need the vmware-any-any patchset.  

[https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation)

---

### Post by luh3417 on 2008-08-26
I ran the *any-any117d but still could not get Vmware to compile. I tried the Vmnet options in the script choosing Yes to keep old settings and I also tried No and reset settings but in both cases it would not compile the module. Here is the error out:

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /tmp/vmware-config7/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config7/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config7/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config7/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config7/vmnet-only/bridge.o
/tmp/vmware-config7/vmnet-only/bridge.c: In function ‘VNetBridgeDevCompatible’:
/tmp/vmware-config7/vmnet-only/bridge.c:278: error: implicit declaration of function ‘dev_net’
/tmp/vmware-config7/vmnet-only/bridge.c: In function ‘VNetBridgeUp’:
/tmp/vmware-config7/vmnet-only/bridge.c:903: warning: passing argument 1 of ‘__dev_get_by_name’ makes pointer from integer without a cast
/tmp/vmware-config7/vmnet-only/bridge.c:941: warning: passing argument 1 of ‘sk_alloc’ makes pointer from integer without a cast
make[2]: *** [/tmp/vmware-config7/vmnet-only/bridge.o] Error 1
make[1]: *** [_module_/tmp/vmware-config7/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config7/vmnet-only'
Unable to build the vmnet module.

---


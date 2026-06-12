---
title: "vmware-workstation on ubuntu 10.04"
date: 2010-05-11
forum: Virtualisation
---

### Post by nsahoo on 2010-05-11
Hi,

I have been trying to start vmware-workstation on ubuntu 10.04 without success. It fails to compile the modules. When I tried to compile this was the error:

```

/usr/bin/vmware-modconfig --console --install-all
Stopping VMware services:
   VMware USB Arbitrator                                               done
   VM communication interface socket family                            done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make -C /lib/modules/2.6.32-22-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driver.o
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:42,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:100:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86_64.h:50:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:42,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:100:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86_64.h:50:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/hostif.o
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:42,
                 from /tmp/vmware-root/modules/vmmon-only/linux/hostif.c:67:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86_64.h:50:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/linux/hostif.c: In function ‘HostIFReadUptimeWork’:
/tmp/vmware-root/modules/vmmon-only/linux/hostif.c:1944: warning: ‘newUpBase’ may be used uninitialized in this function
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/iommu.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/hashFunc.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/task.o
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:42,
                 from /tmp/vmware-root/modules/vmmon-only/common/task.c:50:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86_64.h:50:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/vmx86.o
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:42,
                 from /tmp/vmware-root/modules/vmmon-only/common/vmx86.c:43:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86_64.h:50:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-root/modules/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-root/modules/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-root/modules/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-root/modules/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make -C $PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
Built vmmon module
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmnet-only'
make -C /lib/modules/2.6.32-22-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /tmp/vmware-root/modules/vmnet-only/driver.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/hub.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/userif.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/netif.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/filter.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/smac_compat.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/smac.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/vnetEvent.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/vnetUserListener.o
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c: In function ‘VNetUserListenerEventHandler’:
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: (Each undeclared identifier is reported only once
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: for each function it appears in.)
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c: In function ‘VNetUserListenerRead’:
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: implicit declaration of function ‘signal_pending’
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: implicit declaration of function ‘schedule’
make[2]: *** [/tmp/vmware-root/modules/vmnet-only/vnetUserListener.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmnet-only'
Unable to install vmnet

```

Any help is greatly appreciated.

---

### Post by TJet1.8 on 2010-05-12
Make sure your build environment is up-to-date first "before" re-compiling your VMware modules:

sudo apt-get install gcc build-essential linux-headers-$(uname -r)

Try it and report back.

GL :)

---

### Post by Ryangarve on 2010-05-17
I was having the exact same problem and that worked perfect.  

Thanks for the help!

---

### Post by nitish.shivananda on 2010-05-26
Hi,

Tried this but the same error persists.

Regards,
Nitish

---

### Post by H0lyGanGs7eR on 2010-05-26
Hello, I tried this, but nothing! Please help !
```
niki@niki-desktop:/tmp$ sudo vmware
Logging to /tmp/vmware-root/setup-14836.log
filename:       /lib/modules/2.6.32-22-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-22-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-22-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-22-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
filename:       /lib/modules/2.6.32-22-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-22-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-22-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-22-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
filename:       /lib/modules/2.6.32-22-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-22-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-22-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-22-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
filename:       /lib/modules/2.6.32-22-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-22-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-22-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-22-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
filename:       /lib/modules/2.6.32-22-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-22-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-22-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-22-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
filename:       /lib/modules/2.6.32-22-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-22-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-22-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-22-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
Stopping VMware services:
   VMware USB Arbitrator                                               done
   VM communication interface socket family                            done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make -C /lib/modules/2.6.32-22-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driver.o
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:42,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:100:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86_64.h:50:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:42,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:100:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86_64.h:50:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/hostif.o
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:42,
                 from /tmp/vmware-root/modules/vmmon-only/linux/hostif.c:67:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86_64.h:50:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/linux/hostif.c: In function ‘HostIFReadUptimeWork’:
/tmp/vmware-root/modules/vmmon-only/linux/hostif.c:1944: warning: ‘newUpBase’ may be used uninitialized in this function
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/iommu.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/hashFunc.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/task.o
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:42,
                 from /tmp/vmware-root/modules/vmmon-only/common/task.c:50:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86_64.h:50:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/vmx86.o
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:42,
                 from /tmp/vmware-root/modules/vmmon-only/common/vmx86.c:43:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86_64.h:50:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-root/modules/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-root/modules/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-root/modules/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-root/modules/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make -C $PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
make: *** /tmp/vmware-root/modules/vmnet-only: No such file or directory.  Stop.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmblock-only'
make -C /lib/modules/2.6.32-22-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/block.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/control.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/dbllnklst.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/dentry.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/file.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/filesystem.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/inode.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/module.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/stubs.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/super.o
  LD [M]  /tmp/vmware-root/modules/vmblock-only/vmblock.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-root/modules/vmblock-only/vmblock.mod.o
  LD [M]  /tmp/vmware-root/modules/vmblock-only/vmblock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make -C $PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/vmware-root/modules/vmblock-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/vmware-root/modules/vmblock-only'
cp -f vmblock.ko ./../vmblock.o
make: Leaving directory `/tmp/vmware-root/modules/vmblock-only'
make: *** /tmp/vmware-root/modules/vmci-only: No such file or directory.  Stop.
make: *** /tmp/vmware-root/modules/vmci-only: No such file or directory.  Stop.
Starting VMware services:
   VMware USB Arbitrator                                               done
   Virtual machine monitor                                             done
   Virtual machine communication interface                            failed
   VM communication interface socket family                           failed
   Blocking file system                                                done
   Virtual ethernet                                                   failed
```

---

### Post by fjgaude on 2010-05-26
from what little I know you need WS 7.0 to have it work with Ubuntu 10.04. What version of WS are you using?

---

### Post by H0lyGanGs7eR on 2010-05-27
VMware Workstation 7.0.0-203739 x86_64 Linux . Is this Ok?

---

### Post by wulf-dieter on 2010-05-29
> **H0lyGanGs7eR said:**
> VMware Workstation 7.0.0-203739 x86_64 Linux . Is this Ok?


My remedy for a similar prblem was to go to the VMware download page and download the latest version of the workstation - 7.0.1 (when you have ann account there that you set up when you purchased your original you will have to log in) save it into root next to your 7.00 version and double click on it. This will update your VMware workstation application.
Having done that, just for safety's sake, reboot your machine. Start your virtual machine. This did the trick on my system.
Perhaps it helps you as well

---

### Post by TimsterC on 2010-08-04
NOW SOLVED, thanks to this post [http://ubuntuforums.org/showthread.php?t=1481780](http://ubuntuforums.org/showthread.php?t=1481780)

I'm getting the same error too. But I have previously had VMware workstation 6.5 running on Ubuntu 10.04

```
tim@tclark-w500:~$ vmware
Logging to /tmp/vmware-tim/setup-7931.log
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     B4678ECC7558C5068BA8CF8
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     9B4563B3C180049AA056D00
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmci.ko
supported:      external
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     EAD34527E13C65FD3615E44
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vsock.ko
supported:      external
license:        GPL v2
version:        1.0.0.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     DE98118B82B18CFC2548E80
depends:        vmci
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     B4678ECC7558C5068BA8CF8
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     9B4563B3C180049AA056D00
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmci.ko
supported:      external
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     EAD34527E13C65FD3615E44
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vsock.ko
supported:      external
license:        GPL v2
version:        1.0.0.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     DE98118B82B18CFC2548E80
depends:        vmci
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     B4678ECC7558C5068BA8CF8
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     9B4563B3C180049AA056D00
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmci.ko
supported:      external
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     EAD34527E13C65FD3615E44
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vsock.ko
supported:      external
license:        GPL v2
version:        1.0.0.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     DE98118B82B18CFC2548E80
depends:        vmci
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     B4678ECC7558C5068BA8CF8
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     9B4563B3C180049AA056D00
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmci.ko
supported:      external
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     EAD34527E13C65FD3615E44
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vsock.ko
supported:      external
license:        GPL v2
version:        1.0.0.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     DE98118B82B18CFC2548E80
depends:        vmci
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     B4678ECC7558C5068BA8CF8
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     9B4563B3C180049AA056D00
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmci.ko
supported:      external
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     EAD34527E13C65FD3615E44
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vsock.ko
supported:      external
license:        GPL v2
version:        1.0.0.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     DE98118B82B18CFC2548E80
depends:        vmci
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
Logging to /tmp/vmware-root/setup-8502.logfilename:       /lib/modules/2.6.32-24-generic-pae/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     B4678ECC7558C5068BA8CF8
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     9B4563B3C180049AA056D00
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmci.ko
supported:      external
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     EAD34527E13C65FD3615E44
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vsock.ko
supported:      external
license:        GPL v2
version:        1.0.0.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     DE98118B82B18CFC2548E80
depends:        vmci
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     B4678ECC7558C5068BA8CF8
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     9B4563B3C180049AA056D00
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmci.ko
supported:      external
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     EAD34527E13C65FD3615E44
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vsock.ko
supported:      external
license:        GPL v2
version:        1.0.0.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     DE98118B82B18CFC2548E80
depends:        vmci
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     B4678ECC7558C5068BA8CF8
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     9B4563B3C180049AA056D00
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmci.ko
supported:      external
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     EAD34527E13C65FD3615E44
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vsock.ko
supported:      external
license:        GPL v2
version:        1.0.0.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     DE98118B82B18CFC2548E80
depends:        vmci
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     B4678ECC7558C5068BA8CF8
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     9B4563B3C180049AA056D00
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmci.ko
supported:      external
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     EAD34527E13C65FD3615E44
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vsock.ko
supported:      external
license:        GPL v2
version:        1.0.0.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     DE98118B82B18CFC2548E80
depends:        vmci
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     B4678ECC7558C5068BA8CF8
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     9B4563B3C180049AA056D00
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmci.ko
supported:      external
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     EAD34527E13C65FD3615E44
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vsock.ko
supported:      external
license:        GPL v2
version:        1.0.0.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     DE98118B82B18CFC2548E80
depends:        vmci
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     B4678ECC7558C5068BA8CF8
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     9B4563B3C180049AA056D00
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmci.ko
supported:      external
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     EAD34527E13C65FD3615E44
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vsock.ko
supported:      external
license:        GPL v2
version:        1.0.0.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     DE98118B82B18CFC2548E80
depends:        vmci
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
Stopping VMware services:
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmnet-only'
make -C /lib/modules/2.6.32-24-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic-pae'
  CC [M]  /tmp/vmware-root/modules/vmnet-only/driver.o
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:27,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:24,
                 from /tmp/vmware-root/modules/vmnet-only/driver.c:54:
/tmp/vmware-root/modules/vmnet-only/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:24,
                 from /tmp/vmware-root/modules/vmnet-only/driver.c:54:
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vm_basic_asm.h:46,
                 from /tmp/vmware-root/modules/vmnet-only/vm_oui.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:25,
                 from /tmp/vmware-root/modules/vmnet-only/driver.c:54:
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:62:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:177:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:346:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:453:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-root/modules/vmnet-only/hub.o
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:27,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:24,
                 from /tmp/vmware-root/modules/vmnet-only/hub.c:47:
/tmp/vmware-root/modules/vmnet-only/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:24,
                 from /tmp/vmware-root/modules/vmnet-only/hub.c:47:
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vm_basic_asm.h:46,
                 from /tmp/vmware-root/modules/vmnet-only/vm_oui.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:25,
                 from /tmp/vmware-root/modules/vmnet-only/hub.c:47:
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:62:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:177:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:346:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:453:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-root/modules/vmnet-only/userif.o
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:27,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:24,
                 from /tmp/vmware-root/modules/vmnet-only/userif.c:50:
/tmp/vmware-root/modules/vmnet-only/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:24,
                 from /tmp/vmware-root/modules/vmnet-only/userif.c:50:
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vm_basic_asm.h:46,
                 from /tmp/vmware-root/modules/vmnet-only/vm_oui.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:25,
                 from /tmp/vmware-root/modules/vmnet-only/userif.c:50:
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:62:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:177:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:346:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:453:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-root/modules/vmnet-only/netif.o
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:27,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:24,
                 from /tmp/vmware-root/modules/vmnet-only/netif.c:46:
/tmp/vmware-root/modules/vmnet-only/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:24,
                 from /tmp/vmware-root/modules/vmnet-only/netif.c:46:
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vm_basic_asm.h:46,
                 from /tmp/vmware-root/modules/vmnet-only/vm_oui.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:25,
                 from /tmp/vmware-root/modules/vmnet-only/netif.c:46:
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:62:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:177:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:346:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:453:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-root/modules/vmnet-only/bridge.o
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:27,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:24,
                 from /tmp/vmware-root/modules/vmnet-only/bridge.c:55:
/tmp/vmware-root/modules/vmnet-only/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:24,
                 from /tmp/vmware-root/modules/vmnet-only/bridge.c:55:
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vm_basic_asm.h:46,
                 from /tmp/vmware-root/modules/vmnet-only/vm_oui.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:25,
                 from /tmp/vmware-root/modules/vmnet-only/bridge.c:55:
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:62:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:177:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:346:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:453:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/bridge.c:854:7: warning: "WIRELESS_EXT" is not defined
/tmp/vmware-root/modules/vmnet-only/bridge.c:856:7: warning: "WIRELESS_EXT" is not defined
  CC [M]  /tmp/vmware-root/modules/vmnet-only/filter.o
In file included from /tmp/vmware-root/modules/vmnet-only/vnetFilter.h:36,
                 from /tmp/vmware-root/modules/vmnet-only/filter.c:37:
/tmp/vmware-root/modules/vmnet-only/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:24,
                 from /tmp/vmware-root/modules/vmnet-only/filter.c:39:
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vm_basic_asm.h:46,
                 from /tmp/vmware-root/modules/vmnet-only/vm_oui.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:25,
                 from /tmp/vmware-root/modules/vmnet-only/filter.c:39:
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:62:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:177:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:346:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:453:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-root/modules/vmnet-only/procfs.o
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:27,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:24,
                 from /tmp/vmware-root/modules/vmnet-only/procfs.c:47:
/tmp/vmware-root/modules/vmnet-only/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:24,
                 from /tmp/vmware-root/modules/vmnet-only/procfs.c:47:
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vm_basic_asm.h:46,
                 from /tmp/vmware-root/modules/vmnet-only/vm_oui.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:25,
                 from /tmp/vmware-root/modules/vmnet-only/procfs.c:47:
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:62:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:177:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:346:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:453:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-root/modules/vmnet-only/smac_compat.o
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:27,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:24,
                 from /tmp/vmware-root/modules/vmnet-only/smac_compat.c:57:
/tmp/vmware-root/modules/vmnet-only/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:24,
                 from /tmp/vmware-root/modules/vmnet-only/smac_compat.c:57:
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vm_basic_asm.h:46,
                 from /tmp/vmware-root/modules/vmnet-only/vm_oui.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:25,
                 from /tmp/vmware-root/modules/vmnet-only/smac_compat.c:57:
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:62:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:177:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:346:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:453:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-root/modules/vmnet-only/smac.o
In file included from /tmp/vmware-root/modules/vmnet-only/smac_compat.h:30,
                 from /tmp/vmware-root/modules/vmnet-only/smac.c:56:
/tmp/vmware-root/modules/vmnet-only/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
  CC [M]  /tmp/vmware-root/modules/vmnet-only/vnetEvent.o
In file included from /tmp/vmware-root/modules/vmnet-only/vnetKernel.h:33,
                 from /tmp/vmware-root/modules/vmnet-only/vnetEvent.c:56:
/tmp/vmware-root/modules/vmnet-only/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetEvent.h:27,
                 from /tmp/vmware-root/modules/vmnet-only/vnetEvent.c:57:
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-root/modules/vmnet-only/vnetUserListener.o
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:27,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:24,
                 from /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:36:
/tmp/vmware-root/modules/vmnet-only/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vnet.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:24,
                 from /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:36:
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmnet-only/vm_basic_asm.h:46,
                 from /tmp/vmware-root/modules/vmnet-only/vm_oui.h:28,
                 from /tmp/vmware-root/modules/vmnet-only/vnetInt.h:25,
                 from /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:36:
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:62:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:177:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:346:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vm_basic_asm_x86.h:453:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c: In function &#8216;VNetUserListenerEventHandler&#8217;:
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: &#8216;TASK_INTERRUPTIBLE&#8217; undeclared (first use in this function)
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: (Each undeclared identifier is reported only once
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: for each function it appears in.)
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c: In function &#8216;VNetUserListenerRead&#8217;:
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: &#8216;TASK_INTERRUPTIBLE&#8217; undeclared (first use in this function)
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: implicit declaration of function &#8216;signal_pending&#8217;
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: implicit declaration of function &#8216;schedule&#8217;
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic-pae'
make[2]: *** [/tmp/vmware-root/modules/vmnet-only/vnetUserListener.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmnet-only] Error 2
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmnet-only'
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual machine communication interface                             done
   Blocking file system                                                done
   Virtual ethernet                                                   failed
filename:       /lib/modules/2.6.32-24-generic-pae/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     B4678ECC7558C5068BA8CF8
depends:        
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 
```

---


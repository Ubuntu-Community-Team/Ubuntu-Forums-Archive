---
title: "virtual ethernet failed vmware kubuntu"
date: 2012-07-18
forum: Virtualisation
---

### Post by psv8 on 2012-07-18
[I]Hi, guys.
 I have installed VMware workstation VMware-Workstation-Full-8.0.4-744019.x86_64.bundle
I ve got Kubuntu Linux 3.2.0-26-generic, KDE SC Version 4.8.4

Can not start it, i am getting:
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual machine communication interface                             done
   VM communication interface socket family                            done
   Blocking file system                                                done
   Virtual ethernet                                                   _**failed**_
   VMware Authentication Daemon                                        done

Any ideas?  **Please help!** I am struggling with that for few nights now.

Thank you.[/I]

FULL LOG:

 sudo vmware
Logging to /tmp/vmware-root/modconfig-18916.log

(vmware-modconfig:18916): Gtk-WARNING **: Unable to locate theme engine in module_path: "oxygen-gtk",
filename:       /lib/modules/3.2.0-26-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     0845FE74CACDC7B6DF8502C
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/3.2.0-26-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     953CE20A40BBA61A0C35692
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/3.2.0-26-generic/misc/vmci.ko
supported:      external
license:        GPL v2
version:        9.1.18.0
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     17017D6780BB2857D35A2EB
alias:          pci:v000015ADd00000740sv*sd*bc*sc*i*
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
parm:           disable_host:Disable driver host personality - (default=0) (bool)
parm:           disable_guest:Disable driver guest personality - (default=0) (bool)
parm:           disable_msi:Disable MSI use in driver - (default=0) (bool)
parm:           disable_msix:Disable MSI-X use in driver - (default=0) (bool)
filename:       /lib/modules/3.2.0-26-generic/misc/vsock.ko
supported:      external
alias:          vmware_vsock
license:        GPL v2
version:        9.1.1.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     9878089A7E91D82DD11D683
depends:        vmci
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
filename:       /lib/modules/3.2.0-26-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     0845FE74CACDC7B6DF8502C
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/3.2.0-26-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     953CE20A40BBA61A0C35692
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/3.2.0-26-generic/misc/vmci.ko
supported:      external
license:        GPL v2
version:        9.1.18.0
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     17017D6780BB2857D35A2EB
alias:          pci:v000015ADd00000740sv*sd*bc*sc*i*
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
parm:           disable_host:Disable driver host personality - (default=0) (bool)
parm:           disable_guest:Disable driver guest personality - (default=0) (bool)
parm:           disable_msi:Disable MSI use in driver - (default=0) (bool)
parm:           disable_msix:Disable MSI-X use in driver - (default=0) (bool)
filename:       /lib/modules/3.2.0-26-generic/misc/vsock.ko
supported:      external
alias:          vmware_vsock
license:        GPL v2
version:        9.1.1.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     9878089A7E91D82DD11D683
depends:        vmci
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
filename:       /lib/modules/3.2.0-26-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     0845FE74CACDC7B6DF8502C
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/3.2.0-26-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     953CE20A40BBA61A0C35692
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/3.2.0-26-generic/misc/vmci.ko
supported:      external
license:        GPL v2
version:        9.1.18.0
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     17017D6780BB2857D35A2EB
alias:          pci:v000015ADd00000740sv*sd*bc*sc*i*
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
parm:           disable_host:Disable driver host personality - (default=0) (bool)
parm:           disable_guest:Disable driver guest personality - (default=0) (bool)
parm:           disable_msi:Disable MSI use in driver - (default=0) (bool)
parm:           disable_msix:Disable MSI-X use in driver - (default=0) (bool)
filename:       /lib/modules/3.2.0-26-generic/misc/vsock.ko
supported:      external
alias:          vmware_vsock
license:        GPL v2
version:        9.1.1.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     9878089A7E91D82DD11D683
depends:        vmci
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
filename:       /lib/modules/3.2.0-26-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     0845FE74CACDC7B6DF8502C
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/3.2.0-26-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     953CE20A40BBA61A0C35692
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/3.2.0-26-generic/misc/vmci.ko
supported:      external
license:        GPL v2
version:        9.1.18.0
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     17017D6780BB2857D35A2EB
alias:          pci:v000015ADd00000740sv*sd*bc*sc*i*
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
parm:           disable_host:Disable driver host personality - (default=0) (bool)
parm:           disable_guest:Disable driver guest personality - (default=0) (bool)
parm:           disable_msi:Disable MSI use in driver - (default=0) (bool)
parm:           disable_msix:Disable MSI-X use in driver - (default=0) (bool)
filename:       /lib/modules/3.2.0-26-generic/misc/vsock.ko
supported:      external
alias:          vmware_vsock
license:        GPL v2
version:        9.1.1.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     9878089A7E91D82DD11D683
depends:        vmci
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
filename:       /lib/modules/3.2.0-26-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     0845FE74CACDC7B6DF8502C
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/3.2.0-26-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     953CE20A40BBA61A0C35692
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/3.2.0-26-generic/misc/vmci.ko
supported:      external
license:        GPL v2
version:        9.1.18.0
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     17017D6780BB2857D35A2EB
alias:          pci:v000015ADd00000740sv*sd*bc*sc*i*
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
parm:           disable_host:Disable driver host personality - (default=0) (bool)
parm:           disable_guest:Disable driver guest personality - (default=0) (bool)
parm:           disable_msi:Disable MSI use in driver - (default=0) (bool)
parm:           disable_msix:Disable MSI-X use in driver - (default=0) (bool)
filename:       /lib/modules/3.2.0-26-generic/misc/vsock.ko
supported:      external
alias:          vmware_vsock
license:        GPL v2
version:        9.1.1.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     9878089A7E91D82DD11D683
depends:        vmci
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
filename:       /lib/modules/3.2.0-26-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     0845FE74CACDC7B6DF8502C
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/3.2.0-26-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     953CE20A40BBA61A0C35692
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
filename:       /lib/modules/3.2.0-26-generic/misc/vmci.ko
supported:      external
license:        GPL v2
version:        9.1.18.0
description:    VMware Virtual Machine Communication Interface (VMCI).
author:         VMware, Inc.
srcversion:     17017D6780BB2857D35A2EB
alias:          pci:v000015ADd00000740sv*sd*bc*sc*i*
depends:        
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
parm:           disable_host:Disable driver host personality - (default=0) (bool)
parm:           disable_guest:Disable driver guest personality - (default=0) (bool)
parm:           disable_msi:Disable MSI use in driver - (default=0) (bool)
parm:           disable_msix:Disable MSI-X use in driver - (default=0) (bool)
filename:       /lib/modules/3.2.0-26-generic/misc/vsock.ko
supported:      external
alias:          vmware_vsock
license:        GPL v2
version:        9.1.1.0
description:    VMware Virtual Socket Family
author:         VMware, Inc.
srcversion:     9878089A7E91D82DD11D683
depends:        vmci
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
Stopping VMware services:
   VMware Authentication Daemon                                        done
   VM communication interface socket family                            done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make -C /lib/modules/3.2.0-26-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
          MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-26-generic'
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/apic.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/hashFunc.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-root/modules/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-root/modules/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-root/modules/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-26-generic'
make -C $PWD SRCROOT=$PWD/. \
          MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmnet-only'
make -C /lib/modules/3.2.0-26-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
          MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-26-generic'
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
/tmp/vmware-root/modules/vmnet-only/filter.c:60:16: error: ‘THIS_MODULE’ undeclared here (not in a function)
make[2]: *** [/tmp/vmware-root/modules/vmnet-only/filter.o] Error 1
make[2]: *** Waiting for unfinished jobs....
/tmp/vmware-root/modules/vmnet-only/userif.c: In function ‘VNetCsumCopyDatagram’:
/tmp/vmware-root/modules/vmnet-only/userif.c:520:3: error: incompatible type for argument 1 of ‘kmap’
include/linux/highmem.h:48:21: note: expected ‘struct page *’ but argument is of type ‘const struct <anonymous>’
/tmp/vmware-root/modules/vmnet-only/userif.c:523:3: error: incompatible type for argument 1 of ‘kunmap’
include/linux/highmem.h:54:20: note: expected ‘struct page *’ but argument is of type ‘const struct <anonymous>’
/tmp/vmware-root/modules/vmnet-only/netif.c: In function ‘VNetNetIfSetup’:
/tmp/vmware-root/modules/vmnet-only/netif.c:134:7: error: unknown field ‘ndo_set_multicast_list’ specified in initialiser
/tmp/vmware-root/modules/vmnet-only/netif.c:134:7: warning: initialization from incompatible pointer type [enabled by default]
/tmp/vmware-root/modules/vmnet-only/netif.c:134:7: warning: (near initialization for ‘vnetNetifOps.ndo_validate_addr’) [enabled by default]
make[2]: *** [/tmp/vmware-root/modules/vmnet-only/userif.o] Error 1
make[2]: *** [/tmp/vmware-root/modules/vmnet-only/netif.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-26-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmnet-only'
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmblock-only'
make -C /lib/modules/3.2.0-26-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
          MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-26-generic'
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
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-26-generic'
make -C $PWD SRCROOT=$PWD/. \
          MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/vmware-root/modules/vmblock-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/vmware-root/modules/vmblock-only'
cp -f vmblock.ko ./../vmblock.o
make: Leaving directory `/tmp/vmware-root/modules/vmblock-only'
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmci-only'
make -C /lib/modules/3.2.0-26-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
          MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-26-generic'
  CC [M]  /tmp/vmware-root/modules/vmci-only/linux/driver.o
  CC [M]  /tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.o
  CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciContext.o
  CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciDatagram.o
  CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciDoorbell.o
  CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciDriver.o
  CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciEvent.o
  CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciHashtable.o
  CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciQPair.o
  CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciQueuePair.o
  CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciResource.o
  CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciRoute.o
  CC [M]  /tmp/vmware-root/modules/vmci-only/driverLog.o
  LD [M]  /tmp/vmware-root/modules/vmci-only/vmci.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-root/modules/vmci-only/vmci.mod.o
  LD [M]  /tmp/vmware-root/modules/vmci-only/vmci.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-26-generic'
make -C $PWD SRCROOT=$PWD/. \
          MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/vmware-root/modules/vmci-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/vmware-root/modules/vmci-only'
cp -f vmci.ko ./../vmci.o
make: Leaving directory `/tmp/vmware-root/modules/vmci-only'
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmci-only'
make -C /lib/modules/3.2.0-26-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
          MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-26-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-26-generic'
make -C $PWD SRCROOT=$PWD/. \
          MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/vmware-root/modules/vmci-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/vmware-root/modules/vmci-only'
cp -f vmci.ko ./../vmci.o
make: Leaving directory `/tmp/vmware-root/modules/vmci-only'
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vsock-only'
make -C /lib/modules/3.2.0-26-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
          MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-26-generic'
  CC [M]  /tmp/vmware-root/modules/vsock-only/linux/af_vsock.o
  CC [M]  /tmp/vmware-root/modules/vsock-only/linux/notify.o
  CC [M]  /tmp/vmware-root/modules/vsock-only/linux/notifyQState.o
  CC [M]  /tmp/vmware-root/modules/vsock-only/linux/stats.o
  CC [M]  /tmp/vmware-root/modules/vsock-only/linux/util.o
  CC [M]  /tmp/vmware-root/modules/vsock-only/linux/vsockAddr.o
  CC [M]  /tmp/vmware-root/modules/vsock-only/driverLog.o
  LD [M]  /tmp/vmware-root/modules/vsock-only/vsock.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-root/modules/vsock-only/vsock.mod.o
  LD [M]  /tmp/vmware-root/modules/vsock-only/vsock.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-26-generic'
make -C $PWD SRCROOT=$PWD/. \
          MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/vmware-root/modules/vsock-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/vmware-root/modules/vsock-only'
cp -f vsock.ko ./../vsock.o
make: Leaving directory `/tmp/vmware-root/modules/vsock-only'
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual machine communication interface                             done
   VM communication interface socket family                            done
   Blocking file system                                                done
   Virtual ethernet                                                   failed
   VMware Authentication Daemon                                        done

---

### Post by psv8 on 2012-07-18
Please guys, anybody.  I need to sort it out.
Any idias?

---

### Post by DrNo1 on 2012-08-05
[http://communities.vmware.com/thread/400790](http://communities.vmware.com/thread/400790)

Worked for me. Even with version 4.0.4
(just change to 4.0.4)

---


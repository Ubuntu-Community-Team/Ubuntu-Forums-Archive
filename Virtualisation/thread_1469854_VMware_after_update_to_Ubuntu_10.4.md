---
title: "VMware after update to Ubuntu 10.4"
date: 2010-05-02
forum: Virtualisation
---

### Post by wulf-dieter on 2010-05-02
Vmware Workstation 7.0? bundle installed under Ubuntu 9.4 and refined under Ubuntu 9.10 - worked problem free.
Now updated to Ubuntu 10.4
Saw that Vmware had been updated.
On starting either VmPayer or Vmware Workstation the Wmware Kernel module updater pops up to do its work.

All items get a green tick and I assume that these modules have been updated properly.

virtual network device does not get this green tick, but a warning sign ! in a yellow triangle - makes me assume that this did not update correctly.

Confirmed by the fact that the virtual machine does not start.

What can I do?:confused:

---

### Post by winchendonsprings on 2010-05-05
same problem here. except I have even less green ticks.

---

### Post by calc on 2010-05-05
I haven't had any problems with VMware Workstation 7.0.1 on Ubuntu 10.04 AMD64 but I update kernel modules differently.

I run:

sudo vmware-modconfig --console --install-all

I didn't know that updating kernel modules ever worked in the gui for VMware Workstation under Ubuntu, maybe I was just unlucky in the past.

---

### Post by winchendonsprings on 2010-05-05
That didn't work in the terminal for me. and here is when I run the gui installer

[http://lh4.ggpht.com/_IW9lx8xoDpo/S-D4NnuNbdI/AAAAAAAAAgo/aTLNOyUesQo/ohno.png](http://lh4.ggpht.com/_IW9lx8xoDpo/S-D4NnuNbdI/AAAAAAAAAgo/aTLNOyUesQo/ohno.png)

the gui updater/installer always worked for me before.

---

### Post by wulf-dieter on 2010-05-06
> **calc said:**
> I haven't had any problems with VMware Workstation 7.0.1 on Ubuntu 10.04 AMD64 but I update kernel modules differently.

I run:

sudo vmware-modconfig --console --install-all

I didn't know that updating kernel modules ever worked in the gui for VMware Workstation under Ubuntu, maybe I was just unlucky in the past.

Thanks for the hint, however, when I run this routine the GUI pops up giving me the same as before and in the terminal I see the message last line: Virtual ethernet     failed and the virtual machine does not start.

Now I need a hint on how to set up the virtual ethernet (I am a newcomer to Ubuntu)

---

### Post by wulf-dieter on 2010-05-06
> **wulf-dieter said:**
> Thanks for the hint, however, when I run this routine the GUI pops up giving me the same as before and in the terminal I see the message last line: Virtual ethernet     failed and the virtual machine does not start.

Now I need a hint on how to set up the virtual ethernet (I am a newcomer to Ubuntu)

I would like to add here: that I also see anothere error message when I scroll through the terminal saying: 'could not find module vmnet'

---

### Post by TJet1.8 on 2010-05-06
Since you now have 10.04 installed, you will not be able to recompile your VMware modules until you set your build environemnt first.

Install your Linux Headers, C compiler, and Build Essential files:
sudo apt-get install gcc build-essential linux-headers-$(uname -r)

Re-compile your VMware modules:
sudo /usr/bin/vmware-modconfig --console --install-all

This should work for you...try it and report back.

GL :)

---

### Post by wulf-dieter on 2010-05-07
> **TJet1.8 said:**
> Since you now have 10.04 installed, you will not be able to recompile your VMware modules until you set your build environemnt first.

Install your Linux Headers, C compiler, and Build Essential files:
sudo apt-get install gcc build-essential linux-headers-$(uname -r)

Re-compile your VMware modules:
sudo /usr/bin/vmware-modconfig --console --install-all

This should work for you...try it and report back.

GL :)

I have tried it since I saw your other post to a memeber who has the same problem.
The problem persists:

  	 	 	 	 	 	  wulf@wulf-desktop:~$ sudo vmware-modconfig--console--install-all sudo: vmware-modconfig--console--install-all: command not found wulf@wulf-desktop:~$ sudo vmware modconfig  console  install all Logging to /tmp/vmware-root/setup-14328.log filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmmon.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Monitor. author:         VMware, Inc. srcversion:     9FB063A3FC33465439B2834 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  ERROR: modinfo: could not find module vmnet filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmblock.ko supported:      external version:        1.1.2.0 license:        GPL v2 description:    VMware Blocking File System author:         VMware, Inc. srcversion:     400149ED038D22A87322D56 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  parm:           root:The directory the file system redirects to. (charp) filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmci.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Communication Interface (VMCI). author:         VMware, Inc. srcversion:     9721EAF47E95C11AD349B0E depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vsock.ko supported:      external license:        GPL v2 version:        1.0.0.0 description:    VMware Virtual Socket Family author:         VMware, Inc. srcversion:     BC1943DCE52AE461DCC2D43 depends:        vmci vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmmon.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Monitor. author:         VMware, Inc. srcversion:     9FB063A3FC33465439B2834 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  ERROR: modinfo: could not find module vmnet filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmblock.ko supported:      external version:        1.1.2.0 license:        GPL v2 description:    VMware Blocking File System author:         VMware, Inc. srcversion:     400149ED038D22A87322D56 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  parm:           root:The directory the file system redirects to. (charp) filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmci.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Communication Interface (VMCI). author:         VMware, Inc. srcversion:     9721EAF47E95C11AD349B0E depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vsock.ko supported:      external license:        GPL v2 version:        1.0.0.0 description:    VMware Virtual Socket Family author:         VMware, Inc. srcversion:     BC1943DCE52AE461DCC2D43 depends:        vmci vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmmon.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Monitor. author:         VMware, Inc. srcversion:     9FB063A3FC33465439B2834 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  ERROR: modinfo: could not find module vmnet filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmblock.ko supported:      external version:        1.1.2.0 license:        GPL v2 description:    VMware Blocking File System author:         VMware, Inc. srcversion:     400149ED038D22A87322D56 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  parm:           root:The directory the file system redirects to. (charp) filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmci.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Communication Interface (VMCI). author:         VMware, Inc. srcversion:     9721EAF47E95C11AD349B0E depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vsock.ko supported:      external license:        GPL v2 version:        1.0.0.0 description:    VMware Virtual Socket Family author:         VMware, Inc. srcversion:     BC1943DCE52AE461DCC2D43 depends:        vmci vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmmon.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Monitor. author:         VMware, Inc. srcversion:     9FB063A3FC33465439B2834 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  ERROR: modinfo: could not find module vmnet filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmblock.ko supported:      external version:        1.1.2.0 license:        GPL v2 description:    VMware Blocking File System author:         VMware, Inc. srcversion:     400149ED038D22A87322D56 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  parm:           root:The directory the file system redirects to. (charp) filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmci.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Communication Interface (VMCI). author:         VMware, Inc. srcversion:     9721EAF47E95C11AD349B0E depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vsock.ko supported:      external license:        GPL v2 version:        1.0.0.0 description:    VMware Virtual Socket Family author:         VMware, Inc. srcversion:     BC1943DCE52AE461DCC2D43 depends:        vmci vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmmon.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Monitor. author:         VMware, Inc. srcversion:     9FB063A3FC33465439B2834 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  ERROR: modinfo: could not find module vmnet filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmblock.ko supported:      external version:        1.1.2.0 license:        GPL v2 description:    VMware Blocking File System author:         VMware, Inc. srcversion:     400149ED038D22A87322D56 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  parm:           root:The directory the file system redirects to. (charp) filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmci.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Communication Interface (VMCI). author:         VMware, Inc. srcversion:     9721EAF47E95C11AD349B0E depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vsock.ko supported:      external license:        GPL v2 version:        1.0.0.0 description:    VMware Virtual Socket Family author:         VMware, Inc. srcversion:     BC1943DCE52AE461DCC2D43 depends:        vmci vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmmon.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Monitor. author:         VMware, Inc. srcversion:     9FB063A3FC33465439B2834 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  ERROR: modinfo: could not find module vmnet filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmblock.ko supported:      external version:        1.1.2.0 license:        GPL v2 description:    VMware Blocking File System author:         VMware, Inc. srcversion:     400149ED038D22A87322D56 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  parm:           root:The directory the file system redirects to. (charp) filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmci.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Communication Interface (VMCI). author:         VMware, Inc. srcversion:     9721EAF47E95C11AD349B0E depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vsock.ko supported:      external license:        GPL v2 version:        1.0.0.0 description:    VMware Virtual Socket Family author:         VMware, Inc. srcversion:     BC1943DCE52AE461DCC2D43 depends:        vmci vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  Stopping VMware services:    VMware USB Arbitrator############################################## done    VM communication interface socket family########################### done    Virtual machine communication interface############################ done    Virtual machine monitor############################################ done    Blocking file system############################################### done Using 2.6.x kernel build system. make: Gehe in Verzeichnis '/tmp/vmware-root/modules/vmmon-only' make -C /lib/modules/2.6.32-21-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= modules make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae'   CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driver.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driverLog.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/hostif.o /tmp/vmware-root/modules/vmmon-only/linux/hostif.c: In function ‚ÄòHostIFReadUptimeWork‚Äô: /tmp/vmware-root/modules/vmmon-only/linux/hostif.c:1944: warning: ‚ÄònewUpBase‚Äô may be used uninitialized in this function   CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/iommu.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/common/comport.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/common/cpuid.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/common/hashFunc.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/common/memtrack.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/common/phystrack.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/common/task.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/common/vmx86.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/vmcore/moduleloop.o   LD [M]  /tmp/vmware-root/modules/vmmon-only/vmmon.o   Building modules, stage 2.   MODPOST 1 modules   CC      /tmp/vmware-root/modules/vmmon-only/vmmon.mod.o   LD [M]  /tmp/vmware-root/modules/vmmon-only/vmmon.ko make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae' make -C $PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= postbuild make[1]: Betrete Verzeichnis '/tmp/vmware-root/modules/vmmon-only' make[1]: ¬ªpostbuild¬´ ist bereits aktualisiert. make[1]: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmmon-only' cp -f vmmon.ko ./../vmmon.o make: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmmon-only' Using 2.6.x kernel build system. make: Gehe in Verzeichnis '/tmp/vmware-root/modules/vmnet-only' make -C /lib/modules/2.6.32-21-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= modules make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae'   CC [M]  /tmp/vmware-root/modules/vmnet-only/driver.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/hub.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/userif.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/netif.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/bridge.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/filter.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/procfs.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/smac_compat.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/smac.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/vnetEvent.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/vnetUserListener.o /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c: In function ‚ÄòVNetUserListenerEventHandler‚Äô: /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: ‚ÄòTASK_INTERRUPTIBLE‚Äô undeclared (first use in this function) /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: (Each undeclared identifier is reported only once /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: for each function it appears in.) /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c: In function ‚ÄòVNetUserListenerRead‚Äô: /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: ‚ÄòTASK_INTERRUPTIBLE‚Äô undeclared (first use in this function) /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: implicit declaration of function ‚Äòsignal_pending‚Äô /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: implicit declaration of function ‚Äòschedule‚Äô make[2]: *** [/tmp/vmware-root/modules/vmnet-only/vnetUserListener.o] Fehler 1 make[1]: *** [_module_/tmp/vmware-root/modules/vmnet-only] Fehler 2 make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae' make: *** [vmnet.ko] Fehler 2 make: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmnet-only' Using 2.6.x kernel build system. make: Gehe in Verzeichnis '/tmp/vmware-root/modules/vmblock-only' make -C /lib/modules/2.6.32-21-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= modules make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae'   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/block.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/control.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/dbllnklst.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/dentry.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/file.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/filesystem.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/inode.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/module.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/stubs.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/super.o   LD [M]  /tmp/vmware-root/modules/vmblock-only/vmblock.o   Building modules, stage 2.   MODPOST 1 modules   CC      /tmp/vmware-root/modules/vmblock-only/vmblock.mod.o   LD [M]  /tmp/vmware-root/modules/vmblock-only/vmblock.ko make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae' make -C $PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= postbuild make[1]: Betrete Verzeichnis '/tmp/vmware-root/modules/vmblock-only' make[1]: ¬ªpostbuild¬´ ist bereits aktualisiert. make[1]: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmblock-only' cp -f vmblock.ko ./../vmblock.o make: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmblock-only' Using 2.6.x kernel build system. make: Gehe in Verzeichnis '/tmp/vmware-root/modules/vmci-only' make -C /lib/modules/2.6.32-21-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= modules make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae'   CC [M]  /tmp/vmware-root/modules/vmci-only/linux/driver.o   CC [M]  /tmp/vmware-root/modules/vmci-only/linux/driverLog.o   CC [M]  /tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciContext.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciDatagram.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciDriver.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciDs.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciEvent.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciGroup.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciHashtable.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciProcess.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciQueuePair.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciResource.o   LD [M]  /tmp/vmware-root/modules/vmci-only/vmci.o   Building modules, stage 2.   MODPOST 1 modules   CC      /tmp/vmware-root/modules/vmci-only/vmci.mod.o   LD [M]  /tmp/vmware-root/modules/vmci-only/vmci.ko make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae' make -C $PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= postbuild make[1]: Betrete Verzeichnis '/tmp/vmware-root/modules/vmci-only' make[1]: ¬ªpostbuild¬´ ist bereits aktualisiert. make[1]: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmci-only' cp -f vmci.ko ./../vmci.o make: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmci-only' Using 2.6.x kernel build system. make: Gehe in Verzeichnis '/tmp/vmware-root/modules/vmci-only' make -C /lib/modules/2.6.32-21-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= modules make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae'   Building modules, stage 2.   MODPOST 1 modules make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae' make -C $PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= postbuild make[1]: Betrete Verzeichnis '/tmp/vmware-root/modules/vmci-only' make[1]: ¬ªpostbuild¬´ ist bereits aktualisiert. make[1]: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmci-only' cp -f vmci.ko ./../vmci.o make: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmci-only' Using 2.6.x kernel build system. make: Gehe in Verzeichnis '/tmp/vmware-root/modules/vsock-only' make -C /lib/modules/2.6.32-21-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= modules make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae'   CC [M]  /tmp/vmware-root/modules/vsock-only/linux/af_vsock.o /tmp/vmware-root/modules/vsock-only/linux/af_vsock.c:359: warning: initialization from incompatible pointer type   CC [M]  /tmp/vmware-root/modules/vsock-only/linux/notify.o   CC [M]  /tmp/vmware-root/modules/vsock-only/linux/stats.o   CC [M]  /tmp/vmware-root/modules/vsock-only/linux/util.o   CC [M]  /tmp/vmware-root/modules/vsock-only/linux/vsockAddr.o   CC [M]  /tmp/vmware-root/modules/vsock-only/driverLog.o   LD [M]  /tmp/vmware-root/modules/vsock-only/vsock.o   Building modules, stage 2.   MODPOST 1 modules   CC      /tmp/vmware-root/modules/vsock-only/vsock.mod.o   LD [M]  /tmp/vmware-root/modules/vsock-only/vsock.ko make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae' make -C $PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= postbuild make[1]: Betrete Verzeichnis '/tmp/vmware-root/modules/vsock-only' make[1]: ¬ªpostbuild¬´ ist bereits aktualisiert. make[1]: Verlasse Verzeichnis '/tmp/vmware-root/modules/vsock-only' cp -f vsock.ko ./../vsock.o make: Verlasse Verzeichnis '/tmp/vmware-root/modules/vsock-only' Starting VMware services:    VMware USB Arbitrator############################################## done    Virtual machine monitor############################################ done    Virtual machine communication interface############################ done    VM communication interface socket family########################### done    Blocking file system############################################### done    Virtual ethernet###################################################failed wulf@wulf-desktop:~$  
I saw during 10.4 update that VMware got updated. When I tried to run VMware bundle the message was to uninstall the newer version first. So I did not do it for fear to lose the virtual XP-Professional in the machine. I need this as that installation ran perfectly with all my CAT-tools, that cannot be run in Wine or Virtual box, under 9.4 and 9.10.

The problem seems to be that "could not find module vmnet"

So what next? Your help will be appreciated, Thank you.

Wulf-Dieter Krueger: [email]krueger.wulf@gmail.com[/email]

---

### Post by relic70 on 2010-05-07
> **calc said:**
> I haven't had any problems with VMware Workstation 7.0.1 on Ubuntu 10.04 AMD64 but I update kernel modules differently.

I run:

sudo vmware-modconfig --console --install-all

I didn't know that updating kernel modules ever worked in the gui for VMware Workstation under Ubuntu, maybe I was just unlucky in the past.

Thanks calc. That solution worked perfectly for me with VMware Player installed on Lucid. My complete system stalled and had to be powered off as I started my Windows VM in Player after a kernel update.

I had an earlier post on my problem here

[http://ubuntuforums.org/showthread.php?p=9258534](http://ubuntuforums.org/showthread.php?p=9258534)

relic70

---

### Post by wulf-dieter on 2010-05-08
> **TJet1.8 said:**
> Since you now have 10.04 installed, you will not be able to recompile your VMware modules until you set your build environemnt first.

Install your Linux Headers, C compiler, and Build Essential files:
sudo apt-get install gcc build-essential linux-headers-$(uname -r)

Re-compile your VMware modules:
sudo /usr/bin/vmware-modconfig --console --install-all

This should work for you...try it and report back.

GL :)

Sorry I made an error - I did oversee Install...

I did this today and got

wulf@wulf-desktop:~$ sudo apt-get install gcc build-essential linux-headers-$(uname -r)
[sudo] password for wulf: 
Paketlisten werden gelesen... Fertig = [COLOR=Blue]reading package list ... done[/COLOR]
Abhängigkeitsbaum wird aufgebaut  = [COLOR=Blue]building dependence tree[/COLOR]      
Status-Informationen einlesen... Fertig = [COLOR=Blue]reading status info ... done[/COLOR]
gcc ist schon die neueste Version. = [COLOR=Blue]is already the latest version [/COLOR]
build-essential ist schon die neueste Version. = [COLOR=Blue]is already the latest version [/COLOR]
build-essential wurde als manuell installiert festgelegt. = [COLOR=Blue]specified as manually installed[/COLOR]
linux-headers-2.6.32-21-generic-pae ist schon die neueste Version. = [COLOR=Blue]is already the latest version [/COLOR]
linux-headers-2.6.32-21-generic-pae wurde als manuell installiert festgelegt. = [COLOR=Blue]specified as manually installed[/COLOR]
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert. = [COLOR=Blue]0 updated, 0 new installed, 0 to remove and 0 not updated[/COLOR]
wulf@wulf-desktop:~$ sudo /usr/bin/vmware-modconfig --console --install-all
Stopping VMware services:
   VMware USB Arbitrator                                               done
   VM communication interface socket family                            done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
Using 2.6.x kernel build system.
make: Gehe in Verzeichnis '/tmp/vmware-root/modules/vmmon-only'
make -C /lib/modules/2.6.32-21-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae'
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/hostif.o
/tmp/vmware-root/modules/vmmon-only/linux/hostif.c: In function ‘HostIFReadUptimeWork’:
/tmp/vmware-root/modules/vmmon-only/linux/hostif.c:1944: warning: ‘newUpBase’ may be used uninitialized in this function
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/iommu.o
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
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae'
make -C $PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= postbuild
make[1]: Betrete Verzeichnis '/tmp/vmware-root/modules/vmmon-only'
make[1]: »postbuild« ist bereits aktualisiert.
make[1]: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmmon-only'
cp -f vmmon.ko ./../vmmon.o
make: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmmon-only'
Built vmmon module
Using 2.6.x kernel build system.
make: Gehe in Verzeichnis '/tmp/vmware-root/modules/vmnet-only'
make -C /lib/modules/2.6.32-21-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae'
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
make[2]: *** [/tmp/vmware-root/modules/vmnet-only/vnetUserListener.o] Fehler 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmnet-only] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae'
make: *** [vmnet.ko] Fehler 2
make: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmnet-only'
Unable to install vmnet
wulf@wulf-desktop:~$ ^C
wulf@wulf-desktop:~$ 

The German Word 'Fehler' = [COLOR=Blue]error[/COLOR]
'Verlasse Verzeichnis' = [COLOR=Blue]leave directory[/COLOR]
'Gehe in Verzeichnis = [COLOR=Blue]go to  directory[/COLOR]
'Betrete Verzeichnis' = [COLOR=Blue]enter directory

blue is translation of German text

[COLOR=Black]It seems that the issue now is: why is it unable to install vmnet?

Under Applications - System Tools there is the Virtual Network Editor


Thank you very much indeed so far since we are now one step further in the right direction
[/COLOR][/COLOR]

---

### Post by Midahed on 2010-05-08
Has anyone got a solution to this problem - or even a suggestion.  I have exactly the same problem following the installation of VMWare Workstation 6.5 onto a new Lucid 10.04 installation.

Initially I had an error because gcc-4.3.3 and linux-headers were missing from my system.  Having installed those, the VMWare Kernel Updater ran OK for all stages of the update except where it compiles the Virtual Network Device.

As in the previous post, the process ends with 'Unable to install vmnet'

---

### Post by fjgaude on 2010-05-08
"Initially I had an error because gcc-4.3.3 and linux-headers were missing from my system. Having installed those, the VMWare Kernel Updater ran OK for all stages of the update except where it compiles the Virtual Network Device."

That's where the issue is... 10.04 has a new way to handle networks, nm, and what is required is a manual patch to the kernel. Once this is done you have to redo it everytime there is a kernel update, which is often as we all know.

There are instructions on how to patch the kernel somewhere but it is no beginner process, so that is why I switched to Player 3.0, which is not like Server. If you upgrade to Workstation 7.0, I think it fixes the issue with nm, the manager that handles the networking.

---

### Post by wulf-dieter on 2010-05-08
> **fjgaude said:**
> "Initially I had an error because gcc-4.3.3 and linux-headers were missing from my system. Having installed those, the VMWare Kernel Updater ran OK for all stages of the update except where it compiles the Virtual Network Device."

That's where the issue is... 10.04 has a new way to handle networks, nm, and what is required is a manual patch to the kernel. Once this is done you have to redo it everytime there is a kernel update, which is often as we all know.

There are instructions on how to patch the kernel somewhere but it is no beginner process, so that is why I switched to Player 3.0, which is not like Server. If you upgrade to Workstation 7.0, I think it fixes the issue with nm, the manager that handles the networking.

Same problem with Player 3.0 / Workstation 7 - cannot install vmnet

---

### Post by dcstar on 2010-05-09
> **wulf-dieter said:**
> Same problem with Player 3.0 / Workstation 7 - cannot install vmnet

Probably why Vmware now have 10.04 compatible versions available - Player 3.10 RC and Workstation.

---

### Post by heartbeat348 on 2010-05-09
I can confirm that I have been having same problems with vmnet using Workstation VMware-Workstation-7.0.0-203739.i386 on Lucid. 

Have just upgraded to VMware-Workstation-7.0.1-227600.i386 and everything works as it should!! :) :)

---

### Post by wulf-dieter on 2010-05-10
> **heartbeat348 said:**
> I can confirm that I have been having same problems with vmnet using Workstation VMware-Workstation-7.0.0-203739.i386 on Lucid. 

Have just upgraded to VMware-Workstation-7.0.1-227600.i386 and everything works as it should!! :) :)

Now, how did you do that with VMware-workstation not working?

---

### Post by cisforcojo on 2010-05-12
I just got this to work using the technique from this webpage:

[http://www.madirish.net/justin/node/5](http://www.madirish.net/justin/node/5)

```

# cd /tmp
# tar xf /usr/lib/vmware/modules/source/vmnet.tar
# vi vmnet-only/vnetUserListener.c (near line 37 add #include "compat_sched.h")
# tar cf /usr/lib/vmware/modules/source/vmnet.tar vmnet-only
# tar xf /usr/lib/vmware/modules/source/vmci.tar
# vi vmci-only/linux/vmciKernelIf.c (add #include "compat_sched.h" around line 30)
# vi vmci-only/include/pgtbl.h (add #include "compat_sched.h" around line 30)
# tar cf /usr/lib/vmware/modules/source/vmci.tar vmci-only
# vmware-modconfig --console --install-all

```

EDIT: I did not have to edit vmciKernelIf.c and you don't have to put the include on those exact lines. Just after the first set of #include's is fine.

---

### Post by wulf-dieter on 2010-05-16
> **cisforcojo said:**
> I just got this to work using the technique from this webpage:

[http://www.madirish.net/justin/node/5](http://www.madirish.net/justin/node/5)

```

# cd /tmp
# tar xf /usr/lib/vmware/modules/source/vmnet.tar
# vi vmnet-only/vnetUserListener.c (near line 37 add #include "compat_sched.h")
# tar cf /usr/lib/vmware/modules/source/vmnet.tar vmnet-only
# tar xf /usr/lib/vmware/modules/source/vmci.tar
# vi vmci-only/linux/vmciKernelIf.c (add #include "compat_sched.h" around line 30)
# vi vmci-only/include/pgtbl.h (add #include "compat_sched.h" around line 30)
# tar cf /usr/lib/vmware/modules/source/vmci.tar vmci-only
# vmware-modconfig --console --install-all

```EDIT: I did not have to edit vmciKernelIf.c and you don't have to put the include on those exact lines. Just after the first set of #include's is fine.




Well, in the end the solution is simpler than anticipated.

Go to the VMware website, go to download centre and download the latest version of your Workstation. To do this you will have to log in with your user name/e-mail address and password to verify that you have an account with them, that you had to set up when you purchased your original version.
Save the bundle into root of your linux. Double-click on it and it will update your old installation. 
Inbetween you will have to click on the one or the other 'accept'.
When the update has completed you close everything and can start your virtual machine. It will start in the same way as before.

---

### Post by Dravic on 2010-05-16
The common fixes didn't completely work for me either, at the end of the recompile I was getting the same cant find vmnet-only modules also.
 
I posted a fix for coping the vmney-only source into the tmp direct while doing the recompile.
 
[http://ubuntuforums.org/showthread.php?t=1481780](http://ubuntuforums.org/showthread.php?t=1481780)

---

### Post by masux594 on 2010-05-17
> **cisforcojo said:**
> I just got this to work using the technique from this webpage:

[http://www.madirish.net/justin/node/5](http://www.madirish.net/justin/node/5)

```

# cd /tmp
# tar xf /usr/lib/vmware/modules/source/vmnet.tar
# vi vmnet-only/vnetUserListener.c (near line 37 add #include "compat_sched.h")
# tar cf /usr/lib/vmware/modules/source/vmnet.tar vmnet-only
# tar xf /usr/lib/vmware/modules/source/vmci.tar
# vi vmci-only/linux/vmciKernelIf.c (add #include "compat_sched.h" around line 30)
# vi vmci-only/include/pgtbl.h (add #include "compat_sched.h" around line 30)
# tar cf /usr/lib/vmware/modules/source/vmci.tar vmci-only
# vmware-modconfig --console --install-all

```EDIT: I did not have to edit vmciKernelIf.c and you don't have to put the include on those exact lines. Just after the first set of #include's is fine.

Hi.. This solution is reported in many links, but unfortunately for me it doesen't work at all.. I have a fresh install of vMware 7.0.1 in a Lucid x64 fresh install.. In my case the troubles are:

[LIST]
[*]When i unpack the "/usr/lib/vmware/modules/source/vmnet.tar" module, i don't  have any "vnetUserListener.c" file, but two files named
[/LIST]

[LIST=1]
[*]vnetUserListener.c.orig [empty file]
[*]vnetUserListener.c.rej
[/LIST]

[LIST]
[*]The same thing happen to the "/usr/lib/vmware/modules/source/vmci.tar" module, where i find
[/LIST]

[LIST=1]
[*]vmciKernelIf.c.orig [empty file]
[*]vmciKernelIf.c.rej
[/LIST]

[LIST]
[*]And the third problem is that in the "vmci" mdoule i don't have any "include/" folder, only the "linux/" one
[/LIST]
So, if anyone can help, [COLOR=#000000]will appreciate it  very!

Sysc, A
[/COLOR]

---

### Post by masux594 on 2010-05-18
I tried VirtualBox [v3.1.8], but unfortunately it runs too slow.. About 3 minutes to boot Xp [yeah, i know that xp is slow in nature, but not so much] where vMware needs about 1 minute.. So i try to install vMware Workstation 7.1 [RC], all works fine.. So i suppose that [in my x64 system] vMware 7.0.1 doesen't work becouse of "lucid x64" internal structure..

Sysc, A

---

### Post by cisforcojo on 2010-05-19
masux594,

I had that problem before as well.

Uninstall it, clean out your /tmp folder and try again. That worked for me.

---

### Post by raghavshukla007 on 2010-07-25
Please find attachment including the solutions of the same problem:)

> **wulf-dieter said:**
> Vmware Workstation 7.0? bundle installed under Ubuntu 9.4 and refined under Ubuntu 9.10 - worked problem free.
Now updated to Ubuntu 10.4
Saw that Vmware had been updated.
On starting either VmPayer or Vmware Workstation the Wmware Kernel module updater pops up to do its work.

All items get a green tick and I assume that these modules have been updated properly.

virtual network device does not get this green tick, but a warning sign ! in a yellow triangle - makes me assume that this did not update correctly.

Confirmed by the fact that the virtual machine does not start.

What can I do?:confused:

---


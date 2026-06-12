---
title: "Cannot update/compile VMWare Workstation in 10.04 host"
date: 2010-05-05
forum: Virtualisation
---

### Post by winchendonsprings on 2010-05-05
Since Ubuntu update to 10.04 when I try to launch VMWare Workstation 7 or Player the normal VMWare update/compiler pops up to compile for the new kernel. In the past I have had good luck with this, but there are errors with the new kernel. 

Any ideas what to do? After searching I see other people are having issues too, but I didn't find any solutions. 

[IMG]http://lh4.ggpht.com/_IW9lx8xoDpo/S-D4NnuNbdI/AAAAAAAAAgo/aTLNOyUesQo/ohno.png[/IMG]

---

### Post by unknown3 on 2010-05-05
it seems that VMWare 7.1 support Ubuntu 10.04, but it is still beta yet
 
[http://communities.vmware.com/docs/DOC-12155](http://communities.vmware.com/docs/DOC-12155)

---

### Post by winchendonsprings on 2010-05-05
there is no way to edit my current installation of Workstation and Player to work on the 2.6.32 kernel?

I'm on the vmware forum also but I can't find anything that works for me

Anyone?

---

### Post by winchendonsprings on 2010-05-05
I have downloaded the fixes listed here. But I cannot seem to make them work. I am a novice when it comes to terminal work so take a look at my log:
> 
ry@ry-desktop:~$ sudo sh '/home/ry/Downloads/patch-modules.sh' 
[sudo] password for ry: 
mkdir: cannot create directory `original': File exists
/home/ry/Downloads/patch-modules.sh: 7: cannot open vmware-7.0-2.6.32.patch: No such file
tar: vmnet-only: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors
tar: vmci-only: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors
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
make: *** /tmp/vmware-root/modules/vmnet-only: No such file or directory.  Stop.
Unable to install vmnet
ry@ry-desktop:~$ 


---

### Post by techunit on 2010-05-05
For a seamless virtual machine I would recommend that you try openbox because of it ease of use and light affect on the system. I also believe that it is opensource, but you can easily find in the application manager.

---

### Post by winchendonsprings on 2010-05-05
I am aware that there are alternatives to VMWare. I currently have five somewhat important vm's created with VMWare's Workstation so rather than convert those vm's files to run on other software I'd really just like them work in VMWare.

---

### Post by TJet1.8 on 2010-05-06
Guys...VMware WS 7.0.1 and VMplayer 3.0.1 work just fine in 10.04.

You need to recompile the VMware modules...but first, you need to have your build environment set:

Install your Linux Headers, C compiler, and Build Essential files:
sudo apt-get install gcc build-essential linux-headers-$(uname -r)

Re-compile your VMware modules:
sudo /usr/bin/vmware-modconfig --console --install-all

Try it and report back...

GL

---

### Post by crossy on 2010-05-06
> **winchendonsprings said:**
> I have downloaded the fixes listed here. But I cannot seem to make them work. I am a novice when it comes to terminal work so take a look at my log:

Quick question - where did you get these fixes from? I'm using Server rather than Workstation, and like you I've got a good few VM's that I need to need, but VMware Server doesn't seem to like Lucid. :'(

(Oh, and like you I'm aware of VirtualBox etc, but there's reasons I need to use VMware for these VM's)

Bob.

---

### Post by shebaw on 2010-05-06
> **TJet1.8 said:**
> Guys...VMware WS 7.0.1 and VMplayer 3.0.1 work just fine in 10.04.

You need to recompile the VMware modules...but first, you need to have your build environment set:

Install your Linux Headers, C compiler, and Build Essential files:
sudo apt-get install gcc build-essential linux-headers-$(uname -r)

Re-compile your VMware modules:
sudo /usr/bin/vmware-modconfig --console --install-all

Try it and report back...

GL

Dude, I got 2 words for you, YOU ROCK!!!
I'm a linux newbie, and I was so confused trying to find the solution to my problem since I left files in my virtual machine that I didn't back up and I was afraid of loosing them. Your commands fixed everything, thanks again!

---

### Post by TJet1.8 on 2010-05-06
Glad to hear it's working for you....enjoy!
;)

---

### Post by wulf-dieter on 2010-05-07
> **TJet1.8 said:**
> Glad to hear it's working for you....enjoy!
;)


Lucky he, it works for him but not for me - I am still stuck with "virtual ethernet failed" and "could not find module vmnet"

That's what I get in the terminal:
  	 	 	 	 	 	  wulf@wulf-desktop:~$ sudo vmware-modconfig--console--install-all sudo: vmware-modconfig--console--install-all: command not found wulf@wulf-desktop:~$ sudo vmware modconfig  console  install all Logging to /tmp/vmware-root/setup-14328.log filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmmon.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Monitor. author:         VMware, Inc. srcversion:     9FB063A3FC33465439B2834 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  ERROR: modinfo: could not find module vmnet filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmblock.ko supported:      external version:        1.1.2.0 license:        GPL v2 description:    VMware Blocking File System author:         VMware, Inc. srcversion:     400149ED038D22A87322D56 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  parm:           root:The directory the file system redirects to. (charp) filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmci.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Communication Interface (VMCI). author:         VMware, Inc. srcversion:     9721EAF47E95C11AD349B0E depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vsock.ko supported:      external license:        GPL v2 version:        1.0.0.0 description:    VMware Virtual Socket Family author:         VMware, Inc. srcversion:     BC1943DCE52AE461DCC2D43 depends:        vmci vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmmon.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Monitor. author:         VMware, Inc. srcversion:     9FB063A3FC33465439B2834 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  ERROR: modinfo: could not find module vmnet filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmblock.ko supported:      external version:        1.1.2.0 license:        GPL v2 description:    VMware Blocking File System author:         VMware, Inc. srcversion:     400149ED038D22A87322D56 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  parm:           root:The directory the file system redirects to. (charp) filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmci.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Communication Interface (VMCI). author:         VMware, Inc. srcversion:     9721EAF47E95C11AD349B0E depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vsock.ko supported:      external license:        GPL v2 version:        1.0.0.0 description:    VMware Virtual Socket Family author:         VMware, Inc. srcversion:     BC1943DCE52AE461DCC2D43 depends:        vmci vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmmon.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Monitor. author:         VMware, Inc. srcversion:     9FB063A3FC33465439B2834 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  ERROR: modinfo: could not find module vmnet filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmblock.ko supported:      external version:        1.1.2.0 license:        GPL v2 description:    VMware Blocking File System author:         VMware, Inc. srcversion:     400149ED038D22A87322D56 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  parm:           root:The directory the file system redirects to. (charp) filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmci.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Communication Interface (VMCI). author:         VMware, Inc. srcversion:     9721EAF47E95C11AD349B0E depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vsock.ko supported:      external license:        GPL v2 version:        1.0.0.0 description:    VMware Virtual Socket Family author:         VMware, Inc. srcversion:     BC1943DCE52AE461DCC2D43 depends:        vmci vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmmon.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Monitor. author:         VMware, Inc. srcversion:     9FB063A3FC33465439B2834 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  ERROR: modinfo: could not find module vmnet filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmblock.ko supported:      external version:        1.1.2.0 license:        GPL v2 description:    VMware Blocking File System author:         VMware, Inc. srcversion:     400149ED038D22A87322D56 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  parm:           root:The directory the file system redirects to. (charp) filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmci.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Communication Interface (VMCI). author:         VMware, Inc. srcversion:     9721EAF47E95C11AD349B0E depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vsock.ko supported:      external license:        GPL v2 version:        1.0.0.0 description:    VMware Virtual Socket Family author:         VMware, Inc. srcversion:     BC1943DCE52AE461DCC2D43 depends:        vmci vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmmon.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Monitor. author:         VMware, Inc. srcversion:     9FB063A3FC33465439B2834 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  ERROR: modinfo: could not find module vmnet filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmblock.ko supported:      external version:        1.1.2.0 license:        GPL v2 description:    VMware Blocking File System author:         VMware, Inc. srcversion:     400149ED038D22A87322D56 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  parm:           root:The directory the file system redirects to. (charp) filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmci.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Communication Interface (VMCI). author:         VMware, Inc. srcversion:     9721EAF47E95C11AD349B0E depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vsock.ko supported:      external license:        GPL v2 version:        1.0.0.0 description:    VMware Virtual Socket Family author:         VMware, Inc. srcversion:     BC1943DCE52AE461DCC2D43 depends:        vmci vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmmon.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Monitor. author:         VMware, Inc. srcversion:     9FB063A3FC33465439B2834 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  ERROR: modinfo: could not find module vmnet filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmblock.ko supported:      external version:        1.1.2.0 license:        GPL v2 description:    VMware Blocking File System author:         VMware, Inc. srcversion:     400149ED038D22A87322D56 depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  parm:           root:The directory the file system redirects to. (charp) filename:       /lib/modules/2.6.32-21-generic-pae/misc/vmci.ko supported:      external license:        GPL v2 description:    VMware Virtual Machine Communication Interface (VMCI). author:         VMware, Inc. srcversion:     9721EAF47E95C11AD349B0E depends:         vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  filename:       /lib/modules/2.6.32-21-generic-pae/misc/vsock.ko supported:      external license:        GPL v2 version:        1.0.0.0 description:    VMware Virtual Socket Family author:         VMware, Inc. srcversion:     BC1943DCE52AE461DCC2D43 depends:        vmci vermagic:       2.6.32-21-generic-pae SMP mod_unload modversions 586TSC  Stopping VMware services:    VMware USB Arbitrator############################################## done    VM communication interface socket family########################### done    Virtual machine communication interface############################ done    Virtual machine monitor############################################ done    Blocking file system############################################### done Using 2.6.x kernel build system. make: Gehe in Verzeichnis '/tmp/vmware-root/modules/vmmon-only' make -C /lib/modules/2.6.32-21-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= modules make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae'   CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driver.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driverLog.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/hostif.o /tmp/vmware-root/modules/vmmon-only/linux/hostif.c: In function ‚ÄòHostIFReadUptimeWork‚Äô: /tmp/vmware-root/modules/vmmon-only/linux/hostif.c:1944: warning: ‚ÄònewUpBase‚Äô may be used uninitialized in this function   CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/iommu.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/common/comport.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/common/cpuid.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/common/hashFunc.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/common/memtrack.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/common/phystrack.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/common/task.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/common/vmx86.o   CC [M]  /tmp/vmware-root/modules/vmmon-only/vmcore/moduleloop.o   LD [M]  /tmp/vmware-root/modules/vmmon-only/vmmon.o   Building modules, stage 2.   MODPOST 1 modules   CC      /tmp/vmware-root/modules/vmmon-only/vmmon.mod.o   LD [M]  /tmp/vmware-root/modules/vmmon-only/vmmon.ko make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae' make -C $PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= postbuild make[1]: Betrete Verzeichnis '/tmp/vmware-root/modules/vmmon-only' make[1]: ¬ªpostbuild¬´ ist bereits aktualisiert. make[1]: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmmon-only' cp -f vmmon.ko ./../vmmon.o make: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmmon-only' Using 2.6.x kernel build system. make: Gehe in Verzeichnis '/tmp/vmware-root/modules/vmnet-only' make -C /lib/modules/2.6.32-21-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= modules make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae'   CC [M]  /tmp/vmware-root/modules/vmnet-only/driver.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/hub.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/userif.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/netif.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/bridge.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/filter.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/procfs.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/smac_compat.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/smac.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/vnetEvent.o   CC [M]  /tmp/vmware-root/modules/vmnet-only/vnetUserListener.o /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c: In function ‚ÄòVNetUserListenerEventHandler‚Äô: /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: ‚ÄòTASK_INTERRUPTIBLE‚Äô undeclared (first use in this function) /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: (Each undeclared identifier is reported only once /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: for each function it appears in.) /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c: In function ‚ÄòVNetUserListenerRead‚Äô: /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: ‚ÄòTASK_INTERRUPTIBLE‚Äô undeclared (first use in this function) /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: implicit declaration of function ‚Äòsignal_pending‚Äô /tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: implicit declaration of function ‚Äòschedule‚Äô make[2]: *** [/tmp/vmware-root/modules/vmnet-only/vnetUserListener.o] Fehler 1 make[1]: *** [_module_/tmp/vmware-root/modules/vmnet-only] Fehler 2 make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae' make: *** [vmnet.ko] Fehler 2 make: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmnet-only' Using 2.6.x kernel build system. make: Gehe in Verzeichnis '/tmp/vmware-root/modules/vmblock-only' make -C /lib/modules/2.6.32-21-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= modules make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae'   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/block.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/control.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/dbllnklst.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/dentry.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/file.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/filesystem.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/inode.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/module.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/stubs.o   CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/super.o   LD [M]  /tmp/vmware-root/modules/vmblock-only/vmblock.o   Building modules, stage 2.   MODPOST 1 modules   CC      /tmp/vmware-root/modules/vmblock-only/vmblock.mod.o   LD [M]  /tmp/vmware-root/modules/vmblock-only/vmblock.ko make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae' make -C $PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= postbuild make[1]: Betrete Verzeichnis '/tmp/vmware-root/modules/vmblock-only' make[1]: ¬ªpostbuild¬´ ist bereits aktualisiert. make[1]: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmblock-only' cp -f vmblock.ko ./../vmblock.o make: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmblock-only' Using 2.6.x kernel build system. make: Gehe in Verzeichnis '/tmp/vmware-root/modules/vmci-only' make -C /lib/modules/2.6.32-21-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= modules make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae'   CC [M]  /tmp/vmware-root/modules/vmci-only/linux/driver.o   CC [M]  /tmp/vmware-root/modules/vmci-only/linux/driverLog.o   CC [M]  /tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciContext.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciDatagram.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciDriver.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciDs.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciEvent.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciGroup.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciHashtable.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciProcess.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciQueuePair.o   CC [M]  /tmp/vmware-root/modules/vmci-only/common/vmciResource.o   LD [M]  /tmp/vmware-root/modules/vmci-only/vmci.o   Building modules, stage 2.   MODPOST 1 modules   CC      /tmp/vmware-root/modules/vmci-only/vmci.mod.o   LD [M]  /tmp/vmware-root/modules/vmci-only/vmci.ko make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae' make -C $PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= postbuild make[1]: Betrete Verzeichnis '/tmp/vmware-root/modules/vmci-only' make[1]: ¬ªpostbuild¬´ ist bereits aktualisiert. make[1]: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmci-only' cp -f vmci.ko ./../vmci.o make: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmci-only' Using 2.6.x kernel build system. make: Gehe in Verzeichnis '/tmp/vmware-root/modules/vmci-only' make -C /lib/modules/2.6.32-21-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= modules make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae'   Building modules, stage 2.   MODPOST 1 modules make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae' make -C $PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= postbuild make[1]: Betrete Verzeichnis '/tmp/vmware-root/modules/vmci-only' make[1]: ¬ªpostbuild¬´ ist bereits aktualisiert. make[1]: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmci-only' cp -f vmci.ko ./../vmci.o make: Verlasse Verzeichnis '/tmp/vmware-root/modules/vmci-only' Using 2.6.x kernel build system. make: Gehe in Verzeichnis '/tmp/vmware-root/modules/vsock-only' make -C /lib/modules/2.6.32-21-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= modules make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae'   CC [M]  /tmp/vmware-root/modules/vsock-only/linux/af_vsock.o /tmp/vmware-root/modules/vsock-only/linux/af_vsock.c:359: warning: initialization from incompatible pointer type   CC [M]  /tmp/vmware-root/modules/vsock-only/linux/notify.o   CC [M]  /tmp/vmware-root/modules/vsock-only/linux/stats.o   CC [M]  /tmp/vmware-root/modules/vsock-only/linux/util.o   CC [M]  /tmp/vmware-root/modules/vsock-only/linux/vsockAddr.o   CC [M]  /tmp/vmware-root/modules/vsock-only/driverLog.o   LD [M]  /tmp/vmware-root/modules/vsock-only/vsock.o   Building modules, stage 2.   MODPOST 1 modules   CC      /tmp/vmware-root/modules/vsock-only/vsock.mod.o   LD [M]  /tmp/vmware-root/modules/vsock-only/vsock.ko make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic-pae' make -C $PWD SRCROOT=$PWD/. \ 	  MODULEBUILDDIR= postbuild make[1]: Betrete Verzeichnis '/tmp/vmware-root/modules/vsock-only' make[1]: ¬ªpostbuild¬´ ist bereits aktualisiert. make[1]: Verlasse Verzeichnis '/tmp/vmware-root/modules/vsock-only' cp -f vsock.ko ./../vsock.o make: Verlasse Verzeichnis '/tmp/vmware-root/modules/vsock-only' Starting VMware services:    VMware USB Arbitrator############################################## done    Virtual machine monitor############################################ done    Virtual machine communication interface############################ done    VM communication interface socket family########################### done    Blocking file system############################################### done    Virtual ethernet###################################################failed wulf@wulf-desktop:~$  Before I tried to run the vmware bundle again, but I was told to uninstall the newer version first so I did not do it because I was afraid I would lose the virtual XP-Professional in there. I need this, however, since two of my CAT (computer assisted translation) tools only work in a virtual machine giving me access to my production hard disk. They do not work in Wine or Virtual box (where the problem is that I do not get access to my production hard disk with all the Translation Memories.

---

### Post by Ganymedes on 2010-05-07
Sorry, does not work for me.

I have a newly installed Asus laptop with Ubuntu desktop 10.04, 64-bit. I still get a blank screen when trying to open up my VMware computer (XP Pro).

I followed the instructions by Tjet1.8 and they went through smoothly. I also tried uninstall/install before/between these complications.

Well, perhaps I just need to wait for a newer version than 3.0.1 VMware Player.

---

### Post by techunit on 2010-05-09
I don't like that VMware makes you register your address for there product. Not That I wouldn't but why is this important. I don't need more junk mail... any way IBM makes you do this to for some of there stuff and generally it works out fine.

---

### Post by pmoses on 2010-05-09
I had the same errors using vmware workstation 7.0.0 on kernel 2.6.32-22
The recompile instructions did not work for me :(
I fixed it by installing vmware workstation 7.0.1 ...

---

### Post by Ganymedes on 2010-05-10
I have not tried Workstation but only Player - to my knowledge there are technically speaking the same (please, correct me if I am wrong). Anyway, I am using the latest official versions by VMware.

Well, I am not using the kernel from the 10.04 original release, since it is already updated once (through normal ways, Update Manager).

Maybe that explains why this methods works for some?

---

### Post by TJet1.8 on 2010-05-12
Uhmmm....this may be a stupid question but, when you guys are installing VMware (either Workstation or Player), you are installing as root...right?

i.e.:

sudo ./VMware-Workstation-Full-7.0.1-227600.x86_64

-or-

sudo ./VMware-Player-3.0.1-227600.x86_64

???

Even though after installing VMware it doesn't prompt you to reboot your computer....reboot it ANYWAYS!!!
Many issues seem to magically disappear after a reboot. 

Also remember that any time a new kernel is release and installed on your 10.04 system (via Update Manager or manually), you MUST retrieve the new kernel headers in your build environment and recompile your VMware modules:

sudo apt-get install linux-headers-$(uname -r)

sudo /usr/bin/vmware-modconfig --console --install-all

Note: Pathing IS important (i.e. /usr/bin/vmware-modconfig....and not just vmware-modconfig)

---

### Post by Ganymedes on 2010-05-12
Thanks! Well, I could of course try these out, however:

I use "sudo sh VM*.bundle" - method. So, I am using the bundle distribution.

As for new kernel updates:

- I have reinstalled it completely after the new kernel release of 10.04. I did not try with the original one as delivered in the its first release .ISO. So no need for updates.
- Lately, since 6.5 version of Workstation, there has been no reason to fix manually anything, because it has suggested a recompile in its graphical interface. However, with Ubuntu 10.04 it might be of course different (but it does not matter in my case since I first installed it after the new kernel release).
- whatever this is, is something new. I have used on several computers both Linux and Windows VMware Workstation versions in professional use for years.

There has been vagues talks elsewhere that the script for compiling have small inconsistencies in regard to recent Ubuntu kernel versions. I have not studied these scripts, but just waited for a patch or a new version. However, even in VMware Forum, I have got no answers in this regard.

It might be that you use the original 10.04 kernel and that is why it works for you ... or have you done the kernel update? I am talking about 64-bit version like you seem to be.

---

### Post by bamitt2 on 2010-05-12
> **TJet1.8 said:**
> Glad to hear it's working for you....enjoy!
;)Do you have a documented installation for VMware Server 2 on Ubuntu 10.04 LTS?  Or should it be the same as 9.10?

---

### Post by TJet1.8 on 2010-05-15
> **bamitt2 said:**
> Do you have a documented installation for VMware Server 2 on Ubuntu 10.04 LTS?  Or should it be the same as 9.10?

No I do not...I haven't tried installing VMware Server 2.0.2 on 10.04 yet.

I have read on the web that it is the same as 9.10 (i.e. - you need to install the kernel patch to get it working)...but I can't say for sure.

---

### Post by TJet1.8 on 2010-05-15
> **wulf-dieter said:**
> Lucky he, it works for him but not for me - I am still stuck with "virtual ethernet failed" and "could not find module vmnet"



I can't comment on this error as everything works perfectly for me.

I have VMware Workstation 7.0.1 and/or VMware Player 3.0.1 running on 2 different laptops and a desktop....no issues what-so-ever.

You may have a currupted module, in which case you should manually delete it and recompile:

First, rename your existing vmnet compiled modules:
sudo mv /lib/modules/$(uname -r)/misc/vmnet.o /lib/modules/$(uname -r)/misc/vmnet.o.old
sudo mv /lib/modules/$(uname -r)/misc/vmnet.ko /lib/modules/$(uname -r)/misc/vmnet.ko.old

Then try recompiling:
sudo /usr/bin/vmware-modconfig --console --install-all

See if it works for you.

GL

---

### Post by TJet1.8 on 2010-05-15
> **Ganymedes said:**
> I have not tried Workstation but only Player - to my knowledge there are technically speaking the same (please, correct me if I am wrong). Anyway, I am using the latest official versions by VMware.

Well, I am not using the kernel from the 10.04 original release, since it is already updated once (through normal ways, Update Manager).

Maybe that explains why this methods works for some?

The method I described "should" work for any of the lastest Ubuntu releases (9.04 to present).

It will not work for other distro's (i.e. Opensuse, Fedora, etc...) as they name thier "linux-headers" differently...but the VMware module compilation command should be the same for all distro's as it is not distro dependant.

---

### Post by Ganymedes on 2010-05-15
> **TJet1.8 said:**
> The method I described "should" work for any of the lastest Ubuntu releases (9.04 to present).

It will not work for other distro's (i.e. Opensuse, Fedora, etc...) as they name thier "linux-headers" differently...but the VMware module compilation command should be the same for all distro's as it is not distro dependant.

Thanks!

I tried to re-compile, well compiling seems to work, but VMware does not. I also installed 3.1.0 Beta, which got updated immediately update "automatically". 

Anyway, after all this, it does not work. The only difference is that I could kill the application normally and it would not just hang with a black screen.

---

### Post by furioo on 2010-06-05
that is my problem
 [IMG]http://ubuntuforums.org/%3Ca%20href=http://www.ubuntu-pics.de/bild/77394/s__lection_002_v8GI95.png%20target=_blank%3E[img]http://www.ubuntu-pics.de/thumb/77394/s__lection_002_v8GI95.png[/IMG][IMG]http://www.ubuntu-pics.de/bild/77394/s__lection_002_v8GI95.png[/IMG]
i click install
[IMG]http://www.ubuntu-pics.de/bild/77398/s__lection_004_qyORoL.png[/IMG]
and way?

[IMG]http://ubuntuforums.org/%3Ca%20href=%22http://www.ubuntu-pics.de/bild/77394/s__lection_002_v8GI95.png%22%20target=%22_blank%22%3E%3Cimg%20src=%22http://www.ubuntu-pics.de/thumb2/77394/s__lection_002_v8GI95.png%22%20border=%220%22/%3E%3C/a%3E[/IMG]

---

### Post by Ganymedes on 2010-06-05
To the problem that I reported, there has been an unofficial patch for some weeks. I tried it and it works. That patch is available through VMware Forum.

This week a new version of Workstation and Player were released by VMware. They list now Ubuntu 10.04 as supported, among other enhancements. I trust that this problem is in the past now.

---


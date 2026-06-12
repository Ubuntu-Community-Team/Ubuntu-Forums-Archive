---
title: "Problem compiling VMwareTools for ESX 3.5 on a recent kernel 2.6.30"
date: 2010-05-19
forum: Server Platforms
---

### Post by cronos6 on 2010-05-19
Hi

 I'm running an old Ubuntu 6.10 on ESX 3.5. I had that bug : [http://kb.vmware.com/kb/51306](http://kb.vmware.com/kb/51306) and I decided to compile a new kernel for my old Ubuntu. Compilation of 2.6.32 went bad due to make-kpkg bug or so but finally 2.6.30 compiled OK. I've installed the .deb and rebooted : everything seems ok on this new kernel.
 Unfortunatly, I can't install the Vmware tools (VMwareTools-3.5.0-123630.tar.gz) with this 2.6.30 kernel, got those errors : 
 
>           Using 2.6.x kernel build system.
          make: Entering directory `/tmp/vmware-config2/vmmemctl-only'
          make -C /lib/modules/2.6.30-custom/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/.
          modules
          make[1]: Entering directory `/usr/src/linux-2.6.30'
          CC [M]  /tmp/vmware-config2/vmmemctl-only/backdoorGcc32.o
          CC [M]  /tmp/vmware-config2/vmmemctl-only/os.o
          In file included from /tmp/vmware-config2/vmmemctl-only/os.c:51:
          /tmp/vmware-config2/vmmemctl-only/compat_wait.h:78: error: conflicting types for 'poll_initwait'
          include/linux/poll.h:67: error: previous declaration of 'poll_initwait' was here/tmp/vmware-config2/vmmemctl-only/os.c: In function 'os_init':
          /tmp/vmware-config2/vmmemctl-only/os.c:590: error: 'struct proc_dir_entry' has no member named 'get_info'
          make[2]: *** [/tmp/vmware-config2/vmmemctl-only/os.o] Error 1
          make[1]: *** [_module_/tmp/vmware-config2/vmmemctl-only] Error 2
          make[1]: Leaving directory `/usr/src/linux-2.6.30'
          make: *** [vmmemctl.ko] Error 2
          make: Leaving directory `/tmp/vmware-config2/vmmemctl-only'
          Unable to build the vmmemctl module.

          The memory manager driver (vmmemctl module) is used by VMware host software to
          efficiently reclaim memory from a virtual machine.
          If the driver is not available, VMware host software may instead need to swap
          guest memory to disk, which may reduce performance.
          The rest of the software provided by VMware Tools is designed to work
          independently of this feature.
          If you want the memory management feature, you can install the driver by
          running vmware-config-tools.pl again after making sure that gcc, binutils, make
          and the kernel sources for your running kernel are installed on your machine.
          These packages are available on your distribution's installation CD.
          [ Press Enter key to continue ]


          Trying to find a suitable vmhgfs module for your running kernel.

          None of the pre-built vmhgfs modules for VMware Tools is suitable for your
          running kernel.  Do you want this program to try to build the vmhgfs module for
          your system (you need to have a C compiler installed on your system)? [yes]

          Extracting the sources of the vmhgfs module.

          Building the vmhgfs module.

          Using 2.6.x kernel build system.
          make: Entering directory `/tmp/vmware-config3/vmhgfs-only'
          make -C /lib/modules/2.6.30-custom/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/.
          modules
          make[1]: Entering directory `/usr/src/linux-2.6.30'
          CC [M]  /tmp/vmware-config3/vmhgfs-only/backdoor.o
          CC [M]  /tmp/vmware-config3/vmhgfs-only/backdoor.o
          CC [M]  /tmp/vmware-config3/vmhgfs-only/backdoorGcc32.o
          CC [M]  /tmp/vmware-config3/vmhgfs-only/bdhandler.o
          /tmp/vmware-config3/vmhgfs-only/bdhandler.c:29:27: error: asm/semaphore.h: No such file or directory
          In file included from /tmp/vmware-config3/vmhgfs-only/request.h:35,
                         from /tmp/vmware-config3/vmhgfs-only/bdhandler.c:48:
          /tmp/vmware-config3/vmhgfs-only/compat_wait.h:78: error: conflicting types for 'poll_initwait'
          include/linux/poll.h:67: error: previous declaration of 'poll_initwait' was heremake[2]: *** [/tmp/vmware-config3/vmhgfs-only/bdhandler.o] Error 1
          make[1]: *** [_module_/tmp/vmware-config3/vmhgfs-only] Error 2
          make[1]: Leaving directory `/usr/src/linux-2.6.30'
          make: *** [vmhgfs.ko] Error 2
          make: Leaving directory `/tmp/vmware-config3/vmhgfs-only'
          Unable to build the vmhgfs module.

          The filesystem driver (vmhgfs module) is used only for the shared folder
          feature. The rest of the software provided by VMware Tools is designed to work
          independently of this feature.
          If you wish to have the shared folders feature, you can install the driver by
          running vmware-config-tools.pl again after making sure that gcc, binutils, make
          and the kernel sources for your running kernel are installed on your machine.
          These packages are available on your distribution's installation CD.
          [ Press Enter key to continue ]

          
    Well, that's a real mess. Anyone figure out how to compile the VmwareTools on Ubuntu 32bits 2.6.30 ? Thanks

---

### Post by HermanAB on 2010-05-19
> The filesystem driver (vmhgfs module) is used only for the shared folder
feature. The rest of the software provided by VMware Tools is designed to work
independently of this feature.

Disable the vmhgfs feature and compile again?

---

### Post by cronos6 on 2010-05-20
Got errors with ALL modules, I've just pasted a part of output.

---


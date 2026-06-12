---
title: "My host shared folder doesn't visible in the guest"
date: 2010-01-13
forum: Virtualisation
---

### Post by arlahiru on 2010-01-13
host: win XP
guest: Ubuntu 9.10
vmware: 6.5.0

I have shared a folder in my host os with the guest os using wmware settings. But I can't see that folder in /mnt/hgfs directory. please help me :(

I got an errors when I install vmware tools. Thought may be its related to this problem.
specially when it install vmhgfs module it says "Unable to build the vmhgfs module."

error goes like this :
```

[ Press Enter key to continue ] 

None of the pre-built vmhgfs modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmhgfs module for
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmhgfs module.

Building the vmhgfs module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config16/vmhgfs-only'
make -C /lib/modules/2.6.31-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /tmp/vmware-config16/vmhgfs-only/backdoor.o
In file included from /tmp/vmware-config16/vmhgfs-only/backdoor.h:29,
                 from /tmp/vmware-config16/vmhgfs-only/backdoor.c:40:
/tmp/vmware-config16/vmhgfs-only/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
  CC [M]  /tmp/vmware-config16/vmhgfs-only/backdoorGcc32.o
In file included from /tmp/vmware-config16/vmhgfs-only/backdoor.h:29,
                 from /tmp/vmware-config16/vmhgfs-only/backdoorGcc32.c:45:
/tmp/vmware-config16/vmhgfs-only/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
  CC [M]  /tmp/vmware-config16/vmhgfs-only/bdhandler.o
In file included from /tmp/vmware-config16/vmhgfs-only/rpcout.h:30,
                 from /tmp/vmware-config16/vmhgfs-only/hgfsBd.h:28,
                 from /tmp/vmware-config16/vmhgfs-only/bdhandler.c:45:
/tmp/vmware-config16/vmhgfs-only/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config16/vmhgfs-only/request.h:35,
                 from /tmp/vmware-config16/vmhgfs-only/bdhandler.c:50:
/tmp/vmware-config16/vmhgfs-only/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
make[2]: *** [/tmp/vmware-config16/vmhgfs-only/bdhandler.o] Error 1
make[1]: *** [_module_/tmp/vmware-config16/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-config16/vmhgfs-only'
Unable to build the vmhgfs module.

The filesystem driver (vmhgfs module) is used only for the shared folder 
feature. The rest of the software provided by VMware Tools is designed to work 
independently of this feature.

If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 

```thanks for all in advance.

---

### Post by SecretCode on 2010-01-14
You won't get the shared folder in the guest until you've successfully installed vmhgfs. Unfortunately it's a long time since I've used vmware and I can't remember if I got around this error. Virtualbox was just much easier for me...

---

### Post by arlahiru on 2010-01-15
> **SecretCode said:**
> You won't get the shared folder in the guest until you've successfully installed vmhgfs. Unfortunately it's a long time since I've used vmware and I can't remember if I got around this error. Virtualbox was just much easier for me...

okay, I got it. yeah, If I couldn't find a solution for this one, I'll definitely switch to the VB. But still I'm looking for a way to fix this issue.
Anyway, thanx for your support.

---


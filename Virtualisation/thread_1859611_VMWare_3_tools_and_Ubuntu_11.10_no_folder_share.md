---
title: "VMWare 3 tools and Ubuntu 11.10 no folder share"
date: 2011-10-14
forum: Virtualisation
---

### Post by myotis on 2011-10-14
I have just unpgraded to 11.10 running in VMWare fusion (on Snow Leopard) and re-installed VMWare tools. However several things are't working, in particular folder sharing. 

When I configure VMWare tools I get the following errors:

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmhgfs-only'
make -C /lib/modules/3.0.0-12-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/backdoor.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/backdoorGcc32.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/bdhandler.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/cpName.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/cpNameLinux.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/cpNameLite.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/dentry.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/dir.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/file.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/filesystem.o
/tmp/vmware-root/modules/vmhgfs-only/filesystem.c:69:26: error: ‘SPIN_LOCK_UNLOCKED’ undeclared here (not in a function)
make[2]: *** [/tmp/vmware-root/modules/vmhgfs-only/filesystem.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmhgfs-only'

The filesystem driver (vmhgfs module) is used only for the shared folder 
feature. The rest of the software provided by VMware Tools is designed to work 
independently of this feature.

Has anyone any ideas what might be happening here, On previous upgrades this has always just worked.

Many thanks,

Graham

---

### Post by fjgaude on 2011-10-14
I think you might need an update to Fusion... this last update to Ubuntu is massive and most of the VMware software has to be tailored to work with it.

---

### Post by myotis on 2011-10-14
Frank,

I did wonder if an upgrade might be the answer.

Thanks,

Graham

---

### Post by myotis on 2011-10-20
Upgrading to vmware fusion 4 fixed this. However, the vmware tools menu install din't mount the iso nothing happened when you clicked on the menu. Managed to fudge an install manually, and folder sharing working.

Still waiting for a proper response from VMware (emailed the tuesday) other than an automated "read the install instructions response". 

Thanks for the help.

Graham

---

### Post by felixblue on 2011-12-29
I think one easy way to solve the build problem is:
[FONT=monospace]
follow this diff:
[/FONT]-static spinlock_t swdevs_lock = SPIN_LOCK_UNLOCKED; +static DEFINE_SPINLOCK(swdevs_lock);

reference: [http://patchwork.ozo.com/patch/235/](http://patchwork.ozo.com/patch/235/)

---


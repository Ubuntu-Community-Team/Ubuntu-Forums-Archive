---
title: "vmblock failing to compile with 3.8.0-27 headers (ubuntu 13.04)"
date: 2013-08-07
forum: Virtualisation
---

### Post by Jim_Bowerman on 2013-08-07
I am using VMware Workstation 9.0.2 on Ubuntu 13.04 x86_64.   When I try to recompile the modules, I get errors in vmblock.  Details below. 

Has anyone found or written the patch for this particular combination of headers & modules?   I see a lot of patches for incompatibility issues of this type, but not for this particular kernel level.   


make: Entering directory `/tmp/modconfig-yTsjlZ/vmblock-only'
/usr/bin/make -C /lib/modules/3.8.0-27-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-27-generic'
  CC [M]  /tmp/modconfig-yTsjlZ/vmblock-only/linux/block.o
  CC [M]  /tmp/modconfig-yTsjlZ/vmblock-only/linux/control.o
  CC [M]  /tmp/modconfig-yTsjlZ/vmblock-only/linux/dentry.o
  CC [M]  /tmp/modconfig-yTsjlZ/vmblock-only/linux/file.o
  CC [M]  /tmp/modconfig-yTsjlZ/vmblock-only/linux/inode.o
  CC [M]  /tmp/modconfig-yTsjlZ/vmblock-only/linux/filesystem.o
  CC [M]  /tmp/modconfig-yTsjlZ/vmblock-only/linux/module.o
  CC [M]  /tmp/modconfig-yTsjlZ/vmblock-only/linux/stubs.o
  CC [M]  /tmp/modconfig-yTsjlZ/vmblock-only/linux/super.o
/tmp/modconfig-yTsjlZ/vmblock-only/linux/control.c: In function ‘ExecuteBlockOp’:
/tmp/modconfig-yTsjlZ/vmblock-only/linux/control.c:285:9: warning: assignment from incompatible pointer type [enabled by default]
/tmp/modconfig-yTsjlZ/vmblock-only/linux/control.c:296:4: warning: passing argument 1 of ‘putname’ from incompatible pointer type [enabled by default]
In file included from include/linux/proc_fs.h:5:0,
                 from /tmp/modconfig-yTsjlZ/vmblock-only/linux/control.c:28:
include/linux/fs.h:2052:13: note: expected ‘struct filename *’ but argument is of type ‘char *’
/tmp/modconfig-yTsjlZ/vmblock-only/linux/dentry.c:38:4: warning: initialization from incompatible pointer type [enabled by default]
/tmp/modconfig-yTsjlZ/vmblock-only/linux/dentry.c:38:4: warning: (near initialization for ‘LinkDentryOps.d_revalidate’) [enabled by default]
/tmp/modconfig-yTsjlZ/vmblock-only/linux/dentry.c: In function ‘DentryOpRevalidate’:
/tmp/modconfig-yTsjlZ/vmblock-only/linux/dentry.c:104:7: warning: passing argument 2 of ‘actualDentry->d_op->d_revalidate’ makes integer from pointer without a cast [enabled by default]
/tmp/modconfig-yTsjlZ/vmblock-only/linux/dentry.c:104:7: note: expected ‘unsigned int’ but argument is of type ‘struct nameidata *’
/tmp/modconfig-yTsjlZ/vmblock-only/linux/inode.c:49:4: warning: initialization from incompatible pointer type [enabled by default]
/tmp/modconfig-yTsjlZ/vmblock-only/linux/inode.c:49:4: warning: (near initialization for ‘RootInodeOps.lookup’) [enabled by default]
  LD [M]  /tmp/modconfig-yTsjlZ/vmblock-only/vmblock.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "putname" [/tmp/modconfig-yTsjlZ/vmblock-only/vmblock.ko] undefined!
  CC      /tmp/modconfig-yTsjlZ/vmblock-only/vmblock.mod.o
  LD [M]  /tmp/modconfig-yTsjlZ/vmblock-only/vmblock.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-27-generic'

---


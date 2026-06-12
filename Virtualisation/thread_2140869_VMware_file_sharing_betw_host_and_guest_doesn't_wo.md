---
title: "VMware file sharing betw host and guest doesn't work on Ubuntu 13.04"
date: 2013-04-30
forum: Virtualisation
---

### Post by bostjanv on 2013-04-30
Hello,
I am using a VMware Player on 64 bit Windows 7 to run Ubuntu 13.04, and I installed VMware tools to enable (among other things) file sharing between host and guest. However, file sharing does not work even though it worked fine on Ubuntu 12.10. I get the following messages:

Using 2.6.x kernel build system.
make: Entering directory `/tmp/modconfig-JGcnb7/vmhgfs-only'
/usr/bin/make -C /lib/modules/3.8.0-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /tmp/modconfig-JGcnb7/vmhgfs-only/backdoor.o
  CC [M]  /tmp/modconfig-JGcnb7/vmhgfs-only/backdoorGcc32.o
  CC [M]  /tmp/modconfig-JGcnb7/vmhgfs-only/bdhandler.o
  CC [M]  /tmp/modconfig-JGcnb7/vmhgfs-only/cpName.o
  CC [M]  /tmp/modconfig-JGcnb7/vmhgfs-only/cpNameLinux.o
  CC [M]  /tmp/modconfig-JGcnb7/vmhgfs-only/cpNameLite.o
  CC [M]  /tmp/modconfig-JGcnb7/vmhgfs-only/dentry.o
  CC [M]  /tmp/modconfig-JGcnb7/vmhgfs-only/dir.o
  CC [M]  /tmp/modconfig-JGcnb7/vmhgfs-only/file.o
  CC [M]  /tmp/modconfig-JGcnb7/vmhgfs-only/filesystem.o
  CC [M]  /tmp/modconfig-JGcnb7/vmhgfs-only/fsutil.o
  CC [M]  /tmp/modconfig-JGcnb7/vmhgfs-only/hgfsBd.o
  CC [M]  /tmp/modconfig-JGcnb7/vmhgfs-only/hgfsEscape.o
  CC [M]  /tmp/modconfig-JGcnb7/vmhgfs-only/hgfsUtil.o
  CC [M]  /tmp/modconfig-JGcnb7/vmhgfs-only/inode.o
/tmp/modconfig-JGcnb7/vmhgfs-only/inode.c: In function ‘HgfsTruncatePages’:
/tmp/modconfig-JGcnb7/vmhgfs-only/inode.c:888:4: error: implicit declaration of function ‘vmtruncate’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/tmp/modconfig-JGcnb7/vmhgfs-only/inode.o] Error 1
make[1]: *** [_module_/tmp/modconfig-JGcnb7/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/modconfig-JGcnb7/vmhgfs-only'

Any suggestion would be appreciated.
Regards,
bostjanv

---


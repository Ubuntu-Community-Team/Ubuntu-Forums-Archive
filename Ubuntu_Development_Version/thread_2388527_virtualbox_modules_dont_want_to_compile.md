---
title: "virtualbox modules dont want to compile"
date: 2018-04-04
forum: Ubuntu Development Version
---

### Post by nardusg on 2018-04-04
Hi Ubuntu'ers

Don't know what I broke but has anyone seen this error or got an idea ?

```
root@nix:~# apt-get install virtualbox virtualbox-dkms virtualbox-qt --reinstallReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 0 not upgraded.
Need to get 26.2 MB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://za.archive.ubuntu.com/ubuntu bionic/multiverse amd64 virtualbox-qt amd64 5.2.8-dfsg-5 [8,530 kB]
Get:2 http://za.archive.ubuntu.com/ubuntu bionic/multiverse amd64 virtualbox amd64 5.2.8-dfsg-5 [17.0 MB]
Get:3 http://za.archive.ubuntu.com/ubuntu bionic/multiverse amd64 virtualbox-dkms all 5.2.8-dfsg-5 [656 kB]                                                                                                  
Fetched 26.2 MB in 14s (1,916 kB/s)                                                                                                                                                                          
(Reading database ... 248944 files and directories currently installed.)
Preparing to unpack .../virtualbox-qt_5.2.8-dfsg-5_amd64.deb ...
Unpacking virtualbox-qt (5.2.8-dfsg-5) over (5.2.8-dfsg-5) ...
Preparing to unpack .../virtualbox_5.2.8-dfsg-5_amd64.deb ...
Unpacking virtualbox (5.2.8-dfsg-5) over (5.2.8-dfsg-5) ...
Preparing to unpack .../virtualbox-dkms_5.2.8-dfsg-5_all.deb ...


------------------------------
Deleting module version: 5.2.8
completely from the DKMS tree.
------------------------------
Done.
Unpacking virtualbox-dkms (5.2.8-dfsg-5) over (5.2.8-dfsg-5) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for ureadahead (0.100.0-20) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3) ...
Setting up virtualbox-dkms (5.2.8-dfsg-5) ...
Loading new virtualbox-5.2.8 DKMS files...
Building for 4.15.0-14-generic
Building initial module for 4.15.0-14-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/virtualbox-dkms.0.crash'
Error! Bad return status for module build on kernel: 4.15.0-14-generic (x86_64)
Consult /var/lib/dkms/virtualbox/5.2.8/build/make.log for more information.
Processing triggers for menu (2.1.47ubuntu1) ...
Setting up virtualbox (5.2.8-dfsg-5) ...
vboxweb.service is a disabled or a static unit not running, not starting it.
Processing triggers for systemd (237-3ubuntu7) ...
Processing triggers for man-db (2.8.2-1) ...
Processing triggers for shared-mime-info (1.9-2) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Setting up virtualbox-qt (5.2.8-dfsg-5) ...
Processing triggers for menu (2.1.47ubuntu1) ...
root@nix:~# cat /var/lib/dkms/virtualbox/5.2.8/build/make.log
DKMS make.log for virtualbox-5.2.8 for kernel 4.15.0-14-generic (x86_64)
Wed Apr  4 11:31:00 SAST 2018
make: Entering directory '/usr/src/linux-headers-4.15.0-14-generic'
  CC [M]  /var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/linux/SUPDrv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/SUPDrv.o
  CC [M]  /var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/SUPDrvGip.o
  CC [M]  /var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/SUPDrvSem.o
  CC [M]  /var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/SUPDrvTracer.o
  CC [M]  /var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/SUPLibAll.o
  CC [M]  /var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/r0drv/alloc-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/r0drv/initterm-r0drv.o
/bin/bash: ./debian/scripts/retpoline-extract-one: No such file or directory
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/SUPLibAll.o' failed
make[2]: *** [/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/SUPLibAll.o] Error 127
make[2]: *** Waiting for unfinished jobs....
/bin/bash: ./debian/scripts/retpoline-extract-one: No such file or directory
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/SUPDrvSem.o' failed
make[2]: *** [/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/SUPDrvSem.o] Error 127
/bin/bash: ./debian/scripts/retpoline-extract-one: No such file or directory
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/r0drv/initterm-r0drv.o' failed
make[2]: *** [/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/r0drv/initterm-r0drv.o] Error 127
/bin/bash: ./debian/scripts/retpoline-extract-one: No such file or directory
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/r0drv/alloc-r0drv.o' failed
make[2]: *** [/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/r0drv/alloc-r0drv.o] Error 127
/bin/bash: ./debian/scripts/retpoline-extract-one: No such file or directory
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/linux/SUPDrv-linux.o' failed
make[2]: *** [/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/linux/SUPDrv-linux.o] Error 127
/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/SUPDrvTracer.o: warning: objtool: .text+0x7: indirect jump found in RETPOLINE build
/bin/bash: ./debian/scripts/retpoline-extract-one: No such file or directory
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/SUPDrvTracer.o' failed
make[2]: *** [/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/SUPDrvTracer.o] Error 127
/bin/bash: ./debian/scripts/retpoline-extract-one: No such file or directory
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/SUPDrvGip.o' failed
make[2]: *** [/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/SUPDrvGip.o] Error 127
/bin/bash: ./debian/scripts/retpoline-extract-one: No such file or directory
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/SUPDrv.o' failed
make[2]: *** [/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv/SUPDrv.o] Error 127
scripts/Makefile.build:606: recipe for target '/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv' failed
make[1]: *** [/var/lib/dkms/virtualbox/5.2.8/build/vboxdrv] Error 2
Makefile:1552: recipe for target '_module_/var/lib/dkms/virtualbox/5.2.8/build' failed
make: *** [_module_/var/lib/dkms/virtualbox/5.2.8/build] Error 2
make: Leaving directory '/usr/src/linux-headers-4.15.0-14-generic'
root@nix:~# 

```

Thanks

---

### Post by dino99 on 2018-04-04
Just testing on my system, via synaptic, and it also crashed
This has already been reported  Bug #1760973  and is related to the latest 4.15.014 kernel
Booting with the 4.15.0-13 kernel should not expose that problem when installing virtualbox ( not tested myself)

---

### Post by nardusg on 2018-04-04
Hi dino99

Thanks, but is it related ?

Regards

Nardus

---

### Post by nardusg on 2018-04-04
OK, got it working sort of. Rolled a version back of the kernel and is compiling now.

---


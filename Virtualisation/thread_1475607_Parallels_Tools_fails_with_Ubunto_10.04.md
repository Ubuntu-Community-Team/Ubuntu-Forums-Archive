---
title: "Parallels Tools fails with Ubunto 10.04"
date: 2010-05-07
forum: Virtualisation
---

### Post by emtownsend on 2010-05-07
*(Just noticed I misspelled Ubuntu in my thread title.  Sorry, it is late!)*

Using Parallels 4 for Windows & Linux, I am unable to install the Parallels Tools.  I have tried every known fix that I can find on the web to no avail.
Here is the error I get:

[IMG]http://www.smugmug.com/photos/859454051_rgBa6-L.png[/IMG]

I just purchased this program & am getting frustrated beyond belief.  Any help would be appreciated.  The Parallels forums are about useless.  I have posted three times today since early morning and none of my posts show up until "approved".
I am thinking VMware or VB are going to be best!  Help!

Here is one of the last errors in my overly long parallels-tools-install.log:

Error: there is no X modules for this version of X server.
Error: failed to install user space application and drivers

---

### Post by lisati on 2010-05-07
I'm not familiar with parallel-tools. Are you able to post the information that the error message suggests looking at?

You might want to do this at the command line:
```
cat /var/log/parallel-tools-install.log > log.txt
``` and then attach the file log.txt to your reply.

---

### Post by emtownsend on 2010-05-07
OK, here it is.  Kinda long though:

2010-05-06T15:50:03-0700: 

Parallels Tools 4.0.6630.449744 Installer started.
2010-05-06T15:50:10-0700: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [1]
2010-05-06T15:50:14-0700: E: Couldn't find package dkms
2010-05-06T15:50:14-0700: execCmd: ./installer/pm.sh download_guest_tools 2>&1 [0]

Thu May  6 15:50:14 PDT 2010
Start installation or upgrade of Guest Tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
In file included from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ApiNet.h:21,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmeth.h:11,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.c:37:
/usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ParallelsTypes.h:120:7: warning: "_MSC_VER" is not defined
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
see include/linux/module.h for more information
WARNING: modpost: Found 3 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/inode.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/file.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/interface.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Start installation of prl_tg kernel module
Start installation of prl_fs kernel module
Installation of kernel modules was finished successfully
/etc/modprobe.conf is missing
Start installation of user space modules
X server: xorg, v1.7.6
Install X modules from directory: .1.7
System X modules are placed in /usr/lib/xorg/modules
Error: there is no X modules for this version of X server
Error: failed to install user space applications and drivers
2010-05-06T15:50:35-0700: execCmd: ./install --install [165]
2010-05-06T15:50:35-0700: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2010-05-06T15:51:14-0700: 

Parallels Tools 4.0.6630.449744 Installer started.
2010-05-06T15:51:29-0700: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [1]
2010-05-06T15:51:32-0700: E: Couldn't find package dkms
2010-05-06T15:51:32-0700: execCmd: ./installer/pm.sh download_guest_tools 2>&1 [0]

Thu May  6 15:51:32 PDT 2010
Start installation or upgrade of Guest Tools
Found Guest Tools directory: /usr/lib/parallels-tools
Start removal of user space modules
head: cannot open `/usr/lib/parallels-tools/.backup/.psf' for reading: No such file or directory
sed: -e expression #1, char 0: no previous regular expression
Cannot umount ""

rmdir: failed to remove `': No such file or directory
grep: /usr/lib/parallels-tools/.backup/.psf: No such file or directory
Removing of X server configuration is skipped.
Removal of user space applications and drivers was finished successfully
Start removal of prl_eth kernel module
Kernel module prl_eth was unloaded
Start removal of prl_tg kernel module
Kernel module prl_tg was unloaded
Start removal of prl_fs kernel module
Kernel module prl_fs was unloaded
Remove kernel modules according to /usr/lib/parallels-tools/.backup/.kmods.list file
Removal of kernel modules was finished successfully
Register service to install new Guest Tools
Perform installation into the /usr/lib/parallels-tools directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
In file included from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ApiNet.h:21,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmeth.h:11,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.c:37:
/usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ParallelsTypes.h:120:7: warning: "_MSC_VER" is not defined
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
see include/linux/module.h for more information
WARNING: modpost: Found 3 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/inode.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/file.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/interface.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Start installation of prl_tg kernel module
Start installation of prl_fs kernel module
Installation of kernel modules was finished successfully
/etc/modprobe.conf is missing
grep: /etc/X11/xorg.conf: No such file or directory
Start installation of user space modules
X server: xorg, v1.7.6
Install X modules from directory: .1.7
System X modules are placed in /usr/lib/xorg/modules
Error: there is no X modules for this version of X server
Error: failed to install user space applications and drivers
2010-05-06T15:51:53-0700: execCmd: ./install --install [165]
2010-05-06T15:51:53-0700: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2010-05-06T16:22:16-0700: 

Parallels Tools 4.0.6630.449744 Installer started.

Thu May  6 16:22:24 PDT 2010
Start removal of Guest Tools
Found Guest Tools directory: /usr/lib/parallels-tools
Start removal of user space modules
head: cannot open `/usr/lib/parallels-tools/.backup/.psf' for reading: No such file or directory
sed: -e expression #1, char 0: no previous regular expression
Cannot umount ""

rmdir: failed to remove `': No such file or directory
grep: /usr/lib/parallels-tools/.backup/.psf: No such file or directory
Removal of user space applications and drivers was finished successfully
Start removal of prl_eth kernel module
Kernel module prl_eth was unloaded
Start removal of prl_tg kernel module
Kernel module prl_tg was unloaded
Start removal of prl_fs kernel module
Kernel module prl_fs was unloaded
Remove kernel modules according to /usr/lib/parallels-tools/.backup/.kmods.list file
Removal of kernel modules was finished successfully
Remove /usr/lib/parallels-tools directory
Parallels Guest Tools were removed successfully!
2010-05-06T16:22:25-0700: Parallels Guest Tools were installed, upgraded or removed successfully!
Please, reboot your OS to finish installation, upgrade or removal of Guest Tools.
2010-05-06T16:22:25-0700: execCmd: /usr/lib/parallels-tools/install --remove [0]
2010-05-06T16:22:28-0700: installer: reboot.
2010-05-06T21:58:10-0700: 

Parallels Tools 4.0.6630.449744 Installer started.
2010-05-06T21:58:25-0700: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [1]
2010-05-06T21:58:41-0700: WARNING: The following packages cannot be authenticated!
  dkms fakeroot patch
Authentication warning overridden.
Selecting previously deselected package dkms.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 122714 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.1.2-2fakesync1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.1.1.2-2fakesync1) ...

Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up patch (2.6-2ubuntu1) ...
2010-05-06T21:58:42-0700: execCmd: ./installer/pm.sh download_guest_tools 2>&1 [0]

Thu May  6 21:58:42 PDT 2010
Start installation or upgrade of Guest Tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
In file included from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ApiNet.h:21,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmeth.h:11,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.c:37:
/usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ParallelsTypes.h:120:7: warning: "_MSC_VER" is not defined
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
see include/linux/module.h for more information
WARNING: modpost: Found 3 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/inode.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/file.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/interface.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Start installation of prl_tg kernel module
Start installation of prl_fs kernel module
DKMS modules were added successfully
DKMS modules were built successfully
Installation of kernel modules was finished successfully
/etc/modprobe.conf is missing
Start installation of user space modules
X server: xorg, v1.7.6
Install X modules from directory: .1.7
System X modules are placed in /usr/lib/xorg/modules
Error: there is no X modules for this version of X server
Error: failed to install user space applications and drivers
2010-05-06T21:59:09-0700: execCmd: ./install --install [165]
2010-05-06T21:59:09-0700: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2010-05-06T22:29:02-0700: 

Parallels Tools 4.0.6630.449744 Installer started.
2010-05-06T22:29:08-0700: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [0]

Thu May  6 22:29:08 PDT 2010
Start installation or upgrade of Guest Tools
Found Guest Tools directory: /usr/lib/parallels-tools
Start removal of user space modules
head: cannot open `/usr/lib/parallels-tools/.backup/.psf' for reading: No such file or directory
sed: -e expression #1, char 0: no previous regular expression
Cannot umount ""

rmdir: failed to remove `': No such file or directory
grep: /usr/lib/parallels-tools/.backup/.psf: No such file or directory
Removing of X server configuration is skipped.
Removal of user space applications and drivers was finished successfully
Start removal of prl_eth kernel module
Kernel module prl_eth was unloaded
Start removal of prl_tg kernel module
Kernel module prl_tg was unloaded
Start removal of prl_fs kernel module
Kernel module prl_fs was unloaded
Remove kernel modules according to /usr/lib/parallels-tools/.backup/.kmods.list file
DKMS modules were removed successfully
Removal of kernel modules was finished successfully
Register service to install new Guest Tools
Perform installation into the /usr/lib/parallels-tools directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
In file included from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ApiNet.h:21,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmeth.h:11,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.c:37:
/usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ParallelsTypes.h:120:7: warning: "_MSC_VER" is not defined
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
see include/linux/module.h for more information
WARNING: modpost: Found 3 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/inode.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/file.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/interface.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Start installation of prl_tg kernel module
Start installation of prl_fs kernel module
DKMS modules were added successfully
DKMS modules were built successfully
Installation of kernel modules was finished successfully
/etc/modprobe.conf is missing
grep: /etc/X11/xorg.conf: No such file or directory
Start installation of user space modules
X server: xorg, v1.7.6
Install X modules from directory: .1.7
System X modules are placed in /usr/lib/xorg/modules
Error: there is no X modules for this version of X server
Error: failed to install user space applications and drivers
2010-05-06T22:29:38-0700: execCmd: ./install --install [165]
2010-05-06T22:29:38-0700: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2010-05-06T22:42:59-0700: 

Parallels Tools 4.0.6630.449744 Installer started.
2010-05-06T22:43:07-0700: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [0]

Thu May  6 22:43:07 PDT 2010
Start installation or upgrade of Guest Tools
Found Guest Tools directory: /usr/lib/parallels-tools
Start removal of user space modules
head: cannot open `/usr/lib/parallels-tools/.backup/.psf' for reading: No such file or directory
sed: -e expression #1, char 0: no previous regular expression
Cannot umount ""

rmdir: failed to remove `': No such file or directory
grep: /usr/lib/parallels-tools/.backup/.psf: No such file or directory
Removing of X server configuration is skipped.
Removal of user space applications and drivers was finished successfully
Start removal of prl_eth kernel module
Kernel module prl_eth was unloaded
Start removal of prl_tg kernel module
Kernel module prl_tg was unloaded
Start removal of prl_fs kernel module
Kernel module prl_fs was unloaded
Remove kernel modules according to /usr/lib/parallels-tools/.backup/.kmods.list file
DKMS modules were removed successfully
Removal of kernel modules was finished successfully
Register service to install new Guest Tools
Perform installation into the /usr/lib/parallels-tools directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
In file included from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ApiNet.h:21,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmeth.h:11,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.c:37:
/usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ParallelsTypes.h:120:7: warning: "_MSC_VER" is not defined
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
see include/linux/module.h for more information
WARNING: modpost: Found 3 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/inode.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/file.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/interface.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Start installation of prl_tg kernel module
Start installation of prl_fs kernel module
DKMS modules were added successfully
DKMS modules were built successfully
Installation of kernel modules was finished successfully
/etc/modprobe.conf is missing
grep: /etc/X11/xorg.conf: No such file or directory
Start installation of user space modules
X server: xorg, v1.7.6
Install X modules from directory: .1.7
System X modules are placed in /usr/lib/xorg/modules
Error: there is no X modules for this version of X server
Error: failed to install user space applications and drivers
2010-05-06T22:43:30-0700: execCmd: ./install --install [165]
2010-05-06T22:43:30-0700: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2010-05-06T22:43:58-0700: 

Parallels Tools 4.0.6630.449744 Installer started.

Thu May  6 22:44:08 PDT 2010
Start removal of Guest Tools
Found Guest Tools directory: /usr/lib/parallels-tools
Start removal of user space modules
head: cannot open `/usr/lib/parallels-tools/.backup/.psf' for reading: No such file or directory
sed: -e expression #1, char 0: no previous regular expression
Cannot umount ""

rmdir: failed to remove `': No such file or directory
grep: /usr/lib/parallels-tools/.backup/.psf: No such file or directory
Removal of user space applications and drivers was finished successfully
Start removal of prl_eth kernel module
Kernel module prl_eth was unloaded
Start removal of prl_tg kernel module
Kernel module prl_tg was unloaded
Start removal of prl_fs kernel module
Kernel module prl_fs was unloaded
Remove kernel modules according to /usr/lib/parallels-tools/.backup/.kmods.list file
DKMS modules were removed successfully
Removal of kernel modules was finished successfully
Remove /usr/lib/parallels-tools directory
Parallels Guest Tools were removed successfully!
2010-05-06T22:44:11-0700: Parallels Guest Tools were installed, upgraded or removed successfully!
Please, reboot your OS to finish installation, upgrade or removal of Guest Tools.
2010-05-06T22:44:11-0700: execCmd: /usr/lib/parallels-tools/install --remove [0]
2010-05-06T22:44:13-0700: installer: reboot.
2010-05-06T22:46:16-0700: 

Parallels Tools 4.0.6630.449744 Installer started.
2010-05-06T22:46:34-0700: 

Parallels Tools 4.0.6630.449744 Installer started.
2010-05-06T22:46:56-0700: 

Parallels Tools 4.0.6630.449744 Installer started.
2010-05-06T22:47:02-0700: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [0]

Thu May  6 22:47:02 PDT 2010
Start installation or upgrade of Guest Tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
In file included from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ApiNet.h:21,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmeth.h:11,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.c:37:
/usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ParallelsTypes.h:120:7: warning: "_MSC_VER" is not defined
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
see include/linux/module.h for more information
WARNING: modpost: Found 3 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/inode.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/file.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/interface.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Start installation of prl_tg kernel module
Start installation of prl_fs kernel module
DKMS modules were added successfully
DKMS modules were built successfully
Installation of kernel modules was finished successfully
/etc/modprobe.conf is missing
Start installation of user space modules
X server: xorg, v1.7.6
Install X modules from directory: .1.7
System X modules are placed in /usr/lib/xorg/modules
Error: there is no X modules for this version of X server
Error: failed to install user space applications and drivers
2010-05-06T22:47:29-0700: execCmd: ./install --install [165]
2010-05-06T22:47:29-0700: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2010-05-06T23:10:17-0700: 

Parallels Tools 4.0.6630.449744 Installer started.
2010-05-06T23:10:23-0700: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [0]

Thu May  6 23:10:24 PDT 2010
Start installation or upgrade of Guest Tools
Found Guest Tools directory: /usr/lib/parallels-tools
Start removal of user space modules
head: cannot open `/usr/lib/parallels-tools/.backup/.psf' for reading: No such file or directory
sed: -e expression #1, char 0: no previous regular expression
Cannot umount ""

rmdir: failed to remove `': No such file or directory
grep: /usr/lib/parallels-tools/.backup/.psf: No such file or directory
Removing of X server configuration is skipped.
Removal of user space applications and drivers was finished successfully
Start removal of prl_eth kernel module
Kernel module prl_eth was unloaded
Start removal of prl_tg kernel module
Kernel module prl_tg was unloaded
Start removal of prl_fs kernel module
Kernel module prl_fs was unloaded
Remove kernel modules according to /usr/lib/parallels-tools/.backup/.kmods.list file
DKMS modules were removed successfully
Removal of kernel modules was finished successfully
Register service to install new Guest Tools
Perform installation into the /usr/lib/parallels-tools directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
In file included from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ApiNet.h:21,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmeth.h:11,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.c:37:
/usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ParallelsTypes.h:120:7: warning: "_MSC_VER" is not defined
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
see include/linux/module.h for more information
WARNING: modpost: Found 3 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/inode.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/file.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/interface.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Start installation of prl_tg kernel module
Start installation of prl_fs kernel module
DKMS modules were added successfully
DKMS modules were built successfully
Installation of kernel modules was finished successfully
/etc/modprobe.conf is missing
grep: /etc/X11/xorg.conf: No such file or directory
Start installation of user space modules
X server: xorg, v1.7.6
Install X modules from directory: .1.7
System X modules are placed in /usr/lib/xorg/modules
Error: there is no X modules for this version of X server
Error: failed to install user space applications and drivers
2010-05-06T23:10:55-0700: execCmd: ./install --install [165]
2010-05-06T23:10:55-0700: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.
2010-05-06T23:11:04-0700: 

Parallels Tools 4.0.6630.449744 Installer started.

Thu May  6 23:11:11 PDT 2010
Start removal of Guest Tools
Found Guest Tools directory: /usr/lib/parallels-tools
Start removal of user space modules
head: cannot open `/usr/lib/parallels-tools/.backup/.psf' for reading: No such file or directory
sed: -e expression #1, char 0: no previous regular expression
Cannot umount ""

rmdir: failed to remove `': No such file or directory
grep: /usr/lib/parallels-tools/.backup/.psf: No such file or directory
Removal of user space applications and drivers was finished successfully
Start removal of prl_eth kernel module
Kernel module prl_eth was unloaded
Start removal of prl_tg kernel module
Kernel module prl_tg was unloaded
Start removal of prl_fs kernel module
Kernel module prl_fs was unloaded
Remove kernel modules according to /usr/lib/parallels-tools/.backup/.kmods.list file
DKMS modules were removed successfully
Removal of kernel modules was finished successfully
Remove /usr/lib/parallels-tools directory
Parallels Guest Tools were removed successfully!
2010-05-06T23:11:15-0700: Parallels Guest Tools were installed, upgraded or removed successfully!
Please, reboot your OS to finish installation, upgrade or removal of Guest Tools.
2010-05-06T23:11:15-0700: execCmd: /usr/lib/parallels-tools/install --remove [0]
2010-05-06T23:11:21-0700: installer: reboot.
2010-05-06T23:14:52-0700: 

Parallels Tools 4.0.6630.449744 Installer started.
2010-05-06T23:14:55-0700: execCmd: ./installer/pm.sh check_guest_tools 2>&1 [0]

Thu May  6 23:14:55 PDT 2010
Start installation or upgrade of Guest Tools
Installed Guest Tools were not found
Perform installation into the /usr/lib/parallels-tools directory
cat: /usr/lib/parallels-tools/kmods/../version: No such file or directory
Start installation of prl_eth kernel module
make: Entering directory `/usr/lib/parallels-tools/kmods'
cd prl_eth/pvmnet && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
In file included from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ApiNet.h:21,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmeth.h:11,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.c:37:
/usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ParallelsTypes.h:120:7: warning: "_MSC_VER" is not defined
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/prl_eth.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_eth/pvmnet'
cd prl_tg/Toolgate/Guest/Linux/prl_tg && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg SRCROOT=/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prltg.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.o
see include/linux/module.h for more information
WARNING: modpost: Found 3 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg/prl_tg.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_tg/Toolgate/Guest/Linux/prl_tg'
cp -f prl_tg/Toolgate/Guest/Linux/prl_tg/*.symvers prl_fs/SharedFolders/Guest/Linux/prl_fs ||:
cd prl_fs/SharedFolders/Guest/Linux/prl_fs && make
make[1]: Entering directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/super.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/inode.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/file.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/interface.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.o
see include/linux/module.h for more information
  CC      /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.mod.o
  LD [M]  /usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs/prl_fs.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Leaving directory `/usr/lib/parallels-tools/kmods/prl_fs/SharedFolders/Guest/Linux/prl_fs'
make: Leaving directory `/usr/lib/parallels-tools/kmods'
Start installation of prl_tg kernel module
Start installation of prl_fs kernel module
DKMS modules were added successfully
DKMS modules were built successfully
Installation of kernel modules was finished successfully
/etc/modprobe.conf is missing
Start installation of user space modules
X server: xorg, v1.7.6
Install X modules from directory: .1.7
System X modules are placed in /usr/lib/xorg/modules
Error: there is no X modules for this version of X server
Error: failed to install user space applications and drivers
2010-05-06T23:15:22-0700: execCmd: ./install --install [165]
2010-05-06T23:15:22-0700: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.

---

### Post by aneuryzma on 2010-05-08
hey, did you solve it ? same problem here

---

### Post by emtownsend on 2010-05-08
> **aneuryzma said:**
> hey, did you solve it ? same problem here

No.  Wish I had.  I will keep trying but probably not until Sunday afternoon or Monday morning.  If I can solve it, I will post.  Please do the same if you solve it.

---

### Post by totaloncue on 2010-05-09
I'm experiencing what looks to be the same issue (same error message). Trying to run this on a Macbook Pro with 1GB of RAM and Core Duo processor. 

I did manage to get Ubuntu 10 running (along with the necessary tools) on VirtualBox, so may just stick with that.

Let me know if you find a fix to this issue.

Thanks a ton!

---

### Post by ltaylor on 2010-05-09
I am using Parallels Desktop 5 on my Mini-mac and just updated to Ubuntu 10.04 LTS through the suggestion of Ubuntu's Update Manager.
There were errors in the update, but I was offered the opportunity to run in reduced graphic formats this one time. 
The result looks OK, about the same as before the upgrade. But I don't want all these errors, and I want to find what's wrong. I am posting in this thread because it sounds related -- Ubuntu 10.04, Parallels. 
The file attached is copied from one of the error logs presented for debugging. In it, it seems to say it could not find the Parallels modules, e.g. "prlmouse" and "prlvideo".
"Fatal server error: no screens found."
LAT

---

### Post by jmabry111 on 2010-05-13
I am having the same problem on 10.04. Here is my parallels install log for the last install attempt:



Installer started. Parallels Tools v.4.0-3846.436358.
2010-05-13T11:32:08-0400: execCmd: ./installer/check_selinux.sh 2>&1 [1]
2010-05-13T11:32:08-0400: execCmd: ./installer/pm.sh check 2>&1 [0]

Thu May 13 11:32:08 EDT 2010
Start installation or upgrade of Guest Tools
Found Guest Tools directory: /usr/lib/parallels-tools
Start removal of user space modules
head: cannot open `/usr/lib/parallels-tools/.backup/.psf' for reading: No such file or directory
sed: -e expression #1, char 0: no previous regular expression
Cannot umount ""

rmdir: failed to remove `': No such file or directory
grep: /usr/lib/parallels-tools/.backup/.psf: No such file or directory
Removal of user space applications and drivers was finished successfully
Start removal of prl_eth kernel module
sed: can't read /usr/lib/parallels-tools/.backup/.kmods.list: No such file or directory
Start removal of prl_tg kernel module
sed: can't read /usr/lib/parallels-tools/.backup/.kmods.list: No such file or directory
Start removal of prl_fs kernel module
sed: can't read /usr/lib/parallels-tools/.backup/.kmods.list: No such file or directory
Removal of kernel modules was finished successfully
Remove /usr/lib/parallels-tools directory
Register service to install new Guest Tools
Perform installation into the /usr/lib/parallels-tools directory
Start installation of prl_eth kernel module
make -C /lib/modules/2.6.32-21-generic/build M=/usr/lib/parallels-tools/kmods/prl_eth/pvmnet
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/built-in.o
  CC [M]  /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o
In file included from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ApiNet.h:21,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmeth.h:11,
                 from /usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.c:37:
/usr/lib/parallels-tools/kmods/prl_eth/pvmnet/ParallelsTypes.h:120:7: warning: "_MSC_VER" is not defined
/usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.c: In function ‘pvmnet_setup’:
/usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.c:382: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.c:383: error: ‘struct net_device’ has no member named ‘get_stats’
/usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.c:385: error: ‘struct net_device’ has no member named ‘open’
/usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.c:386: error: ‘struct net_device’ has no member named ‘stop’
/usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.c:387: error: ‘struct net_device’ has no member named ‘init’
/usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.c:389: error: ‘struct net_device’ has no member named ‘set_multicast_list’
make[2]: *** [/usr/lib/parallels-tools/kmods/prl_eth/pvmnet/pvmnet.o] Error 1
make[1]: *** [_module_/usr/lib/parallels-tools/kmods/prl_eth/pvmnet] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [all] Error 2
Error: could not build prl_eth kernel module
Error: failed to install kernel modules
2010-05-13T11:32:12-0400: execCmd: ./install --install [143]
2010-05-13T11:32:12-0400: Error: An error occurred when installing Parallels Tools. Please go to /var/log/parallels-tools-install.log for more information.

---

### Post by sunlight.architect on 2010-05-17
This is a major pain as I rely on Windows software for work and now cannot access any of it! Boo. I had Parallels 4 already installed, and just this weekend upgraded my  Ubuntu install to 10.04, and hey presto, Parallels no longer works.

I'm no longer up to scratch on my Linux techie stuff (it's been about 6 years since I last used it) but I tried running Parallels from the command line to see its output, so if this sheds any light on the problem for you folks who actually DO know a thing about Linux, here's what it spat out:


*** glibc detected *** /usr/lib/parallels-desktop/parallels-desktop: corrupted double-linked list: 0x09dcace8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0x3cf6591]
/lib/tls/i686/cmov/libc.so.6(+0x6b9ea)[0x3cf69ea]
/lib/tls/i686/cmov/libc.so.6(+0x6cd65)[0x3cf7d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x3cfaecd]
/usr/lib/parallels-desktop/libs/libQtCore.so.4/libQtCore.so.4(_Z5qFreePv+0x1d)[0x3f5de5d]
/usr/lib/parallels-desktop/libs/libQtCore.so.4/libQtCore.so.4(_ZN7QString4freeEPNS_4DataE+0x1d)[0x3fa9abd]
/usr/lib/parallels-desktop/parallels-desktop[0x80ad1ae]
/usr/lib/parallels-desktop/parallels-desktop[0x80ad27e]
/usr/lib/parallels-desktop/parallels-desktop[0x884fa70]
/lib/tls/i686/cmov/libc.so.6(+0x2f1bf)[0x3cba1bf]
/lib/tls/i686/cmov/libc.so.6(+0x2f22f)[0x3cba22f]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xee)[0x3ca1bde]
/usr/lib/parallels-desktop/parallels-desktop(_ZN6QTimer11qt_metacallEN11QMetaObject4CallEiPPv+0x39)[0x8099261]
======= Memory map: ========
00110000-00173000 r-xp 00000000 08:05 4562986    /usr/lib/parallels-desktop/libs/libGL.so.1/libGL.so.1
00173000-00179000 rwxp 00062000 08:05 4562986    /usr/lib/parallels-desktop/libs/libGL.so.1/libGL.so.1
00179000-0017a000 rwxp 00000000 00:00 0 
0017a000-00181000 r-xp 00000000 08:05 2548272    /usr/lib/libSM.so.6.0.1
00181000-00182000 r-xp 00006000 08:05 2548272    /usr/lib/libSM.so.6.0.1
00182000-00183000 rwxp 00007000 08:05 2548272    /usr/lib/libSM.so.6.0.1
00183000-00198000 r-xp 00000000 08:05 2548268    /usr/lib/libICE.so.6.3.0
00198000-00199000 r-xp 00014000 08:05 2548268    /usr/lib/libICE.so.6.3.0
00199000-0019a000 rwxp 00015000 08:05 2548268    /usr/lib/libICE.so.6.3.0
0019a000-0019c000 rwxp 00000000 00:00 0 
0019c000-001a4000 r-xp 00000000 08:05 2548360    /usr/lib/libXcursor.so.1.0.2
001a4000-001a5000 r-xp 00007000 08:05 2548360    /usr/lib/libXcursor.so.1.0.2
001a5000-001a6000 rwxp 00008000 08:05 2548360    /usr/lib/libXcursor.so.1.0.2
001a6000-001a7000 rwxp 00000000 00:00 0 
001a7000-001a9000 r-xp 00000000 08:05 2548362    /usr/lib/libXinerama.so.1.0.0
001a9000-001aa000 r-xp 00001000 08:05 2548362    /usr/lib/libXinerama.so.1.0.0
001aa000-001ab000 rwxp 00002000 08:05 2548362    /usr/lib/libXinerama.so.1.0.0
001ab000-001b9000 r-xp 00000000 08:05 2548292    /usr/lib/libXext.so.6.4.0
001b9000-001ba000 r-xp 0000d000 08:05 2548292    /usr/lib/libXext.so.6.4.0
001ba000-001bb000 rwxp 0000e000 08:05 2548292    /usr/lib/libXext.so.6.4.0
001bb000-001bc000 rwxp 00000000 00:00 0 
001bc000-001e0000 r-xp 00000000 08:05 3738573    /lib/tls/i686/cmov/libm-2.11.1.so
001e0000-001e1000 r-xp 00023000 08:05 3738573    /lib/tls/i686/cmov/libm-2.11.1.so
001e1000-001e2000 rwxp 00024000 08:05 3738573    /lib/tls/i686/cmov/libm-2.11.1.so
001e2000-001ec000 r-xp 00000000 08:05 4571173    /usr/lib/parallels-desktop/libs/libgcc_s.so.1/libgcc_s.so.1
001ec000-001ed000 rwxp 00009000 08:05 4571173    /usr/lib/parallels-desktop/libs/libgcc_s.so.1/libgcc_s.so.1
001ed000-001f6000 r-xp 00000000 08:05 3738571    /lib/tls/i686/cmov/libcrypt-2.11.1.so
001f6000-001f7000 r-xp 00008000 08:05 3738571    /lib/tls/i686/cmov/libcrypt-2.11.1.so
001f7000-001f8000 rwxp 00009000 08:05 3738571    /lib/tls/i686/cmov/libcrypt-2.11.1.so
001f8000-0021f000 rwxp 00000000 00:00 0 
0021f000-00222000 r-xp 00000000 08:05 3711063    /lib/libuuid.so.1.3.0
00222000-00223000 r-xp 00002000 08:05 3711063    /lib/libuuid.so.1.3.0
00223000-00224000 rwxp 00003000 08:05 3711063    /lib/libuuid.so.1.3.0
00224000-00248000 r-xp 00000000 08:05 3711184    /lib/libexpat.so.1.5.2
00248000-0024a000 r-xp 00024000 08:05 3711184    /lib/libexpat.so.1.5.2
0024a000-0024b000 rwxp 00026000 08:05 3711184    /lib/libexpat.so.1.5.2
0024b000-0024c000 rwxp 00000000 00:00 0 
0024c000-00250000 r-xp 00000000 08:05 2548280    /usr/lib/libXdmcp.so.6.0.0
00250000-00251000 r-xp 00003000 08:05 2548280    /usr/lib/libXdmcp.so.6.0.0
00251000-00252000 rwxp 00004000 08:05 2548280    /usr/lib/libXdmcp.so.6.0.0
00252000-00254000 rwxp 00000000 00:00 0 
00254000-00255000 r-xp 00000000 08:05 5262216    /usr/lib/locale/en_GB.utf8/LC_IDENTIFICATION
00255000-00256000 r-xp 00000000 08:05 3514640    /usr/lib/locale/en_GB.utf8/LC_MEASUREMENT
00256000-00257000 r-xp 00000000 08:05 3555624    /usr/lib/locale/en_GB.utf8/LC_MESSAGES/SYS_LC_MESSAGES
00257000-00258000 r-xp 00000000 08:05 4055196    /usr/lib/locale/en_GB.utf8/LC_TIME
00258000-0025e000 r-xp 00000000 08:05 3738576    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
0025e000-0025f000 r-xp 00006000 08:05 3738576    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
0025f000-00260000 rwxp 00007000 08:05 3738576    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00260000-00273000 r-xp 00000000 08:05 3738575    /lib/tls/i686/cmov/libnsl-2.11.1.so
00273000-00274000 r-xp 00012000 08:05 3738575    /lib/tls/i686/cmov/libnsl-2.11.1.so
00274000-00275000 rwxp 00013000 08:05 3738575    /lib/tls/i686/cmov/libnsl-2.11.1.so
00275000-00277000 rwxp 00000000 00:00 0 
00277000-00279000 r-xp 00000000 08:05 5268690    /usr/lib/gconv/UTF-16.so
00279000-0027a000 r-xp 00001000 08:05 5268690    /usr/lib/gconv/UTF-16.so
0027a000-0027b000 rwxp 00002000 08:05 5268690    /usr/lib/gconv/UTF-16.so
0027b000-00280000 r-xs 00000000 08:05 1139084    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
00280000-00288000 r-xs 00000000 08:05 1139510    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
00288000-0028e000 r-xs 00000000 08:05 1139753    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-le32d4.cache-3
0028e000-00292000 r-xs 00000000 08:05 1140261    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
00292000-00293000 r-xs 00000000 08:05 1140263    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
00293000-00294000 r-xs 00000000 08:05 1140264    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
00294000-0029c000 r-xp 00000000 08:05 2548327    /usr/lib/libXrender.so.1.3.0
0029c000-0029d000 r-xp 00007000 08:05 2548327    /usr/lib/libXrender.so.1.3.0
0029d000-0029e000 rwxp 00008000 08:05 2548327    /usr/lib/libXrender.so.1.3.0
0029e000-002a8000 r-xp 00000000 08:05 3738578    /lib/tls/i686/cmov/libnss_files-2.11.1.so
002a8000-002a9000 r-xp 00009000 08:05 3738578    /lib/tls/i686/cmov/libnss_files-2.11.1.so
002a9000-002aa000 rwxp 0000a000 08:05 3738578    /lib/tls/i686/cmov/libnss_files-2.11.1.so
002aa000-002b2000 r-xs 00000000 08:05 1139759    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
002b2000-002d4000 r-xs 00000000 08:05 1139766    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3parallels_crash_handler: [pid=4056, tid=4056] crash (signal 6) at ip b17422

---

### Post by sunlight.architect on 2010-05-17
oops sorry double posted, not yet figured out how to delete this one!

---

### Post by emtownsend on 2010-05-17
I have an "official" ticket in with Parallels.
The steps they had me try did not work.  I retried their suggestions just in case, but it seems the suggestions are just old "how to install Parallels Tools" steps that do not take into account the newest version of Ubuntu.
When resolved, I will post here.  Please do the same if you guys get a solution.

---

### Post by begunfx on 2010-05-17
I'm having the same problem.  I thought it was because I didn't do an update to ubuntu first, but after running a successful update, I then did the upgrade (again).  And still had the same problem.  Thankfully, I have the previous version as a virtual machine backed up on Time Machine, and was able to restore it with no problem.  Anyone have any ideas?  I'd like to upgrade.

Thanks.

> **ltaylor said:**
> I am using Parallels Desktop 5 on my Mini-mac and just updated to Ubuntu 10.04 LTS through the suggestion of Ubuntu's Update Manager.
There were errors in the update, but I was offered the opportunity to run in reduced graphic formats this one time. 
The result looks OK, about the same as before the upgrade. But I don't want all these errors, and I want to find what's wrong. I am posting in this thread because it sounds related -- Ubuntu 10.04, Parallels. 
The file attached is copied from one of the error logs presented for debugging. In it, it seems to say it could not find the Parallels modules, e.g. "prlmouse" and "prlvideo".
"Fatal server error: no screens found."
LAT

---

### Post by Dsoslglece on 2010-05-18
Hi,
I've had (since I installed it on my iMac 5 days ago) the same problem with Ubuntu, and didn't yet managed to install prls tools.
But, since you mentioned having this problem with windows too, I can at least assure you that I had no problem to do it with XP nor win7, and ditto for Kubuntu that is also installed on here(but maybe reason is that this last one is a version 9).

---

### Post by emtownsend on 2010-05-21
Parallels 2nd tier support wrote back to me.  It is not good:

> [aserebrennikova - Wed May. 19 09:37:56 2010 ]:
> 
> Dear Eric,
> 
> Unfortunately Ubuntu 10.04 is not supported both Host and Guest OS in
> Parallels Desktop for Windows/Linux
> [http://www.parallels.com/products/desktop/pd4wl/sr/](http://www.parallels.com/products/desktop/pd4wl/sr/)
> 
> That is why you cannot install Parallels Tools, as they were not
> developed for Ubuntu 10.04
> 
> Please feel free to contact us if you have any questions.

I replied to him that I would like instructions for returning my Parallels.  It is no good to me now.  VMware works fine.  This is so aggravating.

---

### Post by jimt65 on 2010-05-30
i found this in the comments of a youtube video, it worked for me. 

On Menu Bar: Virtual Machine -> Install Parallels Tools.
Click Continue and you should see an icon of a CD-ROM in the Ubuntu desktop. Ignore it.
Run Terminal and type the following: sudo sh '/media/Parallels Tools/install'
Just accept everything it&#65279; says and you're done.
After that, reboot the virtual machine.

---

### Post by emtownsend on 2010-06-01
Unfortunately, same error.
Parallels officially said 10.04 is not supported but they are working on support for it.
I told them at first that I was PO'd and wanted my money back, but then thought better of it and decided to tough it out.  I was just frustrated and torqued that they are taking so long for official support.  So, for now, I use VMware...

---

### Post by rhlrx on 2010-08-16
I believe I have an interim solution.  Ubuntu 10.04 installs a new kernel version 2.6.32-24 which the latest version of Parallels Tools (build 5.0.9370) does not support.  I booted with the 2.6.32-23-386 kernel and successfully installed Parallels Tools.  It all seems to work ...

I actually modified my Grub menu so it boots with that kernel by default.

> **emtownsend said:**
> Unfortunately, same error.
Parallels officially said 10.04 is not supported but they are working on support for it.
I told them at first that I was PO'd and wanted my money back, but then thought better of it and decided to tough it out.  I was just frustrated and torqued that they are taking so long for official support.  So, for now, I use VMware...

---


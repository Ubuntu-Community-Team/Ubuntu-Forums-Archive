---
title: "vmware workstation 7.1.1 can not be launched"
date: 2010-09-05
forum: Virtualisation
---

### Post by yasto on 2010-09-05
[SIZE=3][COLOR=Navy]when I finished the installation then try to launch vmware workstation 7.1.1
the errors comes up[/COLOR]
[/SIZE]
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
Stopping VMware services:
   VMware USB Arbitrator                                               done
   VM communication interface socket family                            done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make -C /lib/modules/2.6.32-24-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
/usr/src/linux-headers-2.6.32-24-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
make[2]: gcc: Command not found
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driver.o
/bin/sh: gcc: not found
make[2]: *** [/tmp/vmware-root/modules/vmmon-only/linux/driver.o] Error 127
make[1]: *** [_module_/tmp/vmware-root/modules/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmmon-only'

[SIZE=3][COLOR=Navy]i have read the official help documents
[https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation)
it seems like a kind of kernal problem, so i follow the below guide[/COLOR][/SIZE][COLOR=DarkRed]
[/COLOR]
**Configuration aborts when updating from Feisty to Hardy (or any system running the 2.6.24-2 kernel)**

 When  using the 2.6.24-2 kernel, a patch must be applied to get the vmware  modules to compile.  This applies to you if vmware-config.pl crashes  with the message  
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-2-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'

Unable to build the vmmon module.The solution is to download a patch from [http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz](http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz) that will correct this issue.  Extract the files, then run  
sudo ./runme.pl

[SIZE=3][COLOR=Navy]then another problem comes up too
[/COLOR][/SIZE]
shawn@shawn-nb:~/Downloads/vmware-any-any-update115$ sudo ./runme.pl
Unable to open the installer database /etc/vmware/locations in read-mode.

Execution aborted.

[SIZE=3][COLOR=Navy]anyone knows how to fix up the kind of problem[/COLOR][/SIZE] :confused:
[SIZE=3][COLOR=Navy]coz I'm a linux newbie, try to compare vmware workstation 7 between 
windows platform (windows 7) and linux platform (ubuntu 10.04)[/COLOR][/SIZE]
[SIZE=3][COLOR=Navy]hope someone in experienced may share or offer the informations to solve the problems[/COLOR][/SIZE][SIZE=3][COLOR=Navy]
thanks anyway [/COLOR][/SIZE]:)

---

### Post by e79 on 2010-09-05
I am not sure but this... :

make[1]: gcc: Command not found
make[2]: gcc: Command not found

...leads me to think you do not have the gcc compiler needed for building your new kernel module in order to install it properly...If I recall, the version 4.1 of gcc should do the tricks...  (sudo apt-get install gcc-4.1). Then retry the installation and see if it works.

---

### Post by TJet1.8 on 2010-09-12
> **e79 said:**
> I am not sure but this... :

make[1]: gcc: Command not found
make[2]: gcc: Command not found

...leads me to think you do not have the gcc compiler needed for building your new kernel module in order to install it properly...If I recall, the version 4.1 of gcc should do the tricks...  (sudo apt-get install gcc-4.1). Then retry the installation and see if it works.

Actually...if not installed already, you need to install the "complete" build environment:

sudo apt-get install gcc build-essential linux-headers-$(uname -r) dkms

Good luck :)

---


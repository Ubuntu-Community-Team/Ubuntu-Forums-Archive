---
title: "Ubuntu 23.10 fails to install VBoxLinuxadditions"
date: 2023-10-17
forum: Virtualisation
---

### Post by rokaburra on 2023-10-17
Ubuntu 23.10 fails to install Virtualbox Linuxaddditions (VBox 7.0.10 on Ubuntu 22.04.3).

 vboxadd-setup.log:
Building the main Guest Additions 7.0.10 module for kernel 6.5.0-9-generic.
Building the shared folder support module.
Building the graphics driver module.
Error building the module.  Build output follows.
make V=1 CONFIG_MODULE_SIG= CONFIG_MODULE_SIG_ALL= -C /lib/modules/6.5.0-9-generic/build M=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 -j2 modules
make[1]: warning: -j2 forced in submake: resetting jobserver mode.
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: x86_64-linux-gnu-gcc-13 (Ubuntu 13.2.0-4ubuntu3) 13.2.0
  You are using:           gcc-13 (Ubuntu 13.2.0-4ubuntu3) 13.2.0

Prereqs installed: normally gcc make would do. Not anymore. Tried also build-essentials, dkms. Same errors in log.

How to get x86_64-linux-gnu-gcc-13 (Ubuntu 13.2.0-4ubuntu3) 13.2.0?

---

### Post by TheFu on 2023-10-17
VirtualBox is from Oracle. Maybe better help would come from them for something so very, very, new?

OTOH, if you'd like to use the built-in hypervisor that is part of the Linux kernel, KVM/QEMU, I think you'll be relatively happy. There aren't an guest additions when you go native. I installed 23.10 into a KVM VM a few days ago and it worked well. My KVM host system run 20.04.  copy/paste worked fine between the host and the guest system, immediately. Just sayin.

---

### Post by MAFoElffen on 2023-10-17
Where and hw are you trying to install the VBox guest additions? Have you installed it before?

Did you follow similar instructions to this? [https://help.ubuntu.com/community/VirtualBox/GuestAdditions](https://help.ubuntu.com/community/VirtualBox/GuestAdditions)

---

### Post by rokaburra on 2023-10-17
Got the answer on [https://forums.virtualbox.org/viewtopic.php?t=110327](https://forums.virtualbox.org/viewtopic.php?t=110327). Upgrading to virtualbox 7.0.7.12 with better support for kernel 6.5 did the trick. Thnx all.

---


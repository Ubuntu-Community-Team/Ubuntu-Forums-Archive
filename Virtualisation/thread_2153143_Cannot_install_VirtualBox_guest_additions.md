---
title: "Cannot install VirtualBox guest additions"
date: 2013-06-10
forum: Virtualisation
---

### Post by LeoTheSecond on 2013-06-10
Hi,


I'm using the following constellation:
Host: Win 8 Pro 64 Bit
Guest: Lubuntu 13.04 64 Bit
VirtualBox 4.2.12


If I try to install the guest additions I get the following messages:


leo@leo-VirtualBox:/media/leo/VBOXADDITIONS_4.2.12_84980$ sudo sh ./VBoxLinuxAdditions.run
Verifying archive integrity... All good.
Uncompressing VirtualBox 4.2.12 Guest Additions for Linux............
VirtualBox Guest Additions installerCopying additional installer modules ...
Installing additional modules ...
Removing existing VirtualBox non-DKMS kernel modules ...done.
Building the VirtualBox Guest Additions kernel modules
The make utility was not found. If the following module compilation fails then this could be the reason and you should try installing it.
The gcc utility was not found. If the following module compilation fails then this could be the reason and you should try installing it.
Building the main Guest Additions module ...fail! (Look at /var/log/vboxadd-install.log to find out what went wrong)
Doing non-kernel setup of the Guest Additions ...done.
Installing the Window System driversInstalling X.Org Server 1.13 modules ...done.
Setting up the Window System to use the Guest Additions ...done.
You may need to restart the hal service and the Window System (or just restartthe guest system) to enable the Guest Additions.
Installing graphics libraries and desktop services components ...done.


Content of /var/log/vboxadd-install.log:
/opt/VBoxGuestAdditions-4.2.12/src/vboxguest-4.2.12/build_in_tmp: 62: /opt/VBoxGuestAdditions-4.2.12/src/vboxguest-4.2.12/build_in_tmp: make: not found
Creating user for the Guest Additions.
Creating udev rule for the Guest Additions kernel module.


Does anybody know what I can do? Note that I cannot go online within Lubuntu.

---

### Post by eestet75 on 2013-06-10
You need to install make and gcc. Use another computer to get the packages.

---

### Post by LeoTheSecond on 2013-06-11
I did the following steps:

- download make_3.81-8.2ubuntu2_amd64.deb and gcc_4.7.3-1ubuntu10_amd64.deb
- open GDebi Package Installer
- install make_3.81-8.2ubuntu2_amd64.deb
- install gcc_4.7.3-1ubuntu10_amd64.deb, BUT BEFORE (because of dependency errors) install in this order:
binutils_2.23.2-2ubuntu1_amd64.deb
libgomp1_4.7.3-1ubuntu1_amd64.deb
libitm1_4.7.3-1ubuntu1_amd64.deb
libgcc-4.7-dev_4.7.3-1ubuntu1_amd64.deb
gcc-4.7_4.7.3-1ubuntu1_amd64.deb

Now guest additions are working perfectly, thanks, eestet75.

---

### Post by eestet75 on 2013-06-11
You're welcome. BTW, mark this thread as solved.

---

### Post by gordintoronto on 2013-06-11
Actually, for the version of VirtualBox you have, you should install the Extension Pack, not the guest additions. You can do it from within Virtualbox, or from the VirtualBox web site.

---

### Post by LeoTheSecond on 2013-06-12
Thanks, gordintoronto, Extension Pack Oracle_VM_VirtualBox_Extension_Pack-4.2.12-84980.vbox-extpack has been installed before.

---

### Post by 2Stoned on 2013-06-17
I know this thread has been solved but this worked for me a while ago. Download with synaptic : make, gcc, virtualbox-guest-x11, virtualbox-guest-dkms, virtualbox-guest-utils

---

### Post by dragonfly41 on 2013-06-17
Note that I found that VirtualBox version 4.2.12 is not in the Synaptic repo and I had to do a manual installation of version 4.2.12.

---


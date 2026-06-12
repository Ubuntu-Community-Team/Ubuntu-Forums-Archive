---
title: "Grub"
date: 2019-03-08
forum: Ubuntu Development Version
---

### Post by P-I H on 2019-03-08
Does anybody know the rational for Grub to change boot device in BIOS?
I have three ssd disks one with Disco Dingo, one with Ubuntu 18.10 and one with Ubuntu 18.04 LTS.
When Grub is updated in Disco Dingo it changes boot device in BIOS.
My view is that the owner of the system, shall have control of the boot device, as you have already made the decision in BIOS.
Especially in case you are using the development version and want to totally separate the different OS-versions.
During early development of the new Ubuntu version this behaviour may lead to disastar.

---

### Post by oldfred on 2019-03-08
With BIOS, you used to be able to control which drive grub was installed into and it had an internal setting for which drive.

But with UEFI grub always installs to first ESP, usually sda or first NVMe device.

We have filed bug reports for years:
       Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488)
EFI doesn't show multiple installs of the same operating system 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1561712](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1561712)
Debian has option to install grub to bootx64.efi
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=746662](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=746662)
grub-efi-amd64  grub2/force_efi_extra_removable boolean true

---


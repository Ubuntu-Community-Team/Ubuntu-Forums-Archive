---
title: "problems with new pc - windows 8 and 14.10"
date: 2014-10-11
forum: Ubuntu Development Version
---

### Post by Peter09 on 2014-10-11
Just bought a new PC it has a disk with windows 8 installed. I put a second disk (SSD) in for 14.10. I have been selecting them by choosing the boot device (F12). Great - however when 14.10 installed a new Kernel it decided - without asking  - to use grub to generate a boot menu. Seemed OK. Next time I selected windows from the grub menu it pops up telling me that there was a problem - and outside of my control again, it writes the Windows boot loader over everything so that I get no options to boot Ubuntu. So - its back into the bios to change the order of boot device ( which windows had changed). 

So back to normal - except that every kernel upgrade is going to be a problem.

Any thoughts?

---

### Post by oldfred on 2014-10-11
Are both systems installed in UEFI boot mode? Or both in BIOS boot mode?
If not you only can boot from f12 one time boot key or UEFI/BIOS as UEFI and BIOS are not compatible.

Post link to summary report from this to see details of installs:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grahammechanical on 2014-10-13
This is not an issue peculiar to 14.10. Even though you are using 14.10 this would happen if you were using 12.04 or 14.04. And you will see posts about it in other sections of the forum. 

Whenever we get an update to the Linux kernel then update-grub is run. If that did not happen then we would still be loading the previous kernel and not using the latest kernel. And by the way, the development version gets lots of kernel updates during the 26 week development period.

This problem, it seems to me, is caused by Windows behaving in its usual self-centred way. That is life with a Windows machine.

Regards.

---

### Post by ventrical on 2014-10-13
> **Peter09 said:**
> Just bought a new PC it has a disk with windows 8 installed. I put a second disk (SSD) in for 14.10. I have been selecting them by choosing the boot device (F12). Great - however when 14.10 installed a new Kernel it decided - without asking  - to use grub to generate a boot menu. Seemed OK. Next time I selected windows from the grub menu it pops up telling me that there was a problem - and outside of my control again, it writes the Windows boot loader over everything so that I get no options to boot Ubuntu. So - its back into the bios to change the order of boot device ( which windows had changed). 

So back to normal - except that every kernel upgrade is going to be a problem.

Any thoughts?

 I have similar machines also. Two with SSD disks. When I boot those machines I disconnect the regular  SATA hdd. It works fine for me. If I am running Windows 8 partition or ubuntu partition on regular hdd and install vis a vera I will always get boot error in BIOs mode. That is where Grub Rescue CD (iso) saves the day. It will restore either missing Windows 7/8 bootloader and/or Ubuntu kernel on same disk.

---


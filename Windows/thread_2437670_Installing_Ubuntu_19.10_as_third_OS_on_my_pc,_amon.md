---
title: "Installing Ubuntu 19.10 as third OS on my pc, among Windows 10 and Ubuntu 18.04"
date: 2020-02-27
forum: Windows
---

### Post by maxxiev on 2020-02-27
Hey,

I had a perfectly working dual-boot, but last week I plugged in an SSD of 250GB to install Ubuntu 19.10 on (Among existing Windows 10 (128GB SSD) and Ubuntu 18.04 (800GB-ish) installation). Unfortunately, it did not turn out to be as easy as expected. The problem is as follows.

Whenever I boot my system, I only get to choose between Ubuntu 18.04 and my new Ubuntu 19.10 but no windows is found by the GRUB2 bootloader. To solve the problem I ran the boot-repair tool on my new system which gave me the following information dump:

[https://paste.ubuntu.com/p/8r4rpB5SVv/](https://paste.ubuntu.com/p/8r4rpB5SVv/)

Focussing on the repair suggested by boot-repair I would have to create a >1MB, unformatted filesystem with bios_grub flag. However, this gives me two problems as well. Assuming it is desired that I created this partition on my new drive, I am unable to adjust the partitions on this active OS (obviously... I suppose). The second problem is that I am unable to flag an unformatted filesystem, the program does not allow me to manage these flags.

If any information is missing, please let me know and I will update my post. 

I hope someone is able to help me with this problem.

Thanks!

---

### Post by yancek on 2020-02-27
You installed 19.10 in UEFI mode while windows on sda is a Legacy/CSM install and 18.04 is also a Legacy install.  Simplest thing to do is to have 18.04 boot as it should then boot both windows and 19.10.  Set the sda drive to first boot priority as it has Grub in the MBR which hopefully, points to 18.04.  An EFI install of Linux Grub will not boot a Legacy windows.  Other options and explanations as to why you see this behavior are explained in the Ubuntu documentation at the link below. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---


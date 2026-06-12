---
title: "Grub issue with HDD"
date: 2019-01-16
forum: Ubuntu Development Version
---

### Post by mariog01 on 2019-01-16
Hi everyone. I have one SSD as main disk, using Ubuntu budgie 19.04 and one HDD which I've formatted to ext4 to store data. The HDD had installed Ubuntu 18.04 and after formatting it, keeps showing up in grub but obviously doesn't boot.  Anyone could help me removing it so it doesn't show up anymore? 
The path to SSD is /dev/sdb and for HDD is /dev/sda, if that had anything to do. Thanks in advance!

---

### Post by dino99 on 2019-01-16
With multiple installs with their own grub, one is the  'master' which is used to update other OSs with new kernel(s).

---

### Post by oldfred on 2019-01-16
Your 19.04 is not yet released. While I have it installed, I use as main working install the most current LTS version.

Are installs UEFI or BIOS?

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not post full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mariog01 on 2019-01-17
So, how can I set the 'master' grub the SSD one?

---


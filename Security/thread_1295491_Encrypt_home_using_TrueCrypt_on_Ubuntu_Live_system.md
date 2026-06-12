---
title: "Encrypt home using TrueCrypt on Ubuntu Live system (USB)"
date: 2009-10-19
forum: Security
---

### Post by stbe on 2009-10-19
related: [http://ubuntuforums.org/showthread.php?t=1097888](http://ubuntuforums.org/showthread.php?t=1097888)

I installed 9.04 as live system on USB. I know that TrueCrypt cannot be used for pre-boot on Linux. I just need my home directory (or /home) encrypted. It is ok to enter the password during boot

My thoughts:
- How/where should I create the encrypted partition or the container file? Currently I can only install Ubuntu using UNetbootin using Windows so the whole USB driver is only 1 partition (FAT16). I personally would prefere a simle container file within this FAT16 partition.
- How can I start/mount /home before getting graphical environment? Is /etc/init.d/rc.local a good place or /etc/fstab? Has anybody done this before and can give some hints or config lines to use?

---


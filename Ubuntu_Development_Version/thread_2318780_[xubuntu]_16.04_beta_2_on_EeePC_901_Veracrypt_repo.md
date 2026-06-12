---
title: "[xubuntu] 16.04 beta 2 on EeePC 901: Veracrypt reports error"
date: 2016-03-29
forum: Ubuntu Development Version
---

### Post by GoetzKluge on 2016-03-29
Dear developers, you may want to test how VeraCrypt works with _ubuntu. It doesn't find something when trying to mount containers. (Sorry, I presently don't have my notes at hand, so I cannot describe the "something").

By the way: This is how I used the flash memory in the EeePC 901:

[LIST]
[*]Internal 4G drive: 1 EXT4 partition assigned to "/"
[*]Internal 8G drive: 1 EXT4 partition assigned to "/usr" and one 1G swap partition (sdb5 in an extended partition).
(If I would use the install where it is left to Ubuntu how to partition the disk sda, the swap partition also would be installed on sda5 in the extended partition sda4.)
[*]64G SD memory: 1 EXT2 (for speed (I know the risks, but I don't do serious work with that old EeePC)) assigned to "/home" without encryption.
[/LIST]

---

### Post by GoetzKluge on 2016-03-29
I could solve the problem: **VeraCrypt needs dmsetup** (low level logical volume management). I installed dmsetup and after rebooting the EeePC, VeraCrypt worked well.

---


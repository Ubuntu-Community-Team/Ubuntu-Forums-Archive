---
title: "Error Installing Windows 7 x64 on Secondary HDD"
date: 2014-08-01
forum: Windows
---

### Post by ians0mniac on 2014-08-01
[ATTACH=CONFIG]255182[/ATTACH]
Here's my problem:
I'm attempting to install Windows 7 x64 alongside Ubuntu 14.04. I have 2 HDD's in my computer, one containing my installation of Ubuntu 14.04, the other...unallocated. I am attempting to install Windows 7 x64 to the empty HDD. So far, I have attempted formatting the drive to NTFS and installing it, as well as deleting all partitions from the drive and installing it to the unallocated space. When I tried the latter, the Windows 7 installation utility allowed me to select the empty drive, click 'New' to create an NTFS partition, and select 'Next'. The problem is, when I hit 'Next', I receive an error saying that the setup utility was unable to install Windows to this partition. Now, I have come to you, asking: What do?

---

### Post by oldfred on 2014-08-01
Did you change BIOS to boot from empty drive?
Windows need to install boot loader or boot partition on drive set as boot drive in BIOS. It may try to write the normally hidden 100MB boot partition to the Linux drive.
Also the NTFS partition must be primary and have the boot flag, if installing to one partition. Drive must not be gpt partitioned unless installing in UEFI mode.
Generally Windows likes to be first drive and first partition, but that is not required.

Some suggest disconnecting Ubuntu drive and just install Windows. Then keep Window drive in first SATA port on drive and plug in Ubuntu. Since Ubuntu uses UUID, it should still boot even though device sda has changed to sdb.
Then run this in Ubuntu to update internal settings and find Windows.
sudo update-grub

---

### Post by ians0mniac on 2014-08-01
I'll try removing the HDD and choosing to boot from the empty one. One question, though:
> **oldfred said:**
> Did you change BIOS to boot from empty drive? Also the NTFS partition must be primary and have the boot flag, if installing to one partition. Drive must not be gpt partitioned unless installing in UEFI mode.
It seems as though you're saying two different things here: don't partition, and do. I have tried NTFS w/ boot flag before, but I'll try again with only one HDD, to see what happens. Thanks.

---

### Post by oldfred on 2014-08-01
You can do either, partition in advance or have blank drive.
Blank drive gives the two partition install with a separate boot partition, so you can encrypt the main install or possible boot into the recovery mode when main install is broken. Better to have Windows repair CD or flash drive.
But if BIOS set to boot from Linux drive it may be trying to put 100MB boot partition on Linux drive.

Even if 2nd drive is NTFS, primary & has boot flag, if BIOS is booting from Linux drive it may still be trying to install to that drive not the correct one.

Either blank drive or formatted one partition should work. If BIOS thinks blank drive is hard drive boot drive during install.

---

### Post by ians0mniac on 2014-08-01
Thanks.

---


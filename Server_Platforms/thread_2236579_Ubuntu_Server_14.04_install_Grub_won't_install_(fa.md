---
title: "Ubuntu Server 14.04 install Grub won't install (fatal error) in Raid 1 setup"
date: 2014-07-27
forum: Server Platforms
---

### Post by excetara2 on 2014-07-27
I was installing Ubuntu Server 14.04 and made a raid 1 system with two identical root drives. Then I configured raid 1 for the two drives and installed there. When I got to the step to install grub it threw a fatal error. The step looked right as it was installing grub to both /dev/sda and /dev/sdb. What is the best way to fix this or can I look at what the error was?

---

### Post by oldfred on 2014-07-27
With RAID you do not install to a drive like sda but to a /mapper which is your RAID. And not to a partition in your RAID.

Depending on type of RAID you may need dmraid or mdadm drivers.

       [http://ubuntuforums.org/showthread.php?t=2022679](http://ubuntuforums.org/showthread.php?t=2022679)
"fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0


 Elimination of Alternative installer for 12.10 and no RAID support directly for Desktop.
[http://ubuntuforums.org/showthread.php?t=2049021](http://ubuntuforums.org/showthread.php?t=2049021)

      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---


---
title: "Installing ubuntu 18.04 lts on dell server power edge c6145"
date: 2020-03-30
forum: Server Platforms
---

### Post by espirado on 2020-03-30
I am trying to install ubuntu 18 on a dell c6145 poweredge with 6 disks 5 2TB disks and I 6 Tb disk. The system was initially running cent os 6 with software raid 5 configurations. I did a hardware raid on the disks and partition the hardware. The install process completes with no errors but after reboot it boots the grub rescue screen. The disks are partitioned but the mounting for root,home,swap etc are not in the disks no data is written on the disks. After a couple of attemps playing with the raid it still did the same. I tried a cent os 8 disk but it does not detect the disks. Am not really sure what the problem is. Is it the raid configurations? Missing drivers ? Raid controllers ? any leads to fix this will help

---

### Post by oldfred on 2020-03-30
Moved to server sub-forum where those who know servers may be able to help.

Do not know nor use RAID, but some questions:
You say it was software RAID, but you converted to hardware RAID?
What hardware RAID is it? As then it may be a driver issue.
Or is it really fakeRAID?
Generally on the threads I have seen, most suggest mdadm software RAID as it has less dependency on specific hardware.
Or you do not have to have backup hardware RAID card.

---

### Post by espirado on 2020-04-02
The hardware controller is LSI SAS 2008 . Using software raid also fails on reboot. Is there a way i can install the os independent of the drivers. I have tried installing Ubuntu 16 and am still facing the same issue. What other options apart from changing the controller can i have to bypass the raid issue?

---


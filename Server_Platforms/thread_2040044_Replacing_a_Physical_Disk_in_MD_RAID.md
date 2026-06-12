---
title: "Replacing a Physical Disk in MD RAID"
date: 2012-08-10
forum: Server Platforms
---

### Post by chrislynch8 on 2012-08-10
Hi,

I have a server configured with two DISK setup with Software RAID 1 using mdadm. One of my disks has failed so I flagged it as failed and removed it from the Array. I then shutdown the PC to add a new disk, but when I have the new disk connected the server will not boot. I get GRUB error 22, but when I disconnect the new disk and leave the second disk in it boots find.

The Disk that failed was HDD0 which was originally sda as far as Ubuntu was concerned. Now with the HDD1 connected Ubuntu boots and this disk shows as sda (which is OK as its the only disk now). When I check the RAID status mdadm -D /dev/md0 I can see the sda1 is the second Disk of the array with the first one removed.

How do I get Ubuntu to boot to HDD1 when a new blank disk is connected to HDD0?


----SOLVED----

I actually had to connect the original HDD1 to SATA0 and the new disk to SATA1 and the server booted, I could then replicate the partitions adn readd the new disk to RAID.

So it look like the following

HDD0 -> /dev/sda
HDD1 -> /dev/sdb

/dev/md0 -> [0] -> /dev/sdb1 : [1] -> /dev/sda1
/dev/md1 -> [0] -> /dev/sdb2 : [1] -> /dev/sda2

Rgds
Chris

---

### Post by bakegoodz on 2012-08-11
That makes sense, the computer always boots from primary drive, either first SATA port or can be set in the BIOS too. It needs the boot manager (grub) and enough system to bring up mdadm. Some find putting RAID in essential mount point best for their needs like for /var on a web server. My desktop has 1 SSD for / and a MD RAID 1 for /home It would be a minor inconvenience to setup my root drive again.

---


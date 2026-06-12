---
title: "Ubuntu Server 12.04 - RAID/mdadm question"
date: 2014-01-24
forum: Server Platforms
---

### Post by daz555 on 2014-01-24
Hi,

I am running a 12.04 64 bit install of Ubuntu server. Below is my disk config from fstab:

/dev/sda2    /mnt/sata1    ext4    defaults    0    0
/dev/sdb2    /mnt/sata2    ext4    defaults    0    0
/dev/md0    /mnt/raid1    ext4    defaults    0    0

I also PREVIOUSLY had the following set in /etc/mdadm/mdadm.conf:

ARRAY /dev/md0 UUID=6467222a:e0e11bbc:e368bf24:bd0fce41
DEVICE /dev/sda1 /dev/sdb1
ARRAY /dev/md0 level=raid1 devices=/dev/sda1,/dev/sdb1

In summary I have 2 3TB HDDS with 2 partitions on each. 1st partition on  each is part of a RAID1 array and the 2nd partition on each disk is  just a standard volume.

Now, after some recent updates and a subsequent reboot the server no  longer assembled the array on boot and I had to mount manually. I had a  feeling that the mdadm.conf might be the problem (it actually came from  my original 10.04 32bit install) so I took a backup and deleted it.

I then used mdadm --assemble --scan

....in order to get Ubuntu to assemble the array automatically - which  it did. I then mounted the volume and rebooted. All works fine.

However I'm confused - my RAID 1 partitions mount correctly on each  reboot but I do not have a mdadm.conf file. I am now utterly confused as
to where the RAID setting is configured and what is allowing it to  assemble on boot? FYI I used Webmin to mount the RAID 1 filesystem as  /mnt/raid1. It shows as clean in Webmin also.

Any ideas?

edit: I posted this earlier in the beginners section but on second thoughts it probably belongs here. Mods - should I mark it closed/solved or should it be deleted?

---

### Post by daz555 on 2014-01-26
I have now created a mdadm.conf file and placed the following in it:

ARRAY /dev/md0 UUID=6467222a:e0e11bbc:e368bf24:bd0fce41
DEVICE /dev/sda1 /dev/sdb1

It all still works - with or without the mdadm.conf file though. Hmmm.

---

### Post by rubylaser on 2014-01-26
mdadm will scan your disks automatically with or without an mdadm.conf and try to assemble them at boot.  The mdadm.conf file just ensures that it assembles correctly.  You can also run an update-initramfs -u to have it integrate any changes.

---


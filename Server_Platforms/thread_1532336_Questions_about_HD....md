---
title: "Questions about HD..."
date: 2010-07-16
forum: Server Platforms
---

### Post by unar84 on 2010-07-16
Hi all!

Is it possible that my system (Ubuntu 10.04 Server) changes "logical names" (sda,sdb,sdc,sdd) at each reboot? There is a way to lock them?

I also want to know if there is a way to associate a logical name to the serial number of a disk (to identify it phisically).


Thanks

ar

---

### Post by kemra on 2010-07-16
> **unar84 said:**
> Hi all!

Is it possible that my system (Ubuntu 10.04 Server) changes "logical names" (sda,sdb,sdc,sdd) at each reboot? There is a way to lock them?

I also want to know if there is a way to associate a logical name to the serial number of a disk (to identify it phisically).

The drive names will not change on your system and I don't know if it is even for possible for them to even do so. Taking sda for example the "sd" indicates a scsi or sata disk drive and the a indicates it is the first hard disk on the system, so for example sdb is the second scsi/sata disk on the system. This should also take care of your "naming" issue.

---

### Post by YesWeCan on 2010-07-16
My experience is different. On my 10.0.4 server 64 I have experienced letter swapping after reboot. Which caused me problems as I had created a mdadm RAID1 that scanned based on letters. I don't know why this swapping kept happening but it may have been related to dmraid sticking its nose in during boot (I had to uninstall dmraid). I also changed mdadm.conf to scan for uuids.

---


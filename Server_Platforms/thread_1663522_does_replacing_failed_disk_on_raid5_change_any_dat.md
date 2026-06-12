---
title: "does replacing failed disk on raid5 change any data on  other disks in raid?"
date: 2011-01-09
forum: Server Platforms
---

### Post by Kljuka on 2011-01-09
I've got a raid5 array of 4 disks with ubuntu 8.04 runing on it that is currently still working:
/dev/sda
/dev/sdb
/dev/sdc
/dev/sdd

Smartmontools for /dev/sdc tell that there are 9 sectors pending for reallocation:
```
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       9
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       9
```And /dev/sdd has increasing number of reallocated sectors (about 1 every couple of minutes):
```
5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       1735
```/dev/sdc has failed a coulple of times this week (but I have always sucessfully readded it to raid5) . But the increasing number of reallocated sectores on /dev/sdd concerns me even more.

I'm affraid that during removal of /dev/sdd and adding new /devs/sdd disk, raid might fall appart. That's why I would try to do it in Ubuntu Live CD:

If the raid falls appart (/dev/sdc fails) during the readding of new /dev/sdd disk, I might still remove the new /dev/sdd and return the previous one and assemble the raid with:
/dev/sda
/dev/sdb
/dev/sdd (old one that was previously removed)

Is this correct thinking? 
Does assembling Raid in Ubuntu Live and adding new disk for /dev/sdd write anything on /dev/sda, /dev/sdb and /dev/sdc in the process of adding /dev/sdd into raid5?

Thank you for your help

---

### Post by disabledaccount on 2011-01-10
You need 2 working hdd's to replace failed device, and You are right that there is a risk of corrupting data if /dev/sdc will fail during resyncing. However, sdc propably can work for a while without problems, so you have great chances to replace sdd without problems. Alternatively You can disconnect sdc and then replace sdd. If it's possible You should make backups of most important data.

I would like to see full SMART reports for those drives - because interpretation of values sometimes depends on hdd model. You should check the rason of dropping sdc from array (in logs) - as it maybe due to SATA link problem, not the drive itself.

---

### Post by rubylaser on 2011-01-10
Working with mdadm on an array whether from the livecd or your running box will preform the same changes to the array.  Meaning backup your data, and then remove /dev/sdd.

---


---
title: "3ware Online Capacity Expansion"
date: 2008-04-22
forum: Server Platforms
---

### Post by jakethecake on 2008-04-22
Hi guys

I want to expand my 2.3 TB, 7 drive, RAID6 array with another drive.

My 3ware 9650 raid card can handle OCE, Online Capacity Expansion, but I'm unsure how ubuntu/centos will react. I've got it allocated as a 100GB system drive and a 2.2TB storage drive.

I've got the 2.2TB drive formated as ext3 without a partiton table, so I don't have to care about GPT ([http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)).

gparted ([http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)) lists that it can grow ext3. Does anyone know if that works out okay, if the underlying drive size expands, will it be able to expand the partition? :)

oh, and I've got a bug, regarding packaging of 3wares raid management software. -> [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/218353](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/218353)

---

### Post by ikonia on 2009-05-12
you can expand ext3 shure as a file system no problems with what you are suggesting.

---

### Post by notanatheist on 2011-06-18
Alright, super thread digging. That's what I get for using "search" instead of creating more dead threads. 

Having done a 3Ware RAID migration over the last week my new array is a bit larger but how can I get my system to see the larger array without rebooting? I tried unmounting, then using gparted to delete the partition and rescan the disk. It doesn't see the new size though the 3Ware tools show the new size. 

Any suggestions or back to the vault with this thread?

---


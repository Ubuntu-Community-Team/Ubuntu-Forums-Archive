---
title: "Install Ubuntu Server 16.04 with ZFS"
date: 2017-06-25
forum: Server Platforms
---

### Post by symmtech on 2017-06-25
Hi,  Hoping somebody can share some advice.  I have a Dell R710 with 6 6Tb sata drives and 36 gigs of memory, and 2 processors, 1 perc 710 Raid controller. I also have a [COLOR=#333333][FONT=&quot]**IBM ServeRaid M1015 46M0861 SAS/SATA PCI-e RAID Controller LSI SAS9220-8i **[/FONT][/COLOR]card.  I am wanting to install Ubuntu 16.04 and use ZFS for storing all of my data.  I am looking for some help in devising the overall strategy.  Do I configure the drives on the raid controller?  If so, what is the best strategy. Do I use a 2 drive strategy for the OS, then install ZFS, and use the other drives to create the pool?

Thanks in advance.

Scott

---

### Post by oldfred on 2017-06-27
I do not know Servers, but moved to Sever sub-forum where those that know servers may be able to help.

But I thought I saw in some thread where certain Dell perc cards only worked with Windows, and others only with Linux.

---

### Post by Tadaen_Sylvermane on 2017-06-28
I can't speak to the hardware working in either windows or linux but I know personally I would put 2 ssds in raid 1 for the os, rest of drives in zfs raidz-1. depending on your data though. If it's a bunch of static data (i.e. pictures, movies, music. stuff that doesn't really change) zfs may not be the best choice. For my home server I'm using snapraid and wholly recommend it.

---

### Post by darkod on 2017-06-28
You said you have 6x 6TB disks. I would use any of those for the OS. That is too big to "waste". I would use any small hdd/ssd for the OS, doesn't even need to be raided unless you need this server to be highly available 24/7. I mean, if your OS disk dies you can have ubuntu server up and running in 30mins. Protection of the data is much more important, the OS can be easily reconstructed...

If you want to use ZFS for the 6x data disks I would use raid-z2. That gives you 4x 6TB = 24TB useful space and 2x redundancy (the array can keep working if 2 disks die).

I wouldn't connect any of the disks using the HW raid. Especially not if you want ZFS. ZFS needs it to control the disks which means they can't be passing through raid controller unless it is configured in pass-through mode. The IBM M1015 is very good for that, flash it to IT mode and in that case no raid function exists. The raid card will only serve to connect physically the disks. The OS sees them directly.

I don't know if you can do the same for the Dell Perc. In some cases yes, depending on the chipset it uses. Look it up...

If you want raid for the OS I would use mdadm for raid1 for the OS and then zfs raid-z2 for the data disks.

---


---
title: "Installing Ubuntu Server 14.04 on a Dell R610"
date: 2016-03-05
forum: Server Platforms
---

### Post by Keith_Beef on 2016-03-05
Since this morning, I am the happy owner of a second hand Dell R610. :)

I managed to enable the DVD rom drive and get part way into the installation, but now it is asking me to
"enter an IP address to scan for iSCSI targets"&#8230;

I don't really want to do that; I have just one disc attached, a 2.5" hot swappable SAS.

There is a bit more information I can provide, but since I don't understand quite what the questions are for, I don't know how important or relevant this is.

At "Detect disks" the installer tells me that
"one or more drives containing MDADM containers (Intel/DDF RAID) have been found" and asks if I want to activate the devices.

Then, the installer tells me that
"one or more drives containing Serial ATA RAID configurations have been found" and asks if I want to activate the devices.

It does not matter what answers I give, (I have tried Yes,Yes; Yes,No; No,Yes; No,No), I am always faced with the iSCSI question.

I found the IP address given by DHCP to the R610 and tried that&#8230; no joy.

How do I get past it?

---

### Post by Keith_Beef on 2016-03-05
Well, after reading around and finding no information that seemed helpful to my particular set of circumstances, I sat back and had a beer. Then I cooked a chicken curry for my daughter and me; we ate it and I thought for a while…

Since this was happening during "detect disks" and this was with a second hand disc drive, I thought that maybe the installer had found something on the disc that had been left over from a previous life, that the disc had been an iSCSI target and that perhaps there was some kind of partition left there, even if the data within the partitions had been wiped.

So I started a console on the server, but couldn't find any useful commands for redefining partitions, tables and files systems.

So I started Ubuntu Desktop edition as a live system, used the partition editor to completely repartition the disc, then I ran the Ubuntu Server edition installer again and this time everything worked as I expected. Less than twenty minutes later I had a working system with Apache 2 and a bunch of other good stuff up and running.

---


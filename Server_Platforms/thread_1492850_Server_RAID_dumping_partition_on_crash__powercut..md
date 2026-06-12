---
title: "Server RAID dumping partition on crash / powercut."
date: 2010-05-25
forum: Server Platforms
---

### Post by batman01 on 2010-05-25
Hi all,

Please note this a home server so this isn't drop dead urgent,  but I would be interested in peoples take on this.

Self Build AMD 64 Bit Socket 939 system running Ubuntu 8.04 64Bit Server all currently up to date.

I have a 300G native raid partition currently running on 300G and a 500G SATA drives - set up with mdadm and not using fake raid at all.

This is a bit of a tale so please bear with me.

My server began to randomly crash, once or twice a week. When it did this I would get a rash of error messages on the console pointing at SATA errors. 

Every time this happened the second partition of my raid pair /dev/sdb1 would get kicked out of the array. Not only that but an attempt to add it back into the array failed with mdadm saying there was no such partition. 

I had to delete the partition and re-create it before adding it back. (I have since found that simply re-writing the partition table with fdisk works as well.)

A bit of swapping of cables & drives etc got me to the point that either my second HD or the SATA controller was dying, so I bought another disk drive and replaced sdb as (the cheaper option and I should have had a spare anyway).

With the new HD the problem was exactly the same.

A few days after discovering this the system died dead. It turns out the SATA controller was dying, even attempting to auto detect the discs at this point would crash the BIOS, nuff said.

So, now I have a new motherboard and new sdb so hopefully no more 
crashing.

Unfortunately however, my power has been twitchier than usual of late and I have had a brownout which rebooted my server. The result was /dev/sdb1 kicked out of the raid array as degraded and requiring the partition table to be rewritten before mdadm would acknowledge its presence.

So while the cause is now different the response of the RAID array is the same; if the system unexpectedly reboots for whatever reason the second partition gets kicked out of the array.

Is this deliberate behaviour on the part of the RAID or a undocumented feature?

Cheers

Pete

P.S. Yes, yes, the UPS is on its way

---

### Post by batman01 on 2010-05-27
Wow, no one evan has an opinion? That's gotta be a first on the internet.

Well for anyone that's interested, I now find that even if I do a proper manual shutdown, the second drive gets lobbed out of the raid array.

Something appears to be seriously broken in Ubuntu Server RAID. This has was rock solid since the release of 8.04 up until about 6 months ago, now I can't reboot my server without my RAID breaking. I can only conclude that Ubuntu have broken something in an update.

Bummer.

---


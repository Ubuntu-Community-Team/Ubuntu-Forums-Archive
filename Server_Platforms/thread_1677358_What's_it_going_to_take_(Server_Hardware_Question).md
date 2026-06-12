---
title: "What's it going to take? (Server Hardware Question)"
date: 2011-01-28
forum: Server Platforms
---

### Post by garfonzo on 2011-01-28
Hey Folks:

I need advice on server hardware. This is what the server needs to do:

[LIST]
[*]Host company files (Word, Excel, PDFs, etc.) for LAN access
[*]Run an SQL server backend and run the Web based Front end. This would only be accessed by employees outside the LAN (about 5 people)
[/LIST]

Is this doable off of consumer grade hardware (like a decent desktop) or do I really need server grade hardware?

Thanks!

---

### Post by gordintoronto on 2011-01-28
How complex is the application?

If the five people will all constantly create complex on-screen pages from a multi-GB database, you might make simple consumer hardware break a sweat. More likely, an entry-level consumer system can handle things just fine - like a two-year-old core 2 duo with 4 GB of memory. Most SQL apps use less CPU than playing youtube videos....

---

### Post by CharlesA on 2011-01-28
depending on how much data processing you'll be doing, you could even get away with using an atom pc.

---

### Post by garfonzo on 2011-01-28
> **gordintoronto said:**
> How complex is the application?

If the five people will all constantly create complex on-screen pages from a multi-GB database, you might make simple consumer hardware break a sweat. 

> **CharlesA]depending on how much data processing you'll be doing, you could even get away with using an atom pc.[/QUOTE]

The data is relatively simple. Just client data, pulling up billing information, generating quotes, lots of lookups from other tables to present various information about one client, and possibly some graphs for revenue/expense numbers. It is not a complex system at this point. It is a * moderately* large database, but nowhere near a GB and I don't see it getter there soon.

[QUOTE=gordintoronto said:**
> 
a two-year-old core 2 duo with 4 GB of memory. Most SQL apps use less CPU than playing youtube videos....

That is good to know!!

Thanks for the reply

---

### Post by insane_alien on 2011-01-28
> **garfonzo said:**
> It is a * moderately* large database, but nowhere near a GB and I don't see it getter there soon.

In terms of databases thats quite tiny.

databases in multiple hundreds of gigabytes are moderately large.

and if your google anything less than 2TB is peanuts

---

### Post by SeijiSensei on 2011-01-29
> **garfonzo said:**
> Is this doable off of consumer grade hardware (like a decent desktop)

Yes, though you'll probably want to put the data on a RAID array.  You can either buy an outboard RAID controller or use Linux software RAID. I'd probably stick to RAID1 so you need only one or two additional drives. That way, you won't be putting too big a load on the power supply.

One other cheap piece of hardware to consider is an extra [exhaust fan]("http://www.newegg.com/Product/Product.aspx?Item=N82E16835106083&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-Case+Fans-_-Thermaltake-_-35106083") that sits in a PCI slot.  If you're adding drives, cooling is an important concern.

---

### Post by garfonzo on 2011-01-30
> **SeijiSensei said:**
> Yes, though you'll probably want to put the data on a RAID array.  You can either buy an outboard RAID controller or use Linux software RAID. I'd probably stick to RAID1 so you need only one or two additional drives. That way, you won't be putting too big a load on the power supply.

One other cheap piece of hardware to consider is an extra [exhaust fan]("http://www.newegg.com/Product/Product.aspx?Item=N82E16835106083&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-Case+Fans-_-Thermaltake-_-35106083") that sits in a PCI slot.  If you're adding drives, cooling is an important concern.

I agree about the cooling issue, however I'm unsure as to the why I would need a RAID 1 situation? It seems this would just add a level of complexity that is unecessary. My plan was to have two identically sized hard drives and then, every night, the data from the primary is copied to the secondary (only incremental differences). So, if I am doing this, why use RAID1?

---

### Post by SeijiSensei on 2011-01-31
Well, if you use a hardware RAID card there's hardly any configuration at all.  Even Linux software RAID is pretty simple to set up, too.  You create two equal-sized partitions on the two drives and tell mdadm to make them a RAID1. 

The first advantage I see is improved reliability.  Suppose the primary drive in your scenario goes south.  Can the people in the office continue to work?  No, you or someone else will have to switch the drives over and maybe play around with grub to get it to boot up correctly.  With RAID1, if one drive fails, the other carries on, and the users are unaffected.  mdadm can be configured to monitor the array and send an email notice if a drive fails.

Second, though I think this less important, RAID1 has much better read performance because the system can read data from both halves of the array at once.  It's a bit slower on writes, since you have to make two copies of each block, but writes are much less common than reads on most systems.

RAID is not a solution for backups, though.  You still want to be backing up those important files, preferably to an external drive or another computer in case disaster strikes.  I'd consider designing an off-site backup strategy in case the building burns down.  (I'm not kidding; disaster recovery is an important part of systems administration these days.)  I use rsync to create a remote backup over the Internet every night.

---


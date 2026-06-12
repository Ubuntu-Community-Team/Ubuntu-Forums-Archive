---
title: "Access several hard-drives under a single path"
date: 2010-09-21
forum: Server Platforms
---

### Post by Conoktra on 2010-09-21
Hello, a fellow developer and friend just recently had a massive hard-drive failure and needs extra disk space to store files.

I have a series of high-performance 20 GB SCSI hard-drives that I would like to be able to access under a single path on a rack-mounted Ubuntu 10.04 server.

I plan to access them under a single path, then create an archived file-system at that path w/ Lzma2 compression using gvfs.

I would then give my friend a limited user account with SSH access to upload to that path, where the data is then compressed and distributed across several 20 GB SCSI HD's.

**So, is there is a way to access several separate HD's under a single path?**  (Without using RAID)

Thanks beforehand. :)

---

### Post by gobbledigook on 2010-09-21
i do this using [mhddfs]("http://svn.uvw.ru/mhddfs/trunk/README"). i think a more advanced solution would be [LVM]("https://help.ubuntu.com/community/Installation#LVM%20Installation%20Guides") although i haven't used this personally

---

### Post by the_original_billq on 2010-09-21
When you say "without using RAID", I believe the answer is no.

If you want to use software RAID, I would use LVM.  Multiple physical disks can be combined into a logical volume that may be mounted at a single mount point.  The volume can be a striped (RAID 0), introduce redundancy with mirroring (RAID 1), or combine the two (RAID 1+0 or RAID 0+1).  There are other RAID levels supported and used mainly with hardware RAID controllers (for performance reasons).

LVM is clearly the way to go to accomplish what you are looking to do.  Carefully consider what happens, though, if one of those drives fails - if you are not mirroring, your entire filesystem will be toast.

Cheers,
-Bill

---

### Post by Conoktra on 2010-09-21
> **gobbledigook said:**
> i do this using [mhddfs]("http://svn.uvw.ru/mhddfs/trunk/README").
It looks like that will do the trick.

> **the_original_billq said:**
> When you say "without using RAID", I  believe the answer is no.
I may be mistaken, but I don't think there are any SCSI HD setups that use RAID, then again I had not thought of software raid.

Thank you to both of you!

---

### Post by the_original_billq on 2010-09-21
Yes, there are many, many SCSI, SAS, and SATA hardware RAID solutions:

Adaptec: [http://www.adaptec.com/en-US/products/](http://www.adaptec.com/en-US/products/)
LSI: [http://www.lsi.com/channel/products/megaraid/index.html](http://www.lsi.com/channel/products/megaraid/index.html)

(Sorry, my formatting seems broken at the moment:-()

There are also integrated RAID chassis:

[http://www.rackmountmart.com/html/rackmount03.htm](http://www.rackmountmart.com/html/rackmount03.htm)

Just google "SCSI RAID chassis" - there are many to choose from.

NOTE:  I have no affiliation with any vendor or manufacturer above...

-Bill

---

### Post by Conoktra on 2010-09-21
Software RAID works like a charm, thanks!

---

### Post by Vegan on 2010-09-21
Be careful, the software RAID is risky. Be sure to backup regularly.

---

### Post by CharlesA on 2010-09-22
> **Vegan said:**
> Be careful, the software RAID is risky. Be sure to backup regularly.

No more so then HW RAID - you can have the controller card go out, drives go out, etc. You should keep backups regardless, since RAID isn't a replacement for backups.

---

### Post by grajea01 on 2010-09-22
I'd use fuse-zfs (apt-cache search zfs, apt-cache search fuse | grep -i zfs).

I'm a Solaris guy before being a linux guy; I just love zfs ;)

ZFS in fuse seems to be quite stable, but a bit slow on writing (hey, it *is* fuse, not in-kernel), so I use it to archive stuff on volumes that I don't use much; that'd be good for you, I think.

Only two commands to learn: zpool and zfs.

Go ahead, try it. PM me if there's any need.

--Jeff

---

### Post by psusi on 2010-09-22
Yes, you WANT to use software raid for that kind of thing, but given that these are 20gb drives, they must be what?  10 years old?  Put them in the trash where they belong and go pick up a new drive that is faster and larger than all of the old junkers combined for under $100.  Not to mention, the old drives are far more likely to fail soon.  A single new drive also will be easier to manage, take up less space, less power, and make less noise.

---

### Post by the_original_billq on 2010-09-22
> **psusi said:**
> Yes, you WANT to use software raid for that kind of thing, but given that these are 20gb drives, they must be what?  10 years old?  Put them in the trash where they belong and go pick up a new drive that is faster and larger than all of the old junkers combined for under $100.  Not to mention, the old drives are far more likely to fail soon.  A single new drive also will be easier to manage, take up less space, less power, and make less noise.

The problem is that some of us (ahem...) have a stack of 15K RPM SCSI disks that are lightly used, VERY reliable (5 year warranty), just yearning to be put to use... :-)

Granted, we can go buy a ginormous SATA disk for peanuts, but stripping data across 20 15K RPM spindles SCREAMS.  If you RAID 0+1 the bunch, it will swallow any fire hose of data you care to point at it, while mirroring for redundancy. (yeah, 200G of data never sounded so loud:-)

Will it make your electric meter need a liquid cooling system?  Sure, but if you need really, really fast data access, this is the way to do it.  (look at the big SAN frames from EMC - this is what's inside.)

-Bill

---

### Post by Roasted on 2010-09-22
> **CharlesA said:**
> No more so then HW RAID - you can have the controller card go out, drives go out, etc. You should keep backups regardless, since RAID isn't a replacement for backups.

I'd like to reiterate the above by saying our hardware RAID card died in one of our file servers about 3 months ago. It was producing an ear piercing alarm sound (a feature of the card) that indicated a problem. Further testing revealed a card failure.

Backups are key. Do them often.

---

### Post by CharlesA on 2010-09-22
> **Roasted said:**
> I'd like to reiterate the above by saying our hardware RAID card died in one of our file servers about 3 months ago. It was producing an ear piercing alarm sound (a feature of the card) that indicated a problem. Further testing revealed a card failure.

Backups are key. Do them often.

Indeed. I've heard that if your card craps out, you can replace it with the exact same model of card and it'll "work," but I wouldn't chance losing data due to not being a good backup.

---

### Post by the_original_billq on 2010-09-22
> **CharlesA said:**
> Indeed. I've heard that if your card craps out, you can replace it with the exact same model of card and it'll "work," but I wouldn't chance losing data due to not being a good backup.

Absolutely.  RAID does not replace backups.

Regarding controller replacement - there is a wide margin between bargain basement controllers and the real deal.  The Dell PERC is an awesome controller, in that you can move drives from chassis to chassis with little impact.  Other controllers will not play so nicely with that procedure.  Testing is key, so you know what to expect.

...and always backup your data.

...and test your backups and restores.

-Bill

---

### Post by psusi on 2010-09-22
> **the_original_billq said:**
> The problem is that some of us (ahem...) have a stack of 15K RPM SCSI disks that are lightly used, VERY reliable (5 year warranty), just yearning to be put to use... :-)

I'm not sure what good a 5 year warranty does on a 7 year old drive?  I had the first generation scsi 15k rpm 36 gig seagate cheetah back in what?  2002?  The pair of WD 36 gig 10k rpm sata drives I got in 2006 were faster and cheaper, and the ones you can get today 2-3x faster and 10x larger.

Sure, if you have 20 of the old drives, and a pair of dual channel scsi controllers for them, you might end up with a faster system than a modern single or dual sata drive, but it seems silly to dedicate a pair of pci slots, a stack of drive bays, all the power, and all the noise for that.

---

### Post by Conoktra on 2010-09-23
> **psusi said:**
> Yes, you WANT to use software raid for that kind of thing, but given that these are 20gb drives, they must be what?  10 years old?  Put them in the trash where they belong and go pick up a new drive that is faster and larger than all of the old junkers combined for under $100.  Not to mention, the old drives are far more likely to fail soon.  A single new drive also will be easier to manage, take up less space, less power, and make less noise.

I strongly believe that if you have an existing solution that does everything you require, there is no need to produce a new solution.  Seeing as this does what I want, and for $0 dollars, I see no need to purchase anything.

And yes, my 4 rack-mount servers have been working great for the past 10 years :D. Dual Pentium III's ftw!!!

---

### Post by LightningCrash on 2010-09-23
> **Conoktra said:**
> I strongly believe that if you have an existing solution that does everything you require, there is no need to produce a new solution.  Seeing as this does what I want, and for $0 dollars, I see no need to purchase anything.

Not exactly $0 dollars.
For instance, I saw a smooooking deal on a Quad socket, dual core opteron box with 32GB of RAM. It was $400 + shipping. The problem is that it runs dual 700W power supplies. Even being conservative on usage, I would easily be paying $80/mo in electricity for just that one box.
By the end of the year I could have spent enough money to buy a brand new, power-sipping, quiet six core HP Elite workstation with 16GB of RAM.
Just food for thought.

---

### Post by Conoktra on 2010-09-23
> **LightningCrash said:**
> Not exactly $0 dollars.
For instance, I saw a smooooking deal on a Quad socket, dual core opteron box with 32GB of RAM. It was $400 + shipping. The problem is that it runs dual 700W power supplies. Even being conservative on usage, I would easily be paying $80/mo in electricity for just that one box.
By the end of the year I could have spent enough money to buy a brand new, power-sipping, quiet six core HP Elite workstation with 16GB of RAM.
Just food for thought.

Thats not an issue for me.  Based off of your $80/mo estimate, my machine will only consume about $15 dollars worth of power while my friend sorts out his HD-failure woes.

But, regardless, thank you everyone for your help/input!  It has been very beneficial, now that the issue is resolved.

---


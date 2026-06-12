---
title: "Need help with partitioning with PERC 4/SC Raid controller."
date: 2006-07-19
forum: Server Platforms
---

### Post by haaglin on 2006-07-19
Hi. 

I have a dell PowerEdge 830 with PERC 4/SC Raid controller
(PERC 4/SC single channel RAID card, 64MB cache, 1 int channels (U320)) with 2x 146GB SCSI Ultra320 (10,000rpm) 1in 68 pin Hard Drives.

I have never installed ubuntu with raid, and not the server edition. I want to have a LAMP server, but i'm not sure how to do this. In the partitioning window, it sees only one disc.
```
(SCSI (1,0,0) (sda) - 146.7 GB MegaRaid LD 0 RAID1 139G
```

is the partitioning just like if it was one disc, and can someone recommend a partition setup on this?

As of now, windows server is installed (crap :p)

---

### Post by zac1333 on 2006-07-19
The partitioning should be just as if you had one disc, assuming that your RAID controller has both drives set up in a RAID 1 array.    Assuming you have the new 6.06 disc from Ubuntu, you can choose the LAMP option and it will set it up for you.  Hope this helps.

---

### Post by bjlockie on 2007-12-19
> **zac1333 said:**
> The partitioning should be just as if you had one disc, assuming that your RAID controller has both drives set up in a RAID 1 array.    Assuming you have the new 6.06 disc from Ubuntu, you can choose the LAMP option and it will set it up for you.  Hope this helps.

Exactly, the hardware raid makes it look like one disk.

---

### Post by syadnom on 2008-01-06
i have this controller(actually, i have the 4/dc) and you have 2 options.

option 1 is the fastest
1)hit ctrl+m on bootup during the scsi bios initialization and setup the drives as you like them in raid0 or 1 or 5 or whatever.

boot the ubuntu installer and treat this as if it were a single disk.

upside:onboard processor on raid controller does all the work, has 64-128MB of cache and rocks!

downside: if your controller fails, you will have to get another perc 4 controller or possibly some other LSI controller to get the data.  you wont be able to just stick any random scsi card in without reformatting the drives.

2)get to the scsi bios and configure each drive as a stand-alon disk.  during the ubuntu install setup the md software raid system.

upside:failed controller or failed motherboard, doesnt matter, any linux machine with a scsi controller can read the disk and load the md modules to get the data off.

downsides:raid is done by your CPU, no raid cache.

__

one good thing is that these are inexpensive scsi controllers on ebay and if you did have a failed controller it could be replaced pretty easily.

i would suggest controller clustering but the SC model doesnt support it.  you may consider getting a 4/DC to get clustering, that way you can run a drive on each card and if a card fails you can just plug the drive into the other controller and be back online.  that is how im setup though i have 2x 18.1GB 15000rpm  cheetahs on each controller in raid5 and each controller has 128MB cache so this is smokin fast.  unfortunately the array is much much faster than the PCI bus it connects too.  2 of these drives can hit the 132MB limit on PCI and 4 blows it away.  time to get PCI-E or PCI-X.

---


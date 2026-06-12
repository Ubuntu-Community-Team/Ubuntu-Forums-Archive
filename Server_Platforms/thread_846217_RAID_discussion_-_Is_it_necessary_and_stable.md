---
title: "RAID discussion - Is it necessary and stable?"
date: 2008-07-01
forum: Server Platforms
---

### Post by windependence on 2008-07-01
Hello everyone,

I have been helping people here for a while and one thing has come up time after time. They all seem to want to RAID everything. Most times from the applications they are using their servers for, I don't think it's necessary and in some cases can actually be dangerous in a production environment where quick recovery is needed. What is your opinion? Can someone with Linux software RAID experience try to sell me on why I should even consider this in an enterprise situation? Are there any benefits over hardware RAID? 

I see people trashing their systems all the time with RAID and LVM or worse, a combination of the two. I like the concept of LVM and have some setups with it, but I am deathly afraid of what I will do when one of those gets corrupted. With hardware RAID if a drive fails I just pull it and stick in another drive and it automagically rebuilds - no problems. Why should I or should I not use RAID at all? Some server builds I have done with no RAID at all and just set up an LVM group with three drives and then a separate drive for backup outside of the LVM. Seems to work fine without losing space like I do with my RAID 1 or RAID 5 arrays.

Let me also give you a bit of background on myself so you don't talk to me on the n00b level. I have been in IT for over 10 years and currently work for a Fortune 500 company with worldwide operations and 1000s of servers. I also run a fairly large consulting business on the side since I only work three days a week at my "real" job. IOW, I think I know what I'm doing but lately I have begun to question the need for RAID and even the need for SCSI when SATAII drives are now hot swappable, just as fast (no flames please, the difference is very small) and a MTBF of over 300,000 hours mean they are quite reliable. Some people on this forum have eluded that software RAID is actually better than hardware RAID and that I just don't understand. If that is the case, PLEASE enlighten me.

OK, </rant off> :D

-Tim

---

### Post by artesvida on 2008-07-01
I, too, would like to be enlightened.  A while back I posted something about using hardware RAID (which I do all the time in my server room, with server-class hardware, and it's saved my bacon on a few occasions) and there were a few responses touting software RAID as superior.  I don't think it is, but I'm willing to be convinced.

---

### Post by fjgaude on 2008-07-01
Well, the enterprise still uses SCSI raid, hardware style, for just about everything that is mission critical. One advantage of hardware raid is it is usually GUI in nature and is easy to understand and use. SATA drives are used for second and third, on and offline, backup. Because of the CPUs on each SCSI drive they are faster than SATA in parallel and multitasking jobs. SATA NCQ can't compare with SCSI parallel processing, depth of cues, etc.

Now as to reliability, think... hardware raid requires an extra card pluged into a motherboard, either PCI-X or PCI-E... such cards use the MB's CPU to work with the rest of the system.

Software raid uses the same CPU and motherboard, plus controllers onboard if no cards are needed. So reliability is about the same, one way or the other, when it comes to hardware.

We come to the main issue here, usage. The problem with **mdadm** is lack of full understanding on how to use it under all conditions we come across. Setup, failures, additions, expansions, etc. We have no GUI to guide us. And if we do things in the wrong manner we are likely to get ourselves into deep trouble. We are left with studing the man pages which is a pain... we need a book written by a person who has been through it all, and shows what and how to do in each case. Until we have such a book we are left with folks messing up. Some of us here try to help when we can... it's not a perfect world.

My advise is backup twice all important data, even on raid5/6 arrays, just like the big boys do, on separate machines. Do not trust raid-drive redundancy for salvation if things go wrong. <smile>

---

### Post by windependence on 2008-07-01
> **fjgaude said:**
> Well, the enterprise still uses SCSI raid, hardware style, for just about everything that is mission critical. One advantage of hardware raid is it is usually GUI in nature and is easy to understand and use. SATA drives are used for second and third, on and offline, backup. Because of the CPUs on each SCSI drive they are faster than SATA in parallel and multitasking jobs. SATA NCQ can't compare with SCSI parallel processing, depth of cues, etc.

Yes, I use RAID with SCSI drives and SANS all day long at work but we are still using them mainly because we have them firmly in place and to change would be more expensive than the savings from the drives, so this is why I think many enterprises still use SCSI. After all, if the drive fails whether it is SCSI or SATAII, you can still replace it before another fails without loss of data. No difference here. As for speed, that seems to be up to debate among the experts. One thing they do agree on is that the speed difference is now minimal and may not matter in some situations.

In my consulting business, I have installed many rack servers with SATAII drives and enterprise class boards are now incorporating SATA into their design. Both Tyan and SuperMicro both make excellent boards with built in SATA RAID controllers. I also run several web sites on enterprise class hardware but I made the decision to use SATA over SCSI for the obvious cost savings. These are NOT hobby servers, they make me money.

> **fjgaude said:**
> Now as to reliability, think... hardware raid requires an extra card pluged into a motherboard, either PCI-X or PCI-E... such cards use the MB's CPU to work with the rest of the system.

Here, we don't agree. The cards actuall OFFLOAD the processing to the processor on the card, freeing up CPU resources. That is pretty much a known fact.

> **fjgaude said:**
> Software raid uses the same CPU and motherboard, plus controllers onboard if no cards are needed. So reliability is about the same, one way or the other, when it comes to hardware.

When it comes to hardware, yes, but if a card goes bad you replace it. If something on the MB goes bad, you are cooked.

> **fjgaude said:**
> 
We come to the main issue here, usage. The problem with **mdadm** is lack of full understanding on how to use it under all conditions we come across. Setup, failures, additions, expansions, etc. We have no GUI to guide us. And if we do things in the wrong manner we are likely to get ourselves into deep trouble. We are left with studing the man pages which is a pain... we need a book written by a person who has been through it all, and shows what and how to do in each case. Until we have such a book we are left with folks messing up. Some of us here try to help when we can... it's not a perfect world.

The problem is in a production setting I don't have time to look up man pages and Google stuff. I just need to replace the card or the drive, config it and get it back online. Even if I know the commands, what if the software RAID gets corrupted and I can't rebuild it? I never had that problem with hardware RAID. Since I use *BSD in most of my servers, I am not fearful of the CLI and the only time I use a GUI is in web interface. 

> **fjgaude said:**
> My advise is backup twice all important data, even on raid5/6 arrays, just like the big boys do, on separate machines. Do not trust raid-drive redundancy for salvation if things go wrong. <smile>

Here we agree 100% and you may have seen posts I have made about this. I see so many n00bs thinking there is no need for backup because after all - they have RAID. Nothing could be farther from the truth. RAID - in any form, is NO substitute for good backups.

BTW, thanks for the comment. Please know that in no way am I arguing with you at all, just good discussion. I know there are many more out there wondering the same thing. 

-Tim

---

### Post by TheGameAh on 2008-07-01
I'm sure you guys are much better/smarter than me, but I'll chime in.

I've got a few servers with all the configs, software RAID, hardware RAID, etc.  I've had positive and negative experiences with both.

Definitely one of the plus of software RAID is cost.  It's nice not to have that extra hardware cost.  But the learning curve was rather steep, but for me so far that was the only negative.  Hardware RAID, setup was quick and easy.  Software RAID, had to learn all about MDADM first.

As for necessity, hmm, you bring up an interesting question.  All my servers are RAIDed, but do they need to be?  I don't know.  For some or my lower-hit servers, probably not.  Wouldn't doubt I could rebuild a Debian box and restore my data from backup, just as fast as waiting for a RAID to rebuild, and the users probably wouldn't notice on certain servers either.

---

### Post by windependence on 2008-07-02
Just FYI, you can buy for example some LSI and PERC controllers on eBay for cheap. I just bought 2 brand new Perc 3 controllers for $60 each. Sure, they are old, but they work fine for SCSI RAID. You don't need the latest and greatest for that.

-Tim

---

### Post by promodus on 2008-07-02
Dedicated hardware RAID controllers can make RAID convenient.
Key word that most people ignore is Redundant. RAID 5 is great, but it's even better to have a spare(s) included in the set. If the controller detects the failure it should continue with the spare. If you have monitoring enabled you'll get the alert then you go swap the blinking drive bay and life goes on. 

RAID is no substitute for backups! RAID is meant to prevent operational failure. RAID isn't always needed, that's definitely true. Clustering and failover servers and the like. Don't forget that RAID targets the MTBF of drives, but you also have an MTBF on your controller!
Calculating reliability makes me want to fall asleep:
[http://storageadvisors.adaptec.com/2005/11/01/raid-reliability-calculations](http://storageadvisors.adaptec.com/2005/11/01/raid-reliability-calculations)

Whether to RAID or not to RAID all depends on your acceptable level of downtime (Recovery Time Objective) and your Recovery Point Objective (how much data is ok to loose?) As soon as those are factored in it gets real easy to say, yeah a few spare hard drives is peanuts to a few lost hours of time multiplied by # employees.

---

### Post by gnottage on 2008-07-02
An advantage of software RAID is that it doesn't rely on a particular hardware controller. That would allow for the times when it's the controller that stops working when there's no spare to hand to swap in. With software RAID any drive controllers will suffice, as long as the OS sees the drives.

To me, it's very usable for a small setup (home or small business) where there's not the money to get a hardware RAID card (and backup) and where the redundancy is a useful function to keep activities happening without restoring from backup should a drive go bad. For any business that needs the redundancy and has the money it's easier to throw more money at it and go with hardware solutions. So I think software RAID is ultimately a smaller niche than hardware RAID for the enterprise.

Older hardware RAID cards are available second hand, but they will statistically fail earlier, have no warranty, be harder to guarantee a replacement would work (due to hardware/firmware revisions), and not always have support the latest drives.

---

### Post by sp0nge on 2008-07-02
Thanks for the information! 

I am working with my first server as a hobby for now with the hopes of learning enough to work my way into an IT spot at work administering the server that hosts the web pages and a new application that is in the works. I'm finding every minute more about how much I really don't know! 

I think for my purposes, we'll be using RAID1 setup but I'm going to looki more into backing up on a second machine as well- I never would have thought about that! Is it necessary oto have another PC dedicated to handling the backup or is there any advantage/disadvantage to using an external hard drive?

---

### Post by windependence on 2008-07-02
> **sp0nge said:**
> Thanks for the information! 

I am working with my first server as a hobby for now with the hopes of learning enough to work my way into an IT spot at work administering the server that hosts the web pages and a new application that is in the works. I'm finding every minute more about how much I really don't know! 

I think for my purposes, we'll be using RAID1 setup but I'm going to looki more into backing up on a second machine as well- I never would have thought about that! Is it necessary oto have another PC dedicated to handling the backup or is there any advantage/disadvantage to using an external hard drive?

OK if you want to get into web server administration, you are going to find that:

1. Most enterprises use RAID 5

2. Most enterprises still backup to tape. They may do a backup to disk and then dump it to tape later on because that way the time it takes for the backup of the production machine is minimized as it is faster to backup to disk. The disk file can then be written to tape without regard to how long it will take. Tape is s l o w.

3. Most web farms are many servers clustered behind several load balancers. Any one of the web servers can be taken out of the rotation without affecting the site. The load is spread over several servers to increase response time, and create redundancy.

4. Many shops do use a dedicated backup server.

-Tim

---


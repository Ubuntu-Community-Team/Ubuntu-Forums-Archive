---
title: "RAID question ????"
date: 2009-12-14
forum: Server Platforms
---

### Post by serverCrazy on 2009-12-14
ok, I had a server with ubuntu 8.04 LTS running with 4 HDD of 1TB - Raid 10. Worked fine and smooth. However, after 3 weeks 2 of the HDD crashed (DEAD), need to exchange the disks. Now i would like to ask:

Was it something to do with linux?
Does raid 10 is good with large disk spaces?
Was it too much for linux?

I know that the answer for this can be quite dificult, but my bigest question is:

I better to have 1 server with large disks or 2 + servers with smaller disks (which will decrease the overhead for parity and so on....)?

Guys what do you think about it? Should i build it again with the same amount of HDD's or get another server and split the HDD's!! 

Any advice will be much apreciated!! Thanks in advance

---

### Post by Krupski on 2009-12-14
> **serverCrazy said:**
> ok, I had a server with ubuntu 8.04 LTS running with 4 HDD of 1TB - Raid 10. Worked fine and smooth. However, after 3 weeks 2 of the HDD crashed (DEAD), need to exchange the disks. Now i would like to ask:

Was it something to do with linux?
Does raid 10 is good with large disk spaces?
Was it too much for linux?

I know that the answer for this can be quite dificult, but my bigest question is:

I better to have 1 server with large disks or 2 + servers with smaller disks (which will decrease the overhead for parity and so on....)?

Guys what do you think about it? Should i build it again with the same amount of HDD's or get another server and split the HDD's!! 

Any advice will be much apreciated!! Thanks in advance

Regardless of whether you used software MDADM RAID or hardware RAID, it would not have "broken" your hard drives.

You must have gotten a few bad ones or maybe got a power surge or a mechanical shock (bumped the server box?).

Anyway, why not run RAID-5? You get N-1 storage (that is, number of drives-1 size).

With four 1 TB drives in a RAID-5 configuration, you get a 3 TB array with redundancy.

In fact, that's exactly what I'm running here (albeit with four 2 TB drives, RAID 5 = 6 TB of RAID storage) using Ubuntu Linux Server 9.04, 64 bit and MDADM.

Works like a charm.

(edit to add): DON'T worry about CPU overhead when running RAID-5. The bottleneck will always be the hard drives, not the CPU. When I push my server to the limit, the hard drives saturate, but the CPU never comes off it's idle clock speed.

---

### Post by Thocrun on 2009-12-14
I know hardware raid is better than software and I think RAID 10 is just for having a bunch of HDD with the same info on it so that it can be replaced in case of failure (hence RAID= Array of Independent Disks or Array of Inexpensive Disks), having the same hard drives works the best with RAID 10 I think. --hope that helps,there can be problems with different speeds and sizes of hard drives in a RAID 10 system-since every disk is transferring the same data the disks would preferably need to transfer it at the same rate.

---

### Post by Krupski on 2009-12-15
> **Thocrun said:**
> I know hardware raid is better than software...

"Hardware" RAID is a controller card with a RAID bios in it (i.e software).

"Software" RAID is software communicating with a disk controller card.

There's no difference. All RAID is "software" RAID. Disk drivers talking to a disk controller card. Samey-same.

The only functional difference is that software RAID doesn't begin operating until the appropriate driver(s) are loaded by the operating system while "hardware" RAID runs as RAID from the first moment.

There can be some tricky catch-22 situations with software RAID if the operating system in on the RAID array, but these can usually be easily worked around by putting the OS on a separate disk or by clever use of bootup "fallback" mechanisms where if one disk in the array is bad, the system will boot from the other and at least come up (degraded, but working).

For a headless stand alone file server, an ideal setup (in my opinion) is to place the operating system on a TINY disk (for example, a 4 GB compact flash solid state disk card) and use the hard drives in a data-only RAID array controlled by software RAID (i.e. MDADM in Linux).

The advantages of this setup are:

* The OS is on a low power, very fast, very reliable media that does not depend on RAID to work.
* The OS can be easily backed up or restored as a raw image using DD or other utility.
* In case of "administrator error" :) the OS can be set back to it's "last known good" configuration simply by re-imaging the compact flash card with a backup image.
* If a drive in the RAID array fails, the OS is not affected.
* If drive(s) are added to the array, the OS is not affected.


For what it's worth...

-- Roger

---

### Post by Gone fishing on 2009-12-16
seems very odd that the drives failed- my last server ran raid 1 (just two hard drives) and ran fine for three years. Next one I build will use raid 10 seems more fail safe than raid 5. 

I can only imagine that there must have been a power surge or they massively overheated or something physically damaged them.

---

### Post by CharlesA on 2009-12-16
There's nothing you could do to prevent it. Drive failures happen.

I second the idea of running RAID-5 instead of RAID-10. You get 1 TB more space that way.

Also, I figured I'd want to make a note that RAID does **not** replace backups. If your array goes tits up (2 drives fail on RAID5, and you don't have a backup, you are SOL.

---

### Post by Grenage on 2009-12-16
> "Hardware" RAID is a controller card with a RAID bios in it (i.e software).

"Software" RAID is software communicating with a disk controller card.

There's no difference. All RAID is "software" RAID. Disk drivers talking to a disk controller card. Samey-same.

That's a very loose and one-sided view.  A dedicated RAID card is far better than fake raid, and a hell of a lot more convenient than MDADM.

---

### Post by =not4prophet= on 2009-12-16
There are lots of reasons for running RAID 10 over RAID 5, including i/o performance and the RAID 5 write hole (see [http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_5_performance](http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_5_performance) ).  Either way, RAID under linux would not have been responsible for the HDD failures.

---

### Post by Krupski on 2009-12-16
> **Grenage said:**
> That's a very loose and one-sided view.  A dedicated RAID card is far better than fake raid, and a hell of a lot more convenient than MDADM.

Well... MDADM works just fine for me, and it's so simple "even a caveman can do it".

Don't know how much more "convenient" it could be... ?

---

### Post by Krupski on 2009-12-16
> **CharlesA said:**
> There's nothing you could do to prevent it. Drive failures happen.

I second the idea of running RAID-5 instead of RAID-10. You get 1 TB more space that way.

Also, I figured I'd want to make a note that RAID does **not** replace backups. If your array goes tits up (2 drives fail on RAID5, and you don't have a backup, you are SOL.

One thing that confuses me about RAID 5 is the idea of "capacity = N-1".

It's true... with three 1 TB drives one gets a 2 TB array, with four one gets a 3 TB array, etc...

Thing is, with a three drive array, the "redundancy" drive is 1/2 of the array capacity. With four drives it's only 1/3 of the capacity!

What if someone built a RAID-5 array with 10 drives! Would the array be N-1 still?

How can it work if the "redundancy" drive is now only 1/9 of the array!

How is this possible? Or, am I missing something?

-- Roger

---

### Post by serverCrazy on 2009-12-16
I also think that was not linux with damage the HDDs. Everything i can think of is: 

-Heat, because i do not have a ventilation system for the HDDs and they are all together.

-Power surge, since my server is directly plugged in a normal 240v plug, rather than a UPS or a stabilizer.

I did not drop anything on it!! and not bumped the box, so i dont know. Anyway thanks for the replies, it was helpful.

So just to finish this thread. So most of people think that is better to use RAID 5 than RAID 10, thats surprising, because RAID 10 does perform better than RAID 5, anyway, thanks very much

---

### Post by CharlesA on 2009-12-16
> **Krupski said:**
> 
What if someone built a RAID-5 array with 10 drives! Would the array be N-1 still?

How can it work if the "redundancy" drive is now only 1/9 of the array!

How is this possible? Or, am I missing something?

-- Roger

It stripes the parity across all drives. You could lose 1 drive and still be able to recover your data. With RAID-6, you can lose 2 drives and still be able to recover yer data. If you had 10 drives, I'd use RAID-6. (Even if you lose 2 drives worth of capacity) N-2, you have better fault tolerance.

---

### Post by wirelessmonkey on 2009-12-17
> **Grenage said:**
> That's a very loose and one-sided view.  A dedicated RAID card is far better than fake raid, and a hell of a lot more convenient than MDADM.

Hardware raid cannot be recreated on different hardware. So if your raid controller dies, and you don't have an identical spare, you may be SOL.  A software raid can be recreated on any device capable of running/powering the drives.

I've not seen a performance benchmark that shows that either outperforms the other significantly.

Personally, I use mdadm with partition based raids for levels 1, 0, and 10, (boot and OS)and RAID 6 for multi-terabyte storage arrays (disk-based backup).

RAID 10 has higher throughput (write access) v RAID 5/6 due to parity calculations, but read access speed should be roughly equivalent, depending on the number of disks.

And as mentioned before, RAID is absolutely, positively, without doubt, NOT A BACKUP METHOD. Don't use it as such.

WM

---

### Post by windependence on 2009-12-17
Some of you need to do some reading on how RAID works.

RAID 5 is heavily used in enterprise data centers. The more spindles you have, the better the throughput. RAID 10 is just 2 RAID 1 arrays in another RAID array. It is NOT faster at all than RAID 5, especially if there are many spindles. 

The software RAID fanboys forget that the parity calculations are done on the MPU on the card instead of in the OS. May be no problem today with the power of CPUs, but saying they are the same is NOT correct. Hardware RAID also can usually be created on different hardware if you use the same brand controller. It's a good idea to have a spare if your stuff is mission critical. 

So if you set up partition based software RAID, what happens when your drive fails? You're screwed because half your data is on one drive and half on another - not fun. Also, anyone here know mdadm commands by heart? I didn't think so, but EVERYONE can use a bios based menu like hardware controllers use right?

Running the OS on a flash drive is a great idea. We do almost all our installs like that lately. Make a copy of the card and you have a spare OS you pop in in five minutes or less.

To the OP: I think most likely cause of your failure is heat. Stacking drives is almost never a good idea. The best idea yet for me is mounting them in 5-1/4 inch bays using mount kits or better yet removable trays with fans. This dissipates heat much much better and will extend your drive life tenfold. Modern drives have such a small failure rate that I don't know why so many failed drives are reported on this forum. In enterprise situations I have never seen that many drives fail, especially all at once  I suspect some of these "failures" are nothing more than folks not knowing how to recover a drive from an improperly written MBR or a read-write error.

-Tim

---

### Post by Grenage on 2009-12-17
MDADM works fine, I have several configured here on some of our budget builds.  The performance and convenience pales in comparison to a dedicated card, but it does work ok on a box with ample CPU power.

I personally like to just rip out and replace a disk that's died, knowing the controller will take care of everything; it's a lot easier than having to answer prompts and rebuild the array myself.  I prefer the arrays to be *separate* from the OS.

**windependence** is right, you will usually have more than the one adapter.  In typical business scenarios you will have many servers with the same hardware, so you don't even need dedicated spares, just other servers that aren't very important.  It all comes at a price, but you get what you pay for.

---

### Post by Xianath on 2009-12-17
At the risk of deviating from the original topic, I just want to mention that my 12-spindle mdadm RAID6 (running on a measly Athlon 64 X2 4050e in a regular desktop motherboard) does over 160GB/sec write throughput and could probably do more with some further tweaking. Please don't write off software RAID as slow just because that used to be the case a decade or two ago.

Software RAID has a lot of advantages over hardware RAID for SMB applications. Cost, ease (yes, with the right management software, of which there are many), flexibility, hardware independence are all part of it. Hardware has its place, but mostly when money is not much of an issue.

For the record, the NAS/SAN I built for under $1000 has 9.6TB of usable storage over 12 spindles in RAID6, and its performance is listed above. The "enterprise" class solution from a major computer vendor that we use at work costs over $7000 for 6TB over 4 spindles in RAID5, and can't even saturate a single gigabit link! True, it's not an EMC, but dollar for dollar, a well built software RAID can beat most hardware solutions in the <$5000 range.

Just my 0.02 (or 196MB :) )

Cheers,
Peter

---

### Post by laluz on 2009-12-18
> **serverCrazy said:**
> I also think that was not linux with damage the HDDs. Everything i can think of is: 

-Heat, because i do not have a ventilation system for the HDDs and they are all together.

-Power surge, since my server is directly plugged in a normal 240v plug, rather than a UPS or a stabilizer.

I did not drop anything on it!! and not bumped the box, so i dont know. Anyway thanks for the replies, it was helpful.

So just to finish this thread. So most of people think that is better to use RAID 5 than RAID 10, thats surprising, because RAID 10 does perform better than RAID 5, anyway, thanks very much

How do you know your drives are dead? What are the sympthoms?

---


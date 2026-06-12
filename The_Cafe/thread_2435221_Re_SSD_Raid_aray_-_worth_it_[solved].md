---
title: "Re: SSD Raid aray - worth it? [solved]"
date: 2020-01-17
forum: The Cafe
---

### Post by bunny9000 on 2020-01-17
Hey all.

I'm thinking of migrating my lab test network from a raid 0 of two spinning hard drives to 2 SSDs.

I daily backup so I'm not too bothered if the raid dies.

I've read a bunch of topics stating it's way faster than just one SSD (I've used a lot of SSDs in the past), but wondering whether two really will give me the speed boost I'm after.

My main SSD is currently a two year old samsung evo drive.

Has anyone had good results running their raid 0 with other SSD drives. I tried a cheap kingston drive fairly recently and no surprises it ran out of cache super fast and dropped to a crawl. I still have it, but it's only fast just to boot the OS. The samsung drive can do fast, sustained writes.

Just interested to get some other peoples real world experience & maybe get some ideas of other decent SSD from people who own them.

---

### Post by TheFu on 2020-01-17
I wouldn't risk it. I lost 80% of my data doing that on spinning disks. The hassle-factor isn't worth it to me for any level of performance.  Regardless, I'd use LVM in RAID0 config, not mdadm.

If you are stuck with SATA connections, you'd be much better off switching to NVMe for 10x the performance - or more.  Definitely stay with Samsung Pro, but switch to NVMe. This may require an addon card which should be put into the fastest PCIe slot you have - probably x4.  If the motherboard has multiple NVMe slots already, then carefully read the manual to understand the limitations using them can cause.  

For example, I have a MB with 2 NVMe slots.  One is x4 and the other supports x2 speeds.  Additionally, by using the 2nd NVMe slot, 2 normal SATA ports become disabled. 
Using NVMe ports often will use a shared bus, so other addon cards will be slower.  
It is all documented in the MB manual, though not as clearly as a native English speaker might like.  
Compromises.

Whatever you do, measure the performance before and after so you don't have to go by "it feels faster." You'll have actual data and know that is it or isn't any faster.

---

### Post by bunny9000 on 2020-01-22
True, good points. I ended up getting a 500GB SSD and mixing it with a 250GB not in a raid for the hypervisor. Guess I'll see how that goes. Relegate the HDDs to storage.

---

### Post by oldfred on 2020-01-23
When I built my desktop, NVMe drives were real expensive, but I installed a M.2 SATA drive.
I just last week replaced SATA drive with a new NVMe drive.

While hdparm may not be best tool, it gives some idea of speed.

/dev/nvme0n1p2:
 Timing cached reads:   28012 MB in  1.99 seconds = 14105.04 MB/sec
Timing buffered disk reads: 7356 MB in  3.00 seconds = 2451.96 MB/sec

Hard drive now is sda.
/dev/sda8:
 Timing cached reads:   27046 MB in  1.99 seconds = 13611.89 MB/sec
 Timing buffered disk reads: 392 MB in  3.01 seconds = 130.44 MB/sec

Reads from RAM still fast so best to have lots of RAM, so data cached in RAM.

---

### Post by kevdog on 2020-01-23
I'd probably have to agree that the speed advantage of RAID0 is not so advantageous with more modern hardware such as NVME.  It's curious you're still using RAID 0.   Not saying its wrong but I just haven't heard anyone doing that in some time unless they are running in RAID 10 configuration.

---

### Post by bunny9000 on 2020-01-23
> **kevdog said:**
> I'd probably have to agree that the speed advantage of RAID0 is not so advantageous with more modern hardware such as NVME.  It's curious you're still using RAID 0.   Not saying its wrong but I just haven't heard anyone doing that in some time unless they are running in RAID 10 configuration.

Nah. Not using the RAID0 now. I just finished backing up my XCP-NG hypervisor and relegating the spinning drives to backup as I've got some SSDs coming in the post.

I was really just curious whether 2xSSDs in RAID0 would give me much of a speed bump over 1x for my lab environment and some of the internet searches seemed to suggest that it would.

Since it is lab its fairly burnable

But to be honest running 4x Windows vms in raid 0 on 72k disk was eh, doable and I'm sure that was faster than 1x spinning disk, but compared to that same setup on an SSD it's night and day. I expect it's just as fast to run 2xSSDs as jbod.

I think I'm pretty much over RAID0. 1 SSD is faster than 2x 72k drives in RAID0.

Certainly, the NVME, faster SSD format is on the wishlist, but, maybe I'll get an adapter card at some point and an SSD in RAID10 for lab was a bit too expensive for me at the moment.

---

### Post by bunny9000 on 2020-01-25
I got the numbers I was after - Which was ideally how many virtual machines can you run on SSDs vs Hard Drives. I thought it was about 4 with my hardware. Seems I was wrong.

Turns out the Hard Drive Raid0 array with 2 disks managed 4 windows virtual machines running on a dedicated hypervisor before the machines slowed down to a crawl.

With a 500GB SSD not in RAID I could run 5 to 6 windows without much slowdown on the same hypervisor. I ran out of RAM before I ran out of IO & dynamic ram :(

So, the RAID card has gone into another machine and I've setup a nice, safe RAID 1 with the Hard drives :)

EDIT - I would certainly conclude for my lab setup that RAID 0 (echoing everyone else here) that RAID 0 is certainly not worth it

---


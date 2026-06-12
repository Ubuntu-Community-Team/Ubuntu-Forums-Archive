---
title: "Remove drive from partially RAID'd system"
date: 2009-11-10
forum: Server Platforms
---

### Post by infecticide on 2009-11-10
Hey Folks,

I recently rebuilt my Ubuntu Server using 64 bit as well as software RAID.

One question before I ask my real question, is software RAID any better than the fake-raid that comes with the motherboard?   My research indicated that the risk of onboard RAID chipset failure would result in a RAID layout that could not / would not be recoverable unless I was able to come up with another motherboard with the same RAID chipset/model.

Now to the real question:

I have two of the three SATA drives in the machine setup as a RAID 1 and the other was where all my data was copied before I began this adventure.

Layout:

SDA - 500GB (RAID'd)
SDB - 250GB Backup Data
SDC - 500GB (RAID'd)

My concern is that once I remove the 250 GB drive, the drive configuration is going to change. SDC --> SDB  My question is, will the software RAID find the other half of the mirror at SDB once I remove that drive?

If not, how do I prepare it ahead of time and / or fix it?

---


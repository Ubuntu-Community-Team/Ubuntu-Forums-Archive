---
title: "Esata3 vs USB2 benchmarking"
date: 2010-04-04
forum: The Cafe
---

### Post by blueshiftoverwatch on 2010-04-04
I decided to do some Esata3 vs USB2 benchmarking this morning because I was bored. For simplicity, I put all of the values in bits as well as bytes. 1 bit is equal to 0.125 bytes.

Transferring about 4800Gb (600GB) worth of data from two 8Tb (1TB) Samsung Spinpoint F3 internal HD's (7200RPM) fake RAID0'd together with 3Gbps Sata to one 16Tb (2TB) Cavalry CAXB (Hitachi) external HD (7200RPM) using Esata3 on a computer with 64Gb (8GB) of DDR3-1333 RAM running Debian on a Phenom II X4 965BE CPU. These were the sustained speeds I achieved:

Esata3 is has a theoretical transfer speed of 3Gb/s (384MB/s) and USB2 has a theoretical transfer speed of 0.469Gb/s (60MB/s).

In reality, Esata3 transfers at about 0.430Gb/s (55MB/s). About 14% it's theoretical speed. USB2 transfers at 0.195Gb/s (25MB/s). About 41% it's theoretical speed.

So, Esata3 is only about 2x as fast as USB2 for real world purposes. Even though it's theoretical speed is 6.4x faster than USB2. But it's still well worth $5 to buy the Esata3 cable separately rather than use the USB2 cable that external HD's come with.

I'm thinking that the only way you'd actually get anywhere close to the theoretical speeds is if:
1. I was transferring using solid state instead of hard drives
-and-
2. I had as much RAM as I did data you I was transferring. The limit to how much data you can transfer sequentially is limited to the amount of RAM you have. Since the data must go from internal storage-> RAM -> external storage. However much RAM you have must be filled with all the data that is to be transferred, cleared out if the amount of data is greater than the amount of available RAM, and filled back up again. Which takes time. Trying to transfer 4800Gb (600GB) of data means that the RAM would have to be cleared out 75 times.

Having an i7 instead of a Phenom II CPU would probably also speed things up as well. Since the i7 has a RAM controller built directly into the CPU while the Phenom II has to go through the northbridge to access RAM.

But even then, I have my doubts as to whether you'd actually ever be able to reach the theoretical transfer speeds. They're probably based on some some carefully managed laboratory environment that would be next to impossible to ever implement in the real world.

Moral of the story: Esata3 saves a lot of time. So spend the extra $5 and get rid of that USB2 cable if your external HD supports it and you have an Esata port on your computer.

---

### Post by iponeverything on 2010-04-04
> **blueshiftoverwatch said:**
> I decided to do some Esata3 vs USB2 benchmarking today because I was bored. For simplicity, I put all of the values in bits as well as bytes. 1 bit is equal to 0.125 bytes.

Transferring about 4800Gb (600GB) worth of data from two 8Tb (1TB) Samsung Spinpoint F3 internal HD's (7200RPM) fake RAID0'd together with 3Gbps Sata to one 16Tb (2TB) Cavalry CAXB (Hitachi) external HD (7200RPM) using Esata3 on a computer with 64Gb (8GB) of DDR3-1333 running Debian on and Phenom II X4 965 CPU. These were the sustained speeds I achieved:

Esata3 is has a theoretical transfer speed of 3Gb/s (384MB/s) and USB2 has a theoretical transfer speed of 0.469Gb/s (60MB/s).

In reality, Esata3 transfers at about 430Gb/s (55MB/s). About 14% it's theoretical speed. USB2 transfers at 0.195Gb/s (25MB/s). About 41% it's theoretical speed.

So, Esata3 is only about 2x as fast as USB2 for real world purposes. It's still well worth $5 to buy the cable separately rather than use the USB2 cable that external HD's come with though.

I'm thinking that the only way you'd actually get anywhere close to the theoretical speeds is if:
1. You were transferring using solid state instead of hard drives
-and-
2. Had as much RAM as you did data you were transferring. The limit to how much data you can transfer sequentially is limited to the amount of RAM you have. Since the data must go from internal storage-> RAM -> external storage. However much RAM you have must be filled with all the data that is to be transferred, cleared out if the amount of data is greater than the amount of available RAM, and filled back up again. Which takes time. Trying to transfer 4800Gb (600GB) of data means that the RAM would have to be cleared out 75 times.

Having an i7 instead of a Phenom II CPU would probably also speed things up as well. Since the i7 has a RAM controller built directly into the CPU while the Phenom II has to go through the northbridge to access RAM.

Quite informative, thanks for sharing your results.

---

### Post by blueshiftoverwatch on 2010-04-04
I messed up Esata3's real transfer speed. It's 0.430Gb/s, not 430Gb/s.

---


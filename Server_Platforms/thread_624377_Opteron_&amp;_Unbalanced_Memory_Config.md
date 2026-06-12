---
title: "Opteron &amp; Unbalanced Memory Config"
date: 2007-11-26
forum: Server Platforms
---

### Post by jgcamp99 on 2007-11-26
OK, I have a couple of servers. One dead, one very much alive. The dead server had 4 sticks for a total of 8 GB of PC2700, the live one has 2 sticks for a total of 2 GB PC3200, 10 GB in total.

I have configured CPU 1 to use 4 sticks of the PC2700 for 8 GB and CPU2 to use the 2 sticks of PC3200. They run @ PC2700 speed for all memory and the bios recognizes the full 10 GB. That's the only way she'll see 10 GB, otherwise it's combinations seeing 4, 6 or 8 GB regardless of DIMM slot they go into when mixed. I played around with it until I fully understood singles, pairs or quad per processor.

On a lark, I threw Ubuntu 7.10 desktop into the cdrom and used the live cdrom operating system. Ubuntu only sees 4 GB of the 10 GB there. But it does see the 2 dual AMD Opteron Model 250's.

My first question, if I put Ubuntu server on this box, will all 10 GB be recognized ?

Another question, How does this imbalanced memory configuration effect system performance ? I don't see any hit with just piddling around, then again I'm probably no where near 4 GB, much less 10 GB of used memory. Perhaps Ubuntu 32 bit is seeing only1 stick of 2 GB for CPU1 and CPU2 is seeing both sticks of 1 GB for the other 2 GB, for the total of 4 GB ?

I am using a Tyan S2881, so each cpu has 4 DIMM slots for memory for a total of 16/32 GB depending on whatever the max the bios recognizes (2 vs 4 GB sticks). But I have seen other server motherboards (MSI's in particular) that support up to 12/24 GB in a configuration that seemed odd to me, where CPU1 had 4 DIMM slots and CPU2 had 2 slots. They even have one that has 8 slots for CPU1 and 4 for CPU2. Both boards run the same chipsets as my Tyan S2881.

At any rate, MSI seems to think a server board can run this way, so I have chosen to configure mine in such a manner that it runs the 4 DIMM's full for CPU1 and only 2 for CPU2. Unfortunately for CPU2, The 2 sticks it gets are 1 GB per stick and the CPU1 gets 8 GB on 4 sticks. 

Anyone understand how the OS might be seeing this memory configuration ? Is Ubuntu desktop capa\ble of seeing anymore than 4 GB of memory at this point ?

---

### Post by jgcamp99 on 2007-12-09
Well, no answers, so I downloaded 7.10 AMD64 version, reconfigured the working server to 8 GB, 4 GB for each cpu bank. System Monitor sees all 8 GB's. 

I dropped the old hardware from the dead server as a combo into the new server to test motherboard & cpu's. It works fine, so I'll be replacing the psu in that one and it should run fine.

---


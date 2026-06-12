---
title: "What kind of hardware should I be looking at to scale to ~20k users continually?"
date: 2011-05-04
forum: Server Platforms
---

### Post by buu700 on 2011-05-04
Let's say I'm running Apache Wave on Ubuntu Server 10.04 x86-64, and I'll have approximately 20000 active users from August to January (with many more after that time).

The network this will be hosted on is pretty decent (25/25 Mbps) and the infrastructure is good (there hasn't been a power outage in years).

---

Does $5000 seem like a reasonable amount to expect to drop on the hardware, or should I look at a larger or smaller amount?

Also, how should I treat the tradeoff between raw specs and server-grade hardware (given a limited budget)?

---

For hard drive space, I'm planning around 10 to 15 TB in software RAID 10.  
~$1300

---

As far as power, I'm thinking two PSUs (beyond wattage, is there anything specific I should look for?) and a $100 or $200 UPS for good measure.  
~$300?

---

What I'm less sure about is the CPU/RAM/mobo I should be looking at to scale like this.

One possible approach would be to arbitrarily pick something like two 12-core Opterons and 96 GB RAM then decide that sounds good,  
or I could allocate a certain amount of money toward this then just max out the specs within that bound,  
but I'd like to be reasonably scientific in my approach.

So, what kind of CPU/RAM/mobo setup would you recommend and why?

---

Also, clustering. If not for the initial system, is clustering something I should look into later (e.g. when I need to upgrade / scale up the system), or are there better ways of accomplishing that.

Clustering is something I really have no experience doing, so any advice on that would be appreciated.

---

### Post by collisionystm on 2011-05-04
> **buu700 said:**
> Let's say I'm running Apache Wave on Ubuntu Server 10.04 x86-64, and I'll have approximately 20000 active users from August to January (with many more after that time).

The network this will be hosted on is pretty decent (25/25 Mbps) and the infrastructure is good (there hasn't been a power outage in years).

---

Does $5000 seem like a reasonable amount to expect to drop on the hardware, or should I look at a larger or smaller amount?

Also, how should I treat the tradeoff between raw specs and server-grade hardware (given a limited budget)?

---

For hard drive space, I'm planning around 10 to 15 TB in software RAID 10.  
~$1300

---

As far as power, I'm thinking two PSUs (beyond wattage, is there anything specific I should look for?) and a $100 or $200 UPS for good measure.  
~$300?

---

What I'm less sure about is the CPU/RAM/mobo I should be looking at to scale like this.

One possible approach would be to arbitrarily pick something like two 12-core Opterons and 96 GB RAM then decide that sounds good,  
or I could allocate a certain amount of money toward this then just max out the specs within that bound,  
but I'd like to be reasonably scientific in my approach.

So, what kind of CPU/RAM/mobo setup would you recommend and why?

---

Also, clustering. If not for the initial system, is clustering something I should look into later (e.g. when I need to upgrade / scale up the system), or are there better ways of accomplishing that.

Clustering is something I really have no experience doing, so any advice on that would be appreciated.

I recommend you check out [www.xbyte.com](www.xbyte.com)

---

### Post by a2j on 2011-05-04
4 of these:
AMD Opteron 6174 Magny-Cours 2.2GHz 12 x 512KB L2 Cache 12MB L3 Cache Socket G34 115W 12-Core Server Processor 
on this:
TYAN S8812WGM3NR Quad Socket G34 AMD SR5690 MEB Quad AMD 8-Core/12-Core Opteron 6100 Series Processors (Magny-Cours) Server Motherboard

that should do it... :)

---


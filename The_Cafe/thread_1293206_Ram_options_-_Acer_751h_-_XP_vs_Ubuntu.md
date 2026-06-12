---
title: "Ram options - Acer 751h - XP vs Ubuntu"
date: 2009-10-16
forum: The Cafe
---

### Post by aspergerian on 2009-10-16
I'm looking at an 11.6" Acer Aspire One 751h (1) and have questions about ram. My two smaller netbooks run Hardy Heron. Apparently, the 751h has slots for two memory sticks (see 2). According to cite-2, a 2 gig limit could be achieved by having the original plus one additional 1 gig unit. Alternatively (see 2), a person might opt for a 2 gig ram chip and use only one of the 751h's two memory slots. 

Of those two arrangements, would one 2-gig ram device be faster than having two 1 gig ram devices? 

Also, is XP what is determining the 2 gig limit? I'm tempted to keep the 751h's XP and try wubi. But would a clean install of Ubuntu allow a 4 gig limit for the 751h, via 2 gig ram devices? Perhaps Ubuntu would enable 3 gig of ram (???) via the 1 gig original ram plus a 2 gig addition. 


1. Amazon offering of 751h
[http://www.amazon.com/Acer-Aspire-AO751h-1545-11-6-Inch-Netbook/dp/B002A6LN6C/ref=sr_1_1?ie=UTF8&s=electronics&qid=1255736393&sr=8-1](http://www.amazon.com/Acer-Aspire-AO751h-1545-11-6-Inch-Netbook/dp/B002A6LN6C/ref=sr_1_1?ie=UTF8&s=electronics&qid=1255736393&sr=8-1)

2. Memory upgrades for 751h
[http://www.memoryupgrade.pro/acer-memory-aspire-aspire-one-751h--116.html](http://www.memoryupgrade.pro/acer-memory-aspire-aspire-one-751h--116.html)

---

### Post by |Mitch| on 2009-10-16
32 bit XP recognises 3.3 gigs of ram max. And 2 1gig sticks will be faster because the PC can access both sticks in parallel, so your computer can (theoretically) have access to twice the RAMage as it could if you had only the single RAM stick.

It's the mother-board limiting the 2 gigs, not XP.

---

### Post by Vostrocity on 2009-10-17
Just to clarify..

- All 32-bit OSs are limited to 3-ish GB of (3.3 as Mitch says). 64-bit OSs are practically unlimited in today's sense.

- Most of today's computers use DDR2 RAM, which means you should pair them in x2 increments. Higher-end computers now use DDR3, which means you should pair them in x3 increments. Because yours is DDR2 it would be faster to have 2x1GBs than 1x2GB.

---

### Post by nathang1392 on 2009-10-17
> 

Also, is XP what is determining the 2 gig limit? 



i think that that limit is determined by the motherboard that is used. even if you did a clean install your max would still be 2 gigs, as that isnt the windows limit, but a hardware restriction.

---

### Post by aspergerian on 2009-10-17
Mitch & Vostrocity, 

Thank you.

---

### Post by Paqman on 2009-10-17
> **Vostrocity said:**
> Higher-end computers now use DDR3, which means you should pair them in x3 increments.

Er, not quite. Some high-end machines do use memory in threes, but that's because they have a triple channel memory controller, not because of DDR3. If you put DDR3 into a mobo with a normal dual-channel memory controller, you should use it in pairs.

---

### Post by Vostrocity on 2009-10-17
> **Paqman said:**
> Er, not quite. Some high-end machines do use memory in threes, but that's because they have a triple channel memory controller, not because of DDR3. If you put DDR3 into a mobo with a normal dual-channel memory controller, you should use it in pairs.

Yes, but of course if you're going to bother buying DDR3 memory you're obviously going to make sure you have a compatible motherboard before dropping the extra cash. You would also need one of those fancy new i7s..

---

### Post by Skripka on 2009-10-17
> **Vostrocity said:**
> You would also need one of those fancy new i7s..

Um.  No you don't.  Some late model LGA775 hardware take dual channel DDR3, as do AM3 CPUs to name a few.

---

### Post by Paqman on 2009-10-17
> **Vostrocity said:**
> You would also need one of those fancy new i7s..

For DDR3? No you wouldn't. There's tons of dual-channel DDR3 mobos out there. Even the spanking new i5-based machines are still dual-channel.

---

### Post by cammin on 2009-10-17
The chipset in the 751h only supports 1 memory channel. Both memory slots are on the same channel.

Just buy another 1gb stick and save yourself 15 bucks.

FYI, before getting the laptop, you might want to check the state of the Poulbuso video drivers for linux if you plan on running it on the laptop. When I was considering that laptop, video chipset support for it wasn't almost non-existent. I hear it's better now, but it's still something you should look into.

---

### Post by aspergerian on 2009-10-18
I find interesting that the 751h has 1 slot or 2 for memory modules and, regardless, 2g is the max usable ram. 

I've read some threads about "Poulbuso video drivers for linux" and will be finding out first hand about ram slots and video driver - because I took the plunge and ordered the 751h. 

I'll keep using my HP Mini 1000 running Hardy Heron while I tinker with the 751h as a dual boot XP/Ubuntu with probably 60 gig for XP and 100 for Ubuntu.

---


---
title: "so choosing new RAM."
date: 2007-03-31
forum: The Cafe
---

### Post by billdotson on 2007-03-31
I went this morning to go get another 256MB stick for my sister's PC as it was running slow and I thought that 512MB of RAM would help.  So I pulled the stick out.. it is a Samsung PC2700 Stick and I went to the store looking for another 256MB.  The only 256MB modules they had were K-Byte and while they were PC2700 I didn't know if the clock speed was 333MHz on the original.  I also was weary of buying RAM from a different manufacturer and now that I think of it I don't even know if they have the same latency.

I asked the Staples rep and he kindof scoffed at me and said "Yeah 333MHz is the standard PC2700 speed."  I have built my own PC just 6 months ago but I felt like a complete idiot.  I just bought a 2x1GB Corsair RAM package so I wasn't worrying about looking for compatibility.
So apparently, PC2700 means that the max bandwidth of that RAM is 2.7GB/s and since RAM sends 8 bytes at a time so 333Mhz * 8 = 2700.  So I guess he was right.  Something I don't understand though is that PC2700 (according to wikipedia) operates at 166MHz using DDR-333 chips.  That doesn't seem to make any sense.  Also, there is latency like CAS, RAS to CAS, RAS precharge, and RAS Activate to Precha.  I don't know what any of those are but I have heard it is often smart to have the same manufacturer, bus speed, latency timings and single-sided or double-sided.  I don't know the specs on the RAM I bought except for the PC2700 and I really don't know what single-sided or double-sided is.

Although, it seems to be working in her PC :/

---

### Post by some_random_noob on 2007-03-31
Yeah its crazy... I'm currently studying this stuff. 

Double sided means that the stick has chips soldered onto both sides instead of just one.

---

### Post by DoctorMO on 2007-03-31
If you find out a lot of information I need to incorporate and produce good detection and upgrade advisory features into my dohickey project. this means using the information from the motherboard about the maximum ram, the speed and the slot type in order to discover the best upgrade solution for a detected empty ram slot or existing ram replacement.

It would be kind of nice to take the mystery of buying new hardware upgrades out for novice users so if you can help let me know.

---

### Post by Bartender on 2007-03-31
If you're running memory in dual-channel (not necessarily the same as just two sticks - the motherboard has to support dual-channel) I've always read that you need to have identical RAM modules - timing, latency, etc.  That's why I've always bought RAM intended for dual-channel boards in those "twin" packages.

Is your sister's board a dual-channel?  If not, it's probly not so critical.  Or even if it was a dual channel board, you could probably run two unmatched sticks in the non-dual slots.  In older boards you could run PC100 and PC133 sticks together.  The total memory would just run at PC100.

---

### Post by Ahart212 on 2007-06-02
DDR sents data on the clock up and down tick so a pc2700 at 166 is measured at 166 X 2 which is how they get the 333 speed.  Double sided just means there are chips on both sides of the memory stick.  I just make sure I get all one or the other, just don't mix them.  If you mix speeds they will work but at the slowest memory stick speed.

---

### Post by LightB on 2007-06-02
Speaking of RAM, it never seems to go down in price much, unlike most of the other hardware. My other PC is a tower with damaged memory (confirmed with memtest) and I looked to replace it but there's still no such thing as real cheap DDR2. It can run with the kernel parameters of mem=325MB, reduced just under the damaged part though, if it wasn't for linux it wouldn't be usable. I don't know if windows can even do that. Regardless, it's kind of not enough memory for me so it doesn't get used.

---

### Post by mips on 2007-06-02
> **billdotson said:**
> I went this morning to go get another 256MB stick for my sister's PC as it was running slow and I thought that 512MB of RAM would help.  So I pulled the stick out.. it is a Samsung PC2700 Stick and I went to the store looking for another 256MB.  The only 256MB modules they had were K-Byte and while they were PC2700 I didn't know if the clock speed was 333MHz on the original.  I also was weary of buying RAM from a different manufacturer and now that I think of it I don't even know if they have the same latency.


What Motherboard does the computer have, Brand & Model please ???

We would be able to give you better advice if you told us this.

---

### Post by jgrabham on 2007-06-02
[www.crucial.com](www.crucial.com)

(wait, does it work in linux?)

---


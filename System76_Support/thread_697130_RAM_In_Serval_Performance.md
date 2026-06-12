---
title: "RAM In Serval Performance"
date: 2008-02-14
forum: System76 Support
---

### Post by farruinn on 2008-02-14
I've noticed that the only RAM configurations available are to have 2 RAM modules installed. Is it necessary to have two, or will it support 1 stick of 2GB for example?

I ask because I doubt I'd need more than 2 GB right now, but I would like to know if I have the option of upgrading to 4GB later on by installing only 1 stick.

---

### Post by farruinn on 2008-02-14
Ah, nevermind about the RAM, I'm going for the full 4 GB :)

However - I've found a 320 GB hard drive on Newegg. Is there any reason this size wouldn't be recognized?

Thanks

---

### Post by thomasaaron on 2008-02-15
Well, the largest hard drive I'veheard of anybody using in them is 250GB. I can't find any specs that would indicate you couldn't go higher. It should work fine.

---

### Post by asmiller-ke6seh on 2008-02-15
> **farruinn said:**
> Ah, nevermind about the RAM, I'm going for the full 4 GB :)

However - I've found a 320 GB hard drive on Newegg. Is there any reason this size wouldn't be recognized?

Thanks

When you have a Core Duo, it is best to put one RAM stick in each slot - one for each side of the Core Duo processor - for maximum performance.

And as far as the larger drive, even if Linux didn't recognize the full 320 Gb, partitioning that drive would solve the problem

Is this a replacement internal HDD for the Serval that you are looking at?

---

### Post by farruinn on 2008-02-15
Aye, I didn't think the larger drive would be a problem but wanted to ask. And yes, I plan on replacing the 60 GB drive with the 320 GB.

Thanks for the info on the RAM

---

### Post by thecomputerdoc on 2008-02-15
I have a serval performance w/gutsy 7.10. I have the Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz. I installed 4GB of memory and Gutsy only recognizes 3034MB. Apparently the only way to get it to recognize the full 4 GB's is to upgrade to 64 bit. So sorry.

---

### Post by farruinn on 2008-02-16
Is there any serious disadvantage of running 64-bit? I've been out of the loop for a couple of years, but it was my understanding you could run 32-bit alongside 64 bit?

---

### Post by Vadi on 2008-02-16
None that I know of - you can run 32bit stuff just fine (flash, java, quake wars -hum-). So yeah, go for 64bit.

It's really nice when programs that can support threading are used too, since both cpu's can be used at max (ie, when you're on a dualcore, "make -j 2" is so much faster than just "make").

---


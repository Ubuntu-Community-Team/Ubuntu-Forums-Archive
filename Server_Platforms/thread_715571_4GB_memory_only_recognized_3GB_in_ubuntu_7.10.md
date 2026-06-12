---
title: "4GB memory only recognized 3GB in ubuntu 7.10"
date: 2008-03-05
forum: Server Platforms
---

### Post by zl2k on 2008-03-05
hi, there
This question has been asked many times but all I found is conflicted answers. I put 4GB memory but the ubuntu7.10 only reported 3GB. I tried on i386 desktop, i386 server and 64bit server, all show the same result.

What I found on the net are:
1. with 32bit system, it can't handle 4GB.
2. with 32bit system + pae package, it can handle up to 4GB.
3. with 64bit system, it can handle 4GB. with pae package, it can handle upto 64GB.

I tried both i386 and 64bit ubuntu 7.10 server, both only recognize 3GB. A 64bit ubuntu server does not automatically see 4GB memory.

I am not sure how to compile the kernel with so called pae package. A detail help is highly appreciated.

My system is dell inspiron 530, intel core 2 quad, 4GB ram. The bios can see 4GB and the motherboard supports 4GB.

My question is: how can I let the system recognize the 4GB (I have another 256M on graphic card). I can configure the system to any combination of desktop/server/i386/64bit, as long as it can see all the memory.

I am not looking for yes or no, I am looking for how. Thanks for help.

zl2k

---

### Post by smileypaul on 2008-03-05
Hmm.. can't help with the how.

But the 32 bit 4Gb limitation is a a total of all memory, including page file etc, hence why you probably only see about 3.2 gigs.

I believe unless all of your hardware supports 64 bit addressing, you're basically stuck where you are..

best of luck,

---


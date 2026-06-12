---
title: "Does anyone have any idea why Windows stopped working on my dual boot?"
date: 2009-02-17
forum: The Cafe
---

### Post by gymophett on 2009-02-17
I had Windows XP on a 10gb parition and 70gb on Ubuntu partition.
All my games and everything were saved on Windows. I added 10 more gigs to make it 20gb partition last night. It was working earlier today. Then it just stopped, and I wasn't even able to mount the partition in Ubuntu to back up my game files. :/
I'm reinstalling Windows now, so can someone help?

---

### Post by SonnHalter on 2009-02-17
my only guess is that you didn't give it enough attention. 


It is very strange for that to happen if it was working before. you've had to done **something**

---

### Post by Dark Aspect on 2009-02-17
> **gymophett said:**
> I had Windows XP on a 10gb parition and 70gb on Ubuntu partition.
All my games and everything were saved on Windows. I added 10 more gigs to make it 20gb partition last night. It was working earlier today. Then it just stopped, and I wasn't even able to mount the partition in Ubuntu to back up my game files. :/
I'm reinstalling Windows now, so can someone help?

How did it stop working? Did the system simply boot into Ubuntu and ignore windows? If so the windows partition may still be there as well as your data. The windows boot loader may have been corrupted,try using [super grub]("http://www.supergrubdisk.org/") to fix the windows partition.

---

### Post by gymophett on 2009-02-17
> **Dark Aspect said:**
> How did it stop working? Did the system simply boot into Ubuntu and ignore windows? If so the windows partition may still be there as well as your data. The windows boot loader may have been corrupted,try using [super grub]("http://www.supergrubdisk.org/") to fix the windows partition.

Did all of that. It will boot into it but sticks at the welcome sign. Wouldn't let me mount taht partition in Ubuntu, and the last thing I did taht couldve caused it would have been resizing it =/

---

### Post by MikeTheC on 2009-02-17
Operating Systems Local 101 organized a strike against Linux-installed computers, citing a breakdown in labor negotiations and improper instalation of a non-union kernel.

*Figures...*

---

### Post by Grant A. on 2009-02-17
Virus?

---

### Post by Keyper7 on 2009-02-17
> **gymophett said:**
> I had Windows XP on a 10gb parition and 70gb on Ubuntu partition.
All my games and everything were saved on Windows. I added 10 more gigs to make it 20gb partition last night. It was working earlier today. Then it just stopped, and I wasn't even able to mount the partition in Ubuntu to back up my game files. :/
I'm reinstalling Windows now, so can someone help?

What did you use to add those extra 10 gigs? Did it stop working right after you added them?

Vista, for example, doesn't like when you use external tools to mess with partition sizes. XP is more friendly, but I'm not sure it's 100% friendly.

What's the message you get when you try to boot directly into Windows? Can you take a picture of it?

---

### Post by gymophett on 2009-02-17
> **Keyper7 said:**
> What did you use to add those extra 10 gigs? Did it stop working right after you added them?

Vista, for example, doesn't like when you use external tools to mess with partition sizes. XP is more friendly, but I'm not sure it's 100% friendly.

What's the message you get when you try to boot directly into Windows? Can you take a picture of it?

I've alreadye rased it and reinstalled =,/
anyway. now my ubuntu live cd wont boot!

---

### Post by gymophett on 2009-02-17
Nevermind, I got it working, the usb I had in my computer was confusing it.

---


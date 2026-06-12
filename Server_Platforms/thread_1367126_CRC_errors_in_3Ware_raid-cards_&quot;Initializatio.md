---
title: "CRC errors in 3Ware raid-cards &quot;Initialization&quot; after power outage"
date: 2009-12-29
forum: Server Platforms
---

### Post by tofagerl on 2009-12-29
So, of course we had a power outage over christmas, cause the effing UPS was down. 
I have a 4x500gb Raid-5 on a 3ware 8506, with Ubuntu 9.10, running ext3.

After a power outage the 3ware card automatically goes into "initialization" mode, which is a sort of verify, only it can't be stopped. The problem is it's been stuck at 70% for days now, and the diag command in tw_cli shows tons of crc errors like the one at the end of this post.
All disks show as OK, and I can access my data, though very slowly, and the computer is heavily IO lagged, disturbing other processes.

My question is: will the initialization ever end, or should I try to migrate that data (with current speeds, it would take a little over a week to transfer) over to a new disk and rebuild the raid?
Should I replace the disks or controller?

I don't have backups, but that's because these aren't critical data, just "good to have" data.

```

[11:05:07] [tom@bear /home/tom]$ sudo tw_cli info c6
[sudo] password for tom:

Unit  UnitType  Status         %Cmpl  Stripe  Size(GB)  Cache  AVerify  IgnECC
------------------------------------------------------------------------------
u0    RAID-5    INITIALIZING   70     64K     1397.28   ON     -        -

Port   Status           Unit   Size        Blocks        Serial
---------------------------------------------------------------
p0     OK               u0     465.76 GB   976773168     S0MUJ1NPB32425
p1     OK               u0     465.76 GB   976773168     S0MUJ1NPB32434
p2     OK               u0     465.76 GB   976773168     S0MUJ1NPB32426
p3     OK               u0     465.76 GB   976773168     S0MUJ1KLB36471

SATA CRC error 0C51
 TFR Out 00 80 80 BE 07 E0 25 
 Aport error 00 03BC9CB3 A520 
 TFR In  0C 3D C4 BE 07 E0 51

```

---

### Post by tofagerl on 2010-01-01
It's still on 70 %, days later. I am going to have to copy all data over to another drive, but who knows how long it will take.

No advice?

---

### Post by CharlesA on 2010-01-02
The CRC errors don't look good at all. How much data is on the array?

I ran into something like that with my array (different controller) where it needed to rebuild the entire array. 72 hours later, it was done.

I think the best course of action is the copy the data off and hope you don't get any errors.

---

### Post by tofagerl on 2010-01-02
Close to full of course. Murphy never rests. 
I think you're right, I'm going to try copying and hope for the best. Think I'm going to replace both the drives and the Raid-card as well, they're getting old anyway, and I don't want this to happen again.

---

### Post by CharlesA on 2010-01-02
That sounds like a good idea. Will you be using another 3Ware card?

---

### Post by tofagerl on 2010-01-02
No idea, whatever we have lying around I think. This is just a workgroup server, so we're using spare parts and whatever we can get through petty cash.

---

### Post by Vegan on 2010-01-02
Be careful with choosing a RAID card. I have used High Point cards and they are OK. They are inexpensive too.

---

### Post by CharlesA on 2010-01-02
I'm running  High-Point Tech card as well on my file server (RAID-5 array) It is working well and they have drivers for linux. :D

---


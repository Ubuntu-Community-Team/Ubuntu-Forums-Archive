---
title: "New server power supply?"
date: 2011-07-13
forum: The Cafe
---

### Post by Neutronologist on 2011-07-13
I will soon be building a computer to be my server.

The computer will consist of:

1 x cheap Intel motherboard
1 x cheap Intel CPU
1GB of DDR2 Memory
2 x 500GB 7200RPM hard drives (mirror RAID)

Will a 350 watt power supply be enough?

How could I calculate such needs?

---

### Post by 3rdalbum on 2011-07-13
It'll be enough, if it's a cheap CPU and not a Core i5 or something.

There are power supply calculators on the web - Google should be able to find you a good one.

If this is a server, I'm assuming it will be turned on 24/7 - so make sure it's a decent brand and not some unbranded one that comes with a $40 case.

---

### Post by mips on 2011-07-13
Yes that will be more than enough.

I would advice you to buy a decent PSU unit though, something from Antec or Corsair.

---

### Post by handy on 2011-07-13
Why do you want to use RAID-1?

It is the quickest way known to man to duplicate corruption.

---

### Post by Tac2 on 2011-07-13
I built myself a computer earlier this year with a Core i5 processor, 8 gigs of RAM and two 5400 RPM drives (one 1.5 TB and one 500 GB). It is powered by a Seasonic X-400 (fanless, 400 W), and I've had no problems at all regarding power. And I have a server built around the Intel D945GSEJT motherboard (it has a built-in Intel Atom N270 processor - very low power), with one 500 GB 5400 RPM drive and 2 gigs of RAM that runs off a 80 W power supply. 

So I suppose a 350 W power supply should be enough for you, and depending on your processor of choice, even less could do.

---

### Post by disabledaccount on 2011-07-13
> **handy said:**
> Why do you want to use RAID-1?

It is the quickest way known to man to duplicate corruption.
??? I've never heard one bad word about RAID1 - this the cheapest solution to provide protection against HDD failure. On the other hand it's so popular and well known only because the market is flooded with low-cost fake-raid controllers and almost every modern motherboard offers fake-raid1 functionality. It's much less known that linux md can run raid10 on 2 disks, giving better performance while keeping the same level of redundancy.

---

### Post by handy on 2011-07-13
> **tomazzi said:**
> ??? I've never heard one bad word about RAID1 - this the cheapest solution to provide protection against HDD failure. 

...

You don't see the problem?

---

### Post by Paqman on 2011-07-13
> **handy said:**
> Why do you want to use RAID-1?

It is the quickest way known to man to duplicate corruption.

Still better than a single drive though, isn't it? RAID-1 is a perfectly reasonable way of introducing redundancy into your data storage.

---

### Post by disabledaccount on 2011-07-13
If we are talking about low power home server then such level of redundancy is usually acceptable. Of course there are better solutions, but having Raid1 or 2-disks raid 10 is far more safe than single HDD. Besides, md is several classes better than any low-cost fake-raid and I can assure You that it can properly behave in critical situations, unlike most of bios-based solutions (heavily tested ;) )

---

### Post by pwnst*r on 2011-07-13
Don't go cheap with your PSU.  As mentioned Corsair makes very good ones.

---

### Post by handy on 2011-07-13
> **Paqman said:**
> Still better than a single drive though, isn't it? RAID-1 is a perfectly reasonable way of introducing redundancy into your data storage.

A waste of money, electricity & space in my opinion.

---

### Post by wizard10000 on 2011-07-13
> **tomazzi said:**
> ...It's much less known that linux md can run raid10 on 2 disks, giving better performance while keeping the same level of redundancy.

Unless you're doing transaction processing the array only has to talk faster than your network interface.  If (and it's a big if) you could get 100% utilization on a gigabit network interface the array would only have to maintain 125mb/sec to keep up.

I see a lot of sysadmins make this mistake when putting together hardware specs.  If you're doing something that has to be blindingly fast like processing cell phone transactions you'd want something like SSD RAID - or an SSD SAN.  For other backend processing like database transactions you might want a fairly fast disk subsystem, but for a file or print server the disk only has to talk faster than your NIC.

If you've got a gigabit backbone RAID10 might make sense but if the backbone is only 100Base-Tx RAID1 would give you acceptable performance without the added complexity.

---

### Post by wizard10000 on 2011-07-13
> **handy said:**
> A waste of money, electricity & space in my opinion.

Depends, at least IMO.

If the goal is high availability then yeah, RAID1 makes sense.  If the goal is to skip the requirement to back the system up then I agree completely, as **RAID is not a backup solution.**  

:D

---

### Post by Paqman on 2011-07-13
> **handy said:**
> A waste of money, electricity & space in my opinion.

What, RAID 1 or redundancy in general? I don't trust hard drives as far as I can chuck 'em, personally.

---

### Post by handy on 2011-07-13
> **Paqman said:**
> What, RAID 1 or redundancy in general? I don't trust hard drives as far as I can chuck 'em, personally.

RAID 1.

No I don't trust them either. For my home system I have a NAS for backup & optical media to backup that which I can't possibly afford to lose.

---

### Post by disabledaccount on 2011-07-14
> **wizard10000 said:**
> Unless you're doing transaction processing  the array only has to talk faster than your network interface.  If (and  it's a big if) you could get 100% utilization on a gigabit network  interface the array would only have to maintain 125mb/sec to keep up.

I see a lot of sysadmins make this mistake when putting together  hardware specs.  If you're doing something that has to be blindingly  fast like processing cell phone transactions you'd want something like  SSD RAID - or an SSD SAN.  For other backend processing like database  transactions you might want a fairly fast disk subsystem, but for a file  or print server the disk only has to talk faster than your NIC.
You're right, but I was talking about slightly better performance of cheap 2-HDD raid10 comparing to cheap 2-HDD Raid1, used in low-cost home server :)
And if You need really fast storage then raid50 of 6-10 SSDs running on high end controller can give over 1GB/s bandwidth...

> **handy said:**
> RAID 1.

No I don't trust them either. For my home system I have a NAS for backup & optical media to backup that which I can't possibly afford to lose.
Raid1/10/5/6 etc is used on every computer that is supposed to work as server. HDD redundancy is fundamental for keepeng server alive for longer time - and this nothing to trust, it's a fact.

---

### Post by mips on 2011-07-14
> **handy said:**
> ...optical media to backup that which I can't possibly afford to lose.

Copy those optical discs to fresh ones once in a while (yearly I would say). I don't trust optical media either as they go wonky with time. Store then in a cool dark place. You even get special archival optical media of higher quality from some vendors but you pay more for that & it's hard to find.

I've even had original disks (pressed in a plant) go bad, just the other day myself and a mate had this problem with PS1 discs. He dragged his old PS1 out of storage for his young one and most of the discs would not work, I checked some of mine and same thing. Luckily I had backup images for most of his discs, don't ask :D

---

### Post by handy on 2011-07-15
> **tomazzi said:**
> 
...

Raid1/10/5/6 etc is used on every computer that is supposed to work as server. HDD redundancy is fundamental for keeping server alive for longer time - and this nothing to trust, it's a fact.

RAID 10-5-6 fine. 1 is dumb. :)

---

### Post by handy on 2011-07-15
> **mips said:**
> Copy those optical discs to fresh ones once in a while (yearly I would say). I don't trust optical media either as they go wonky with time. Store then in a cool dark place. You even get special archival optical media of higher quality from some vendors but you pay more for that & it's hard to find.

I've even had original disks (pressed in a plant) go bad, just the other day myself and a mate had this problem with PS1 discs. He dragged his old PS1 out of storage for his young one and most of the discs would not work, I checked some of mine and same thing. Luckily I had backup images for most of his discs, don't ask :D

I have multiple copies on multiple brands of disk, mostly on DVD.

They are always kept in a dark draw in a room that is protected from getting direct sunlight. Apart from the ones that I used to carry in a briefcase when I used them to work on other people's Windows machines. (They are all CDs & over 5.5 years old & still good last time I had need to look.)

I've seen you offering good advice on emulators in the Games sub-forum. No need to ask. :)

---

### Post by Bandit on 2011-07-16
> **handy said:**
> You don't see the problem?

Dont think he knows about bit parity.

RAID5 with 3 drives would be better option IMHO and only cost 40 bucks more. Plus much faster and great redundancy.

---


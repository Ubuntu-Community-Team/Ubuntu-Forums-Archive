---
title: "Best raid system for my configuration"
date: 2012-06-05
forum: Server Platforms
---

### Post by doktoreas on 2012-06-05
Hello everybody,
I am going to install Ubuntu 12.04 Server Edition on a server with 24Gb of ram and 8 HD of 300 GB; the idea is to create 2 virtual machine: 1 for the DB and one for the Web Server.
I am thinking about a Raid 10 because I have also a tape back form my data and another machine for DB replication so I should be pretty safe.
A friend of mine suggested me to use 2 discs with raid 1 for the operating system and the others with raid 5 for the data. I think it's a very good solution too.

What do you think about?

Thx
L.

---

### Post by rubylaser on 2012-06-05
How much storage space do you anticipate needing? And, are you planning to use hardware or software RAID?

---

### Post by doktoreas on 2012-06-05
> **rubylaser said:**
> How much storage space do you anticipate needing? And, are you planning to use hardware or software RAID?

Hardware RAID.
With RAID 10 I can have 1.2 TB (half of full space) right?

Thx!

---

### Post by rubylaser on 2012-06-05
I would setup a base install of each and benchmark each RAID setup for your use case.  Both of the setups you mentioned would obviously allow for 900GB of storage and should be fast if you have a hardware card with a write cache. 

But, the correct answer should be the RAID10.  The 8 disk RAID10 will have nearly the same available storage space as the 6 disk RAID5, and should support around 2.5 times the IOPS of the 6 disk RAID5. (These are rough numbers, but I'm sure you'll get the idea) :)

Another potential benefit of RAID10 is that it "could" have much higher fault tolerance than RAID5.  You could lose up to 4 disks (one from each mirror) and still have a functioning array (obviously, this is a best case scenario).  Even in it's worst case, losing two disks from the same mirror, RAID10 is still as fault tolerant as RAID5.

---

### Post by rubylaser on 2012-06-05
> **doktoreas said:**
> Hardware RAID.
With RAID 10 I can have 1.2 TB (half of full space) right?

Thx!

Yes, you're actual usable space would be around 1117.59GB or 1.11TB.

---

### Post by doktoreas on 2012-06-06
Thanks for all those information. Just last question..which is the procedure for a raid 10 to increase to space available?

Thx
L.

---

### Post by rubylaser on 2012-06-06
It depends on your RAID card and if it supports it.  If you plan to expand in the future, you might be better served by a different RAID level like RAID6, so you KNOW you can lose 2 drives before you lose your whole array.

---

### Post by spynappels on 2012-06-06
Another option, if the card can support it, is to create a RAID volume now and use it as the 1st Physical Volume in a LVM setup.

When you add more disks, you can simply create another RAID volume and add it to your LVM setup as a second Physical Volume and grow your LVM partitions to use the extra space.

This does depend on whether your RAID card allows you to have multiple arrays on the one controller.

---


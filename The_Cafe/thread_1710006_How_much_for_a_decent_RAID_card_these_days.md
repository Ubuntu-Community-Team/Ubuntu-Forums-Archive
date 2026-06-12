---
title: "How much for a decent RAID card these days?"
date: 2011-03-19
forum: The Cafe
---

### Post by Cuddles McKitten on 2011-03-19
Since I have bad luck with hard drives, I was considering getting a RAID card on my next PC so I wouldn't be doing disaster recovery every time one of them decides to crap out.  Looking at Newegg, they seem to range in price from $25 to over $1000.  For the purposes of a home PC where speed isn't necessarily the main imperative, how much do I need to spend to get a card with decent RAID 10  or 0+1 capabilities?

---

### Post by handy on 2011-03-19
I don't know. 

My only input on this topic is don't use RAID-1. It is the quickest way known to man to duplicate data corruption.

Have you thought of using a lower power consumption specialised NAS device?

You can organise one of those to backup whatever, automatically, on schedule & such.

I use a Netgear ReadyNAS Duo, to keep what is important to me backed up. It is also a fantastic cheap to run torrent slave.

Anyway, I hope you solve your problem.

---

### Post by LowSky on 2011-03-19
Most motherboards support RAID right from BIOS. Why waste money on a card?

---

### Post by handy on 2011-03-19
> **LowSky said:**
> Most motherboards support RAID right from BIOS. Why waste money on a card?

If you happen to have a motherboard with on-board RAID, the problem you can face is that sometime down the track your motherboard will die, & you can have a LOT of difficulty being able to access the data in your array.

Some people have to go to great lengths to find another identical motherboard to be able to get access to their array again.

The same thing of course happens with a failed card.

Ask any data storage professional what RAID is for, they will all say that RAID is NOT for backup.

---

### Post by cariboo on 2011-03-19
Using raid, is not an excuse for not keeping good backups. Instead of setting up a raid array, get a couple of external drives and make it a habit of backing up regularly.

Do not whatever you do use fakeraid even if you motherboard has the ability to do raid, use software raid. I tried fakeraid several years ago and had nothing but problems. It was to the point where I thought I had two failing hard drives, as I was having data corruption problems.

I broke the array apart, reformatted the drives, they are still in service today, 4 years later.

---

### Post by Telengard C64 on 2011-03-19
> **handy said:**
> Ask any data storage professional what RAID is for, they will all say that RAID is NOT for backup.

Correct. RAID provides redundancy, and that is all. The one thing RAID does well is protect you from hard disk failure.

If a file is deleted or corrupted then that deletion or corruption is duplicated across the array. You still have to go through data recovery to get it back.

I think OP should consider well whether or not RAID will solve the problem he is worried about. If hard disk failure is a concern, then having RAID redundancy on an external backup device may serve well.

---

### Post by ssam on 2011-03-19
why not use software raid?

have a read of [http://linux.yyz.us/why-software-raid.html](http://linux.yyz.us/why-software-raid.html)

---

### Post by jerenept on 2011-03-19
Raid on Linux: it's Free as in ZFS :P

---

### Post by jerenept on 2011-03-19
> **handy said:**
> I don't know. 

My only input on this topic is don't use RAID-1. It is the quickest way known to man to duplicate data corruption.

Have you thought of using a lower power consumption specialised NAS device?

You can organise one of those to backup whatever, automatically, on schedule & such.

I use a Netgear ReadyNAS Duo, to keep what is important to me backed up. It is also a fantastic cheap to run torrent slave.

Anyway, I hope you solve your problem.

or and old comp with FreeNAS. Brilliant, that.

---

### Post by handy on 2011-03-19
> **jerenept said:**
> or and old comp with FreeNAS. Brilliant, that.

Yes, I agree. I ended up dumping my FreeNAS system due to the system I ran it on being too powerful & therefore a waste (in a variety of ways). I wouldn't use it as a torrent slave due to the cost of running it continually.

These are the reasons why I use the little ReadyNAS Duo. It is very cheap to run & reliable. They also have a great forum which can be helpful when you are initially setting up on Linux, or if you want to do something different with it. 

Like bypass the automatic RAID-1 when 2 drives are installed, into being 2 separate RAID-0 arrays. Extending the storage instead of wasting a perfectly good drive. :)

---


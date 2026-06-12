---
title: "slow raid"
date: 2011-02-26
forum: Server Platforms
---

### Post by PW-toXic on 2011-02-26
Hi,

I have a System with 3 raids and 11 hard drives
#1 Raid5: 6 * 1TB WD Green Power
#2 Raid1: 2 * 500GB WD Greem Power
#3 Raid1: 2 * 2TB Hitachi 24/7

Im using the raid GUI palimpsest.
read test from palimpsest
#1 212.2 MB/s average
#2 61.0 MB/s average
#3 85,0 MB/s average
i can't do the write test because it says: "the disk seems to ahve usage 'filesystem' ..."
So I try copy via file browser..
From #1 to #3 i have an average write rate of 17 MB/s (one big file)
When I do the same over GBit network, i get about 21 MB/s

Thats frustrating!

I've got an X2 4200+ which is about 50% in use (both cores) in the worst case.
I hope someone can give me some hints..
I hope this is the right Forum for this question

---

### Post by rubylaser on 2011-02-26
Some more benchmarks might be in order, but if transfers on the machine are fast, that points either a network issue, or more likely a slow file sharing protocol. What are you using? (I'm guessing SMB).  NFS is much faster than SMB.  If you have other Linux boxes, NFS is a no brainer.  If you have a mixed environment with PCs, you'd need to enable the Windows NFS services, or Client Services for UNIX depending on what version of Windows you're running.

---

### Post by PW-toXic on 2011-02-26
I have no problem with the samba speed. The problem is when i directly copy with the ubuntu file browser from raid to raid. I am not running a special ubuntu server distribution. I have a normal desktop ubuntu because I need a desktop GUI and all the other known ubuntu tools.

---

### Post by rubylaser on 2011-02-26
Sorry, I misunderstood your problem. Is it still slow from the one RAID1 array to the other RAID1 array?  That way there won't be parity calculations involved.

---


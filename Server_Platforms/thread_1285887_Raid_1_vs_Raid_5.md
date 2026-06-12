---
title: "Raid 1 vs Raid 5"
date: 2009-10-08
forum: Server Platforms
---

### Post by sarfimenez on 2009-10-08
I am thinking of implementing a safety level raid in my server, but I dont decide which  raid is better for me if  1 or 5 , someone can tell me the advantages and disadvantages for each of these raids??

For the time spent reaing my question tanks ;)

---

### Post by Cowzor on 2009-10-08
You might want to have a look at this page: [http://en.wikipedia.org/wiki/Standard_RAID_levels]("http://en.wikipedia.org/wiki/Standard_RAID_levels")

---

### Post by Lars Noodén on 2009-10-08
It gets harder and harder to find good material online.  Here is an explanation with clear diagrams:

[http://www.adaptec.com/en-US/_common/compatibility/_education/RAID_level_compar_wp.htm](http://www.adaptec.com/en-US/_common/compatibility/_education/RAID_level_compar_wp.htm)

---

### Post by CharlesA on 2009-10-08
It would depend on the application.

I'm running a RAID-5 due to me being a lazy bum and wanting to run it. It was sort of a toss up between RAID-5 and RAID-10 and I went with RAID-5 due to only needed a minimum of 3 disks.

If you want 50% overhead go with RAID1, if you want a bit less you can use RAID-5, but it uses 1 entire disk for parity and stuff.

Like I said in the beginning, it really depends on what you are going to use it for.

Oh, check [here]("http://guildwars.incgamers.com/showthread.php?t=486381"), there is some nice links and nifty infos/arguments as to HW/SW RAID and which RAID level.

---

### Post by Xianath on 2009-10-08
I would go with RAID6. In all honesty, I don't think any single-parity RAID will do in the long run. How many disks, what size, and what class (green/desktop/RAID)?

Cheers,
Peter

---


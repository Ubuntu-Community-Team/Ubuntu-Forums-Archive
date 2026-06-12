---
title: "How long does a gparted resize operation usually take?"
date: 2011-04-03
forum: The Cafe
---

### Post by Dustin2128 on 2011-04-03
Just wondering, gparted has been running for a good hour now, resizing a 214GB partition to 101- I don't recall it ever taking this long before.

---

### Post by earthpigg on 2011-04-03
the larger and fuller the partitions in question, the longer it will take. as i understand it.

1 hour for a partition containing lots of data... yeah, you may have quit a bit longer of a wait.

put a movie on? maybe start watching the star wars trilogy, or LOTR? :P

edit: i pretty much don't bother resizing partitions, myself. time cost of moving all relevant data off the internal hard drive and onto an external, deleting all partitions, creating brand new partition table with desired partition sizes, re-installing, and moving data back onto internal hard drive... is generally less than the time-cost of resizing partitions by my guestimation. of course, windows is not a factor for me, and that could alter the equation significantly. your situation may be different.

---

### Post by 23dornot23d on 2011-04-03
Can take a long time if it is moving information ....... its got me a couple of times
and it seems like a simple operation .... empty partition resize ......
and it decides its going to move every bit piece by piece ............

you can usually check the output while its running ..... will say where its  up to and 
what it is doing below it ..... each section opens up to give more details ......

sometimes it decides to move things block by block ......

---

### Post by Paqman on 2011-04-03
An hour isn't an especially long time. If it's having to write a whole lot of data to a new location (most common if you're moving the start of a partition) then it can take ages.

---

### Post by Dustin2128 on 2011-04-03
Eh, it finished. No problems there, but it looks like the fedora install's borked :P. ah well, I'll fix it tomorrow or something.

---


---
title: "Software RAID 1 vs rsync"
date: 2007-04-19
forum: Server Platforms
---

### Post by Clashlab on 2007-04-19
Hello,

I am considering buying a laptop from HP which has two hard drives.
I would like to have a /home partition of about 50GB (not the entire drive) and to keep a backup (in an other 50GB partition) on the other drive.

What will be the best solution:
- Software RAID 1 :
    * this adds a layers before the file system (performance)
    * reads will be faster?
    * writes will be slower?
    * data always in sync

- rsync (+ cron) :
    * needs to read the file table every hour to compare the partitions that might be identical
    * if I launch rsync only when I logout, shutdown might take some time
    * in the event of a crash the data might be an hour (day with the upper solution) old [in fact I don't really mind]

Maybe one of you had this dilemma before or is using one of this solution.
Thank for your advice

---

### Post by markitect on 2007-04-19
I use software raid.
* yes it adds extra stuff to do as far as performance i can still drive 100TX ethernet connection at 85-95%, it does however also add a 3-10% overhead on the cpu (depends on processor)
* reads can be 50% faster, but if your doing something like decompression or decoding that takes a lot of cpu it slows down some because of the cpu overhead (can be slower then non-raid)
*writes are supposedly slower, but its only noticeable in the high cpu load case
*Data will always be synced and read to go, if you add a new disc however be prepared for a long wait well it gets all the data.
###Also speed ups are contingent on the drives being on separate channels if your using pata

rsync (used it for remote backups)
if your using the system while it's syncing you will notice a general performance hit to everything, if you have it on logoff or nightly it will take longer to do.

---

### Post by astrogazer on 2007-04-20
Software RAID works great, in my PC the CPU(Athlon 2G) overdeah is less than 1%.
However RAID will  not protect you against accidental or malicious file deletion.

---

### Post by Clashlab on 2007-04-20
Ok, so software RAID is great but has a bit of overhead on the CPU (it will be a Core 2 Duo T7200).
About the accidental file deletion, it hasn't append to me for a long time, so this doesn't matter.

But what about rsync? Does it take some time to figure out that the two partitions are identical?
I guess it has to do some file IO and to more files, the more IO. This can be anoying with an hourly job.
Am I right?

---

### Post by jtc on 2007-04-20
Would you mind terrible much if I were to point out that you are trying to solve the wrong problem :-)

---

### Post by Clashlab on 2007-04-20
No, go ahead

---

### Post by jtc on 2007-04-20
I assume the point of these backup-solutions is to preserve the data you have on your laptop?

Personally I'd say that two of the major dangers to the data on your laptop is either your laptop getting stolen/missing or the laptop hitting the ground a bit to hard. In the first case you'll definatly loose both harddrives and in the second case that is a very real possibility as well. There are also cases like overheating and electricial issues which might impact both drives simultaneously.

Without knowing all the facts, and quite possibly have misunderstood the whole thing, I'd say the right problem to solve is howto backup your data to a place which is not the laptop.

---

### Post by Clashlab on 2007-04-20
Mm, I see what you mean.

But being a bit paranoiac, my laptop is always locked to something that will no move (a coil heater at the moment), and that was succesful. A couple of month ago my roomate laptop was stolen, not mine, guess why
Second thing, I use the laptop as a desktop replacement. When I move the laptop around I am really careful, so its changes to hit the floor are very small.
My concern is the hard drives themselves. There are mechanic parts that are moving and it will stop working at some point. The only question is when.

I also have some backups of very important files on some of my ftp, but that is not so convenient (my internet connection is kind of slow). So in case of a desaster (of one drive) it will be great that a can recovery most of my data.
So I'm looking for a solution...

---


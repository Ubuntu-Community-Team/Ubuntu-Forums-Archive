---
title: "Large partitions, one disk failure acceptable"
date: 2008-06-17
forum: Server Platforms
---

### Post by LyhjeHylje on 2008-06-17
Sorry if the subject line is bit confusing, I am building home media server and I'd like to use LVM, JBOD or similar to combine all disks holding my music, recordings etc.
In my setup it would be ok to lose all the data on one disk should it break but apparently with all jbod-ish schemes I have researched, I'd lose all data on all disks.

So what I am looking for is basic "separate disks" scheme with some kind of layer that makes it look like one disk without the fragileness of LVM & co.

RAID would be overkill as it is not big deal to rip few cd's again or lose some recorded McGyver episodes. OS partition would be raided of course.
What I am asking does not sound impossible but does any partition/volume managers support it?

---

### Post by windependence on 2008-06-17
Well you could set up several disks and then replicate the disk with rsync to one of the other disks. After that, run a cron job that syncs the disks say every 15 minutes or whatever interval you choose. The possibility of 2 disks going out at the same time is very slim. Not RAID or a mirror but close.

-Tim

---

### Post by LyhjeHylje on 2008-06-17
> **windependence said:**
> Well you could set up several disks and then replicate the disk with rsync to one of the other disks. After that, run a cron job that syncs the disks say every 15 minutes or whatever interval you choose. The possibility of 2 disks going out at the same time is very slim. Not RAID or a mirror but close.

-Tim

But this works only with writing, what happens when mythtv or amarok wants to play file?

---

### Post by windependence on 2008-06-17
> **LyhjeHylje said:**
> But this works only with writing, what happens when mythtv or amarok wants to play file?

Unlike Windoze, Linux can share files and separate processes without missing a beat. You could either play the file from the master or the copy, whichever you choose. People replicate data this way all the time on Unixlike systems. I really think it would work. Remember, rsync will only write to the copy the data that has changed. If there is no change, there is no write to the copy drive. So, while you are recording a show, it is writing. When you are watching, nothing is changing unless you are recording at the same time, and even then, I think it will work.

Why the opposition to just plain old RAID one on a hardware controller?

-Tim

---

### Post by LyhjeHylje on 2008-06-17
Um, yes I misunderstood your idea. 
My original point was that backups for my media files are not necessity. If one of three disk goes kaput and I lose some dvb-recordings it's not big deal but with lvm and jbod that one disk takes the others with it and that is bigger deal.

I was looking something that makes multiple disks look like one while still keeping them separate so that I can e.g. plug one of them to separate computer or replace faulty disk. Raid could do this but with storage space loss and, if I understood correctly, disk would have to be added as pairs or triplets which is difficult if your mb has room left for only one.

---


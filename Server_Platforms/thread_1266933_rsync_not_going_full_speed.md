---
title: "rsync not going full speed"
date: 2009-09-15
forum: Server Platforms
---

### Post by sherl0k on 2009-09-15
Hey guys,

I'm having some trouble getting rsync to push out at full speed. the NICs are gigabit, the switches are gigabit, yet rsync won't let me push more than 200mbit/sec or so. If I thread the rsync from my daemon, having multiple clients connect at once, I can push the limits of the card to its full gigabit speed. But for one client, I get maybe a fifth of the speed.

Here's the rysnc command I'm using:

rsync --recursive --delete --times --omit-dir-times --whole-file rsync://x.x.x.x/xxxx /media/xxxx


The files themselves are pretty big, upwards of 8-10 gigs. Using --whole-file or not I still get the same results.

Is there anything else I can do to tweak this, so a single client can experience the full speed, or is this a limitation of the software?

---

### Post by jondkent on 2009-09-15
Have you tried the following option:

--bwlimit=(transfer rate in kilobytes)

value of 0 means no limit

---

### Post by sherl0k on 2009-09-15
I still only get 200mbit/sec, not a gigabit. :confused:

---

### Post by koenn on 2009-09-15
first, test your rsync with a transfer of 1 large file (eg a dvd iso image) to get an accurate reading.

---

### Post by sherl0k on 2009-09-15
That's exactly what I did.

---

### Post by koenn on 2009-09-15
consider that you can not copy a file across the network any faster than you can read it off the source and write it on the destination. What are the disk transfer rates involved here ?

---

### Post by sherl0k on 2009-09-15
Ohhhh you mean a straight rsync copy from one location to another on the disk, not across the network.

I'll give that a shot tomorrow.

---

### Post by koenn on 2009-09-15
no, i meant : you can't push data through that 1Gbit pipe any faster than you can read it off the disk, and you can't (at the other end) pull data  from the 1 Gb pipe  faster than you can write it to the disk. 

but doing a local rsync (preferably between 2 independent disks) may give you an idea of the speed you can expect. 


Also note that there'll always be some addititional overhead (in the several stages of processing the data, i.e. disk controllers, CPU, network stack,  ...) so it's unlikely you'll ever reach a full  125 MB/s (or 1Gbps) for a single transfer. The point in having gigabit networks is mainly that the network is still useful for other traffic even while such a huge transfer is under way. Depending on other factor (such as disk read/wrte speeds),  you can probably expect something around 30-40 MB/s, i.e 200-300 mbps

---

### Post by sherl0k on 2009-09-15
Well I've been able to do regular samba shares pushing gigabit speeds, doing a single file at a time. That's why I'm wondering if I'm configuring rsync correctly.

---

### Post by koenn on 2009-09-15
well, rsync is more then simply copying. It attempts to reduce the actual volume it needs to transfer by a number of mechanisms. You can think of rsync as a program that re-creates a file elsewhere, rather than moving bits from one place to another.  So it might be doing more processing than actual copying. 
That amount of processing increases also if you run rsync with compression. 

Other than that i don't know any rsync configurable options that might affect troughput (other than deliberately limiting the throughput, but that's not what you're after).

I get little over 20-25 MB/S with Samba, approx. 40 MB/S with NFS, and have been told that this is in the normal range. 
I used to measure speeds by FTP-ing a single large file - maybe i should do that again. FTP is about the most straightforward file transfer you can get.

---


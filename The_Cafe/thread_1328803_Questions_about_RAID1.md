---
title: "Questions about RAID1"
date: 2009-11-16
forum: The Cafe
---

### Post by blueshiftoverwatch on 2009-11-16
Since the hard drive is the main bottleneck of the modern desktop computer and solid state drives are still too expensive for my tastes I was thinking of getting a second 1TB hard drive to setup a RAID1 (my motherboard supports RAID) to increase my performance. According to Wikipedia:
> Since all the data exists in two or more copies, each with its own hardware, the read performance can go up roughly as a linear multiple of the number of copies. That is, a RAID 1 array of two drives can be reading in two different places at the same time, though not all implementations of RAID 1 do this. To maximize performance benefits of RAID 1, independent disk controllers are recommended, one for each disk. Some refer to this practice as splitting or duplexing. When reading, both disks can be accessed independently and requested sectors can be split evenly between the disks. For the usual mirror of two disks, this would, in theory, double the transfer rate when reading. The apparent access time of the array would be half that of a single drive.

I know that Wikipedia says that I can theoretically cut my read times in half by adding a second hard drive. But when I switched from an IDE to SATA hard drive I didn't notice much of a speed increase. And SATA can I think transfer data about 2x as fast as IDE. If I didn't notice much of a speed increase when switching from IDE to SATA will I notice enough of a speed increase when switching from a single HD to 2 mirrored HD's to warrant buying a new hard drive?

Since having 2 mirrored HD's means that I'll be writing twice as much information at once how much will that slow down my write times and effect the computer's overall performance?

Also, is RAID1 something that will require me to delete my entire partition table and start all over again? Or can I just plug in the second drive and let it copy everything from the original drive over to the second?

---

### Post by JonRohan on 2009-11-16
That article is suggesting you use two independent RAID cards for your RAID1. 

Personally RAID1 for me is to add a little more redundancy not performance (on desktop pc's anyway). Most desktop motherboards don't have spectacular RAID cards on them compared to RAID cards used in there. IMO (again!!!) performance gains are negligible in real world usage in this instance.

---

### Post by cariboo on 2009-11-16
For an increase in disk read/write speed, you should go with Raid0, i found that raid1 if anything can be a little slower than than a single drive.

---

### Post by The Funkbomb on 2009-11-16
I think you're talking about RAID0.  Raid0 does striping, splitting one set of info to two disks.

RAID1 is mirrored.  Writing one set each to each disk.

---

### Post by blueshiftoverwatch on 2009-11-16
I don't see how RAID0 (which isn't technically true RAID) could perform faster than RAID1. With RAID1 you have two HD's that are exact replias of each other.

Say a file took up 4 sectors (for simplicity's sake). HD1 could load parts 1 and 2 while HD2 loaded parts 3 and 4. So instead of 1 HD doing all the work it's only doing half the work. But with RAID0 it each HD would only have half (2/4 sectors) of the file. So it would load the first half off of one and the second half off of the other. At the very least it seems like RAID0 would be equally as fast as RAID1 but yet loose the advantage of having data redundancy to protect you data if one of the two HD's crashed.

---

### Post by inobe on 2009-11-16
raid0 doubles disk speed, one arm reads while the other writes.

raid0 has absolutely no fault tolerance, this is a problem, if one drive bites the dust there is no way to recover.

raid5 is by far the best but we need more than three hard drives in order to set it up.

more drives' the better as this increases fault tolerance.

raid5 performs just as well as raid0.

---

### Post by skatinjj on 2009-11-16
This [guide]("http://www.staff.uni-mainz.de/neuffer/scsi/what_is_raid.html") is a decent source of information.

---

### Post by blueturtl on 2009-11-17
I very recently [tested RAID1]("http://www.saunalahti.fi/~amodinos/andreas/epic_raidproject/") and found that the performance of two SATA 5400 rpm drives is about equal to a single 7200 rpm PATA drive.

For better performance, you can either do a RAID0 or a RAID5.

RAID 5 is better because it is fault tolerant, but will cost you more because it requires several disks.

---

### Post by Paqman on 2009-11-17
> **inobe said:**
> 
raid0 has absolutely no fault tolerance, this is a problem, if one drive bites the dust there is no way to recover.


Worse than that, since you're running two drives you actually double the chance of a drive failure wiping out your system. It cuts your MTBF in half. 

I would recommend not storing *any* data on a RAID0 array. There's no reason you could put the OS on one though.

---

### Post by Grenage on 2009-11-17
I've been using RAID0 for around 10 years or so, and for me the benefits outweigh the risks.  I don't store anything other than config files, and those are backed up elsewhere; thankfully I've not had a drive fail.

On the flip side, a boss with a VAIO laptop came to me with a failing drive full of "4 years worth of work without a backup".  Turned out that the VAIO came, by default, with XP installed on two drives with RAID0.  I managed to get the data back but it was not at all fun, and he was lucky.

Bottom line with RAID0 is that you do double your chance of failure, albeit it's a relatively small chance you're doubling.  As long as you backup files that matter, it's great.  I always use RAID0 over RAID5 on my workstations, I don't want the overhead; on servers it's either RAID5 or 10.

---

### Post by The Funkbomb on 2009-11-17
Yeah, you can always use a nested RAID like 10 or 01

---

### Post by blueshiftoverwatch on 2009-11-17
If I knew that RAID0 was the RAID that's used performance gains and not RAID1 I'd have gotten two 500GB hard drives instead of one 1TB. I purchased the [Samsung Spinpoint F3]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152185&cm_re=spinpoint_f3-_-22-152-185-_-Product") because according to the reviews I read it's the fastest 1TB drive on the market. And figured that if I decided to setup RAID later I'd just add add on second HD.

If I do end up setting up RAID0 I have no idea what I'm going to do with almost 2TB of space now that I know my data isn't going to be mirrored and that I'll be using the full amount of both HD's put together.

Does having larger partitions (my / and /home directories are on different partitions) with tons and tons of excess space slow down performance, or make no difference?
> **skatinjj said:**
> This [guide]("http://www.staff.uni-mainz.de/neuffer/scsi/what_is_raid.html") is a decent source of information.
I just read over the page you linked to. I'll read over the rest later tonight.

---

### Post by alphaniner on 2009-11-17
> **inobe said:**
> raid5 is by far the best but we need more than three hard drives in order to set it up.

RAID 5 makes me [BAARF]("http://miracleas.com/BAARF/BAARF2.html").

---

### Post by Exodist on 2009-11-17
> **blueshiftoverwatch said:**
> I don't see how RAID0 (which isn't technically true RAID) could perform faster than RAID1. With RAID1 you have two HD's that are exact replias of each other.

Say a file took up 4 sectors (for simplicity's sake). HD1 could load parts 1 and 2 while HD2 loaded parts 3 and 4. So instead of 1 HD doing all the work it's only doing half the work. But with RAID0 it each HD would only have half (2/4 sectors) of the file. So it would load the first half off of one and the second half off of the other. At the very least it seems like RAID0 would be equally as fast as RAID1 but yet loose the advantage of having data redundancy to protect you data if one of the two HD's crashed.

RAID0 (Stripping, aka; Performance) transfers data down both channels at the same time. So half your data will end up on one drive and the other half on the other, thus each channel only has to transfer half the data(using 2 hard drives) it originally would have to start with. In addition both drives search data at the same time. With a stripping setup both drives are used as one single drive. But when you have two drives looking for data at the same time it naturally finds it faster. The search times are not cut in half the normal search time, but it is faster.

---


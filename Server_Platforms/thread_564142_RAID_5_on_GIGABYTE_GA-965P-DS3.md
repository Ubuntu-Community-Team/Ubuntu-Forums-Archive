---
title: "RAID 5 on GIGABYTE GA-965P-DS3"
date: 2007-09-30
forum: Server Platforms
---

### Post by dfreer on 2007-09-30
Hi everyone,

  Well, I'm about to build my first RAID server, and being that I'm a RAID noob I've already screwed it up :( . I bought a Gigabyte GA-965P-DS3 motherboard, it comes with six SATA II ports and onboard RAID. I was planning on doing RAID 5, but only now (after having bought the board and three 320GB SATA hard drives) did I realize that only two of the six SATA ports support RAID, and RAID 0/1 at that. 
:crying: :cursing: :loading shotgun:

  Basically, I have about 500 GB's of data that needs to be backed up, and I was hoping to use RAID 5 so that I can add drives for future growth, and then if I lose a hard drive I can rebuild the data on a new one without losing any data.

  Am I SOL, or will I be able to still use linux software RAID? What are my options? Thanks in advance for any help you guys can give me!

---

### Post by agent8131 on 2007-10-01
Well, though others may disagree, I'd say you got lucky.  I'd say you're much better with software RAID.  The hardware RAID on most motherboards is far less sophisticated than the linux software RAID.  Plus, one reason that I prefer linux software RAID is that the disks are portable to another linux system.  With any hardware RAID you run the risk that the disks will not be portable to another RAID controller, on a motherboard or as a card.  So I'd say go for software RAID 5.  I'm pretty sure you can set it up through the installer.  The only thing to be careful of is that, unless things have changed, the /boot partition cannot be on a RAID 5 drives.  So consider this partition scheme:

sda1 - boot, sda2 - root
sdb1 - boot, sdb2 - root
sdc1 - boot,  sdc2 - root

where your boot partition is a few hundred megabytes, say 256, and the root partition is the rest.

then you'll setup 2 MD (ie RAID) devices:

md0 = RAID1 of the 3 boot paritions (basically making them redundant so you can boot off of any 1 of them)

md1 = RAID5 of the 3 root partitions

Don't worry about a swap partition and use the package dphys-swapfile instead to create a swap file.

Though, this is just what I would do, so you may want to ask around for more advice.

---

### Post by dfreer on 2007-10-01
How bad will the performance hit be on my CPU when using software RAID? The CPU is a Intel Dual-Core 2.2 Ghz, so I assume it should be ok? I plan on getting a lot of reads from multiple users, but I will be the only one writing. From what I understand of it, when reading RAID 5 has pretty much the same performance as RAID 0 correct?

Thanks a lot for your help, when I realized I couldn't use hardware RAID I about lost it :D

---

### Post by agent8131 on 2007-10-19
Sorry for the late reply, for some reason I forgot to subscribe to this thread.  You've probably already moved forward but I would say performance will not be an issue.  Performance for a RAID5 will be less than RAID0 with an equal number of disks but that's to be expected.  RAID0 (aka RAID naught aka RAID not) isn't RAID at all since it's not redundant and, worse, increases the chance of data loss.  However, RAID5 should have similar read performance as RAID0 because reads are being striped across the disk but write performance will be worse.  This seems like a good match for your usage pattern.  The CPU impact will be negligible, or perhaps even better than the onboard RAID which is generally a software RAID anyway (supported by a driver, like a winmodem).

As I said the only really important thing is to make sure your /boot partition is not on the RAID5.  But that disk layout I suggested has worked quite well for me though you could consider putting lvm instead of root on the RAID5 if you're into that kind of thing.

---

### Post by dfreer on 2007-10-20
Thanks for the reply, I have already moved forward with RAID5. I set up RAID1 for the /boot like you suggested, but then also decided to use RAID1 for the swap, as I didn't mind losing the the few gigs of space. I ended up using RAID5 on the rest of the drive, approx 300 GB's on each drive leaving me with 600 GB's of usable space. That space is already full, so within the next year I will probably add another RAID5 with similiar specs.

I also did some tests if anyone is interested:
```
Command I used to test: *sudo hdparm -t /dev/XXX*
ReiserFS on all drives.

**Test #1**: SATA I 5400 RPM internal laptop hard drive:
30.42 MB/sec
31.08 MB/sec
30.83 MB/sec

**Test #2**: EIDE 7200 RPM external USB hard drive:
32.17 MB/sec
32.36 MB/sec
32.37 MB/sec

**Test #3**: EIDE 7200 RPM internal hard drive:
63.84 MB/sec
63.82 MB/sec
63.86 MB/sec

**Test #4**: SATA II 7200 RPM internal hard drive:
68.63 MB/sec
68.52 MB/sec
68.82 MB/sec

**Test #5**: RAID5 w/3 SATA II 7200 RPM internal hard drives:
146.32 MB/sec
146.93 MB/sec
146.92 MB/sec

**Test #6**: RAID0 w/3 SATA II 7200 RPM internal hard drives:
210.44 MB/sec
210.55 MB/sec
211.25 MB/sec

```

---


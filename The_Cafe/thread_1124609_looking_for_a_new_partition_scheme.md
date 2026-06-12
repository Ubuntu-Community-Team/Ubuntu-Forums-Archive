---
title: "looking for a new partition scheme"
date: 2009-04-13
forum: The Cafe
---

### Post by markp1989 on 2009-04-13
i just brought my self a 30gb OCz vertex ssd to add to my desktop. that i plan to use for my root drive.

my current partition scheme is as follows: 

Hdd 1: 80gb sata
8gb ubuntu root 
10gb arch root
rest  as /home for arch

hdd 2: 160gb sata
all /media/data

im going to be adding the new sata ssd as my new root drive . I was thinking of setting the new drives up as follows 

SSD: 
all for arch root

HDD1: 80gb 
/home

hdd2: 160gb
/media/data

im not sure if 80gb is over kill for a home partition considering my current home partition has hardly anything in it , just some settings, and themes. 


also, im thinking that having /home on a hdd which is slower will cause a slight bottleneck during boot. or application loading . for example when a app runs from ssd then has to load the settings from the hdd. is this an issue, or am i just over thinking things. 

if this is a problem i could have the ssd partitioned 10gb for root. and 20gb for home. that way they are both on ssd. 

what do you all think ? 

Thanks for taking the time to read this.

---

### Post by JohnFH on 2009-04-13
What's in /media/data?  The reason I ask it that if you are using it as someone would use a home directory (ie. pictures, videos, music, documents, etc), then 80Gb for your home directory is overkill.

When setting up the filesystems on the SSD, use ext3 with journalling turned on.  This goes against what most people think in that ext2 is better suited for SSD for prolong it's life, but the risk and threat of a corrupt filesystem is much greater than coming to the end of the SSD life.  I speak from experience!

Another thing you need to consider is backups.  Where are you putting your backups at the moment?  If you put both partitions of root and home on the SSD, then you could use the 80GB disk for backups, for example.  Your backups should at least go on a different hard disk.

To answer your other question about loading settings files from the slower drive - you won't see much difference if any.

---

### Post by adamlau on 2009-04-13
SSD: 30GB (Arch)
/ 
/home

HDD1: 80GB 
/bak (Backups)
/tmp
/var

HDD2: 160GB
/data (Multimedia)

Similar to above, this is how I have my MSP 7500 16GB + WD3000GLFS box set up:

SSD: 16GB (Arch + XFS logdev=/dev/sdb1)
/ 
/home

WD3000GLFS: 300GB (XFS + logdev from /dev/sda1)
/bak (Backups)
/data (Multimedia)
/doc (Documents)
/tmp
/var

---

### Post by markp1989 on 2009-04-14
currently /media/data is used for music, and iso images. all of my movies/tv shows are on my file server. 

im thinkg i may use the 80gb for backups, just get an external caddie for it . then  use the following scheme 

30gb SSD : 
15gb root
15gb home

160gb sata: 
/media/data 

i know the ssd wont be exactly 30gb, but i will split it half and half any way. 

Thanks for the pointers:D

---


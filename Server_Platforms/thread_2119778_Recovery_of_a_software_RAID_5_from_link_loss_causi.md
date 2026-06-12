---
title: "Recovery of a software RAID 5 from link loss causing multiple disks to fail"
date: 2013-02-24
forum: Server Platforms
---

### Post by MakOwner on 2013-02-24
This is more of an exrecise than anything at this point, no big deal if I have to wipe and start over, but I know there should be a way to do this.
At least next time maybe.

I'm using the latest version of the SANS Digital 8 bay eSATA enclosure.
I have noted over the last couple of generations of these things they have become somewhat dodgy, so when I get a new one, I usually set up some older disks in them to verify functionality so I can RMA them before putting them into use.  

I had set up a 6 drive RAID 5 array, three disks on each port multiplier and started copying some test data onto it.  It was sitting idle last night and when I walked past it this afternoon, I noticed that the link light and all the disk power lights on one of the port multipliers was dark.  

I touched the eSATA cable on that port and they all came back to life.  

So, I have all of the original disks back online, but three of the 6 have been failed out of the array.
I tried a create with assume clean, specifying the devices in what I'm _pretty sure_ is the original order.  I'm using the order as specified in /proc/mdstat prior to trying any of this.


The array assembles when using this order, and the partition on the drive shows up but appears to be not contain any valid data.  

When I do this assmebly using logical order I get a RAID volume but no partition.

Is there a good/safe way to recover from this sort of thing?

I figured this would be a good exercise for if/when when one of my in-use enclosures does the same thing.

I'm running this from a minimal installation of 12.04 LTS.

```

# mdadm --create /dev/md3 --assume-clean --level=5 --raid-devices=6 /dev/sdh1 /dev/sdi1 /dev/sdc1 /dev/sdg1 /dev/sde1 /dev/sdd1 
mdadm: /dev/sdh1 appears to be part of a raid array:
    level=raid5 devices=6 ctime=Sat Feb 23 18:59:42 2013
mdadm: /dev/sdi1 appears to be part of a raid array:
    level=raid5 devices=6 ctime=Sat Feb 23 18:59:42 2013
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid5 devices=6 ctime=Sat Feb 23 18:59:42 2013
mdadm: /dev/sdg1 appears to be part of a raid array:
    level=raid5 devices=6 ctime=Sat Feb 23 18:59:42 2013
mdadm: /dev/sde1 appears to be part of a raid array:
    level=raid5 devices=6 ctime=Sat Feb 23 18:59:42 2013
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid5 devices=6 ctime=Sat Feb 23 18:59:42 2013
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md3 started.


# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md3 : active raid5 sdd1[5] sde1[4] sdg1[3] sdc1[2] sdi1[1] sdh1[0]
      2441269760 blocks super 1.2 level 5, 512k chunk, algorithm 2 [6/6] [UUUUUU]
      
unused devices: <none>

# ls -al /dev/md3*
brw-rw---- 1 root disk   9, 3 Feb 24 17:00 /dev/md3
brw-rw---- 1 root disk 259, 0 Feb 24 17:00 /dev/md3p1
root@PE850-fs04:/home/dale# mount /dev/md3p1 /mnt/md3
mount: wrong fs type, bad option, bad superblock on /dev/md3p1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

---

### Post by ali abry on 2013-02-25
you said your pretty sure of the order of disks. you can make sure of the order by checking output of this :
mdadm --examine /dev/as[a-z]1 > raid-statue 
from that file you can confirm your order by using "Array UUID" and "Device Role" .
I'm not expert on raid but you may need to specify the size. check here :
[https://raid.wiki.kernel.org/index.php/RAID_Recovery](https://raid.wiki.kernel.org/index.php/RAID_Recovery)

---

### Post by darkod on 2013-02-25
With mdadm you usually use the md devices directly, not with partitions on them, like that md3p1. I'm not sure if it's a result of the failure, or it existed before???

Did you try something like:
sudo mount /dev/md3 /mnt

If you want to use mount point /mnt/md3 it has to exist first of course.
sudo mkdir /mnt/md3

---


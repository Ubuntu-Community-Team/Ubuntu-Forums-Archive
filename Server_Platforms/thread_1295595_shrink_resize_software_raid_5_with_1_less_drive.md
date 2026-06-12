---
title: "shrink resize software raid 5 with 1 less drive?"
date: 2009-10-19
forum: Server Platforms
---

### Post by plonka2000 on 2009-10-19
Hi All,

I've recently been looking to shrink my 7-drive mdadm raid5 to a smaller amount of drives. I've seen on various parts of the interweb that there is a method to shrink mdadm raid5 by failing and removing a drive then resizing then rebuilding the whole array onto the remaining drives.

The theory sounds logical but I have no idea if anyone is managed to do this in real actual practise.

**The immediate problem I now have though is that one of y drives is now failed and I wish to shrink my array onto 6 drives so that I may use my other 2 ports for larger and non-essential data drives (as I've found filling my server with 1 big raid5 was a good idea at the beginning, but not anymore).**

Can anyone help me please?

One of the only points of useful reference I have found for shrinking raid is [here]("http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid") but this seems to be for raid mirrors rather than raid5.

---

### Post by windependence on 2009-10-19
Keep in mind, less spindles = slower access time.

-Tim

---

### Post by plonka2000 on 2009-10-20
Hi,

The slower access time is fine for me, as its 7 drives to 6 drives I'm going for... Its more than fast enough. :)

I need to find out a correct method for doing this, even if anyone can just provide a link to a howto somewhere.

Thanks all.

---

### Post by plonka2000 on 2009-10-20
Just bumping this up to see if anyone can help?

---

### Post by fjgaude on 2009-10-21
Correct method, can't say for sure... I'd stop the array, fault the drive, remove the drive, then assemble it, clean with raid-devices=6. All this is in the man pages for mdadm.

---

### Post by plonka2000 on 2009-10-22
> **fjgaude said:**
> Correct method, can't say for sure... I'd stop the array, fault the drive, remove the drive, then assemble it, clean with raid-devices=6. All this is in the man pages for mdadm.
I'd really like to clarify this for anyone trying to do this in future, if I can.
As far as I can tell, there are a lot of people wanting to know how to do this, but no documented methods to do this.

Ok so to my understanding:

**1- Stop the array:**
```
mdadm --manage /dev/md0 --stop
```

**2- Fault the Drive:**
```
mdadm --manage /dev/md0 --fail /dev/sdf1
```

**3- Remove the drive:**
```
mdadm --manage /dev/md0 --remove /dev/sdf1
```

**At this point I would power down the server, physically remove /dev/sdf and move drive /dev/sdg to sata port occupied by /dev/sdf, essentially coming back up as /dev/sdf [COLOR="Red"]<- Is this ok or should I complete the shrink before any power down?[/COLOR]**

**I'd then boot up, check that raid drives arranged logically from sda->sdf, and continue?**

**4- Assemble the array, clean with 6 devices:**
```
mdadm --assemble /dev/md0 --scan --raid-devices=6 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1
```

**5- Dont I need to shrink the filesystem here?**
```
mdadm --grow /dev/md0 --raid-devices=6 --size 2400G
xfs_growfs /dev/md0
```

[COLOR="Red"]Could I kindly ask if someone can sanity check my commands, as I'm sure about a few of them.[/COLOR]

---

### Post by fjgaude on 2009-10-22
Everything is okay as you stated except I don't think you have to size the new array. The re-sync process takes care of that.

I tell you, you are at the place where it shows that, no-matter-wha,t you should have full backup of anything that is important... over all the years with me playing around with software raid I always had backup, and that is why I don't worry about all the subtle things we are dealing with here. Can't never be sure that I wouldn't do something that destroyed my data... backup, backup...

---

### Post by plonka2000 on 2009-10-23
It looks like my efforts may be in vain.

I have been reading the XFS filesystem FAQ [here]("http://xfs.org/index.php/XFS_FAQ") and it states that: 

> **Q: Is there a way to make a XFS filesystem larger or smaller?**

**[COLOR="Red"]You can NOT make a XFS partition smaller online. The only way to shrink is to do a complete dump, mkfs and restore.[/COLOR]**
An XFS filesystem may be enlarged by using xfs_growfs(8 ).
If using partitions, you need to have free space after this partition to do so. Remove partition, recreate it larger with the exact same starting point. Run xfs_growfs to make the partition larger. Note - editing partition tables is a dangerous pastime, so back up your filesystem before doing so.
Using XFS filesystems on top of a volume manager makes this a lot easier.

Bummer... Looks like a complete backup and restore on new RAID5. :(

---


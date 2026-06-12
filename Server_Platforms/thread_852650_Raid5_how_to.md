---
title: "Raid5 how to"
date: 2008-07-07
forum: Server Platforms
---

### Post by gecka on 2008-07-07
Hello,

I have partitioned my 3 harddisks into the following configuration:

/boot 1GB with RAID1 on sda1, sdb1, sdc1
Three swap 12GB on each disk (sda3, sdb3, sdc3)
/ the rest of the hard disk space with RAID5 on sda2, sdb2, sdc2

I have unplugged sda1 to simulate hard disk failure and the server won't boot anymore even if I shutdown and replug sda.

What have I miss ?

Regards

---

### Post by fjgaude on 2008-07-07
Well, for raid1 you need pairs of partitions... I don't know what three does.

I know you need to have grub on each drive to be able to boot with just one disk... and from what I've read here and about there is a bug in Ubuntu that will not permit raid1 to function correctly.

Guess we'll have to re-think what we wish to do and how, eh?

---

### Post by gecka on 2008-07-07
> **fjgaude said:**
> Well, for raid1 you need pairs of partitions... I don't know what three does.

Well all three partition are mirrored! That is ok

> **fjgaude said:**
> I know you need to have grub on each drive to be able to boot with just one disk... and from what I've read here and about there is a bug in Ubuntu that will not permit raid1 to function correctly.

Guess we'll have to re-think what we wish to do and how, eh?

Solved it. recovered my raid 5 in recovry mode from INSTALL cd.
Then It is as easy as doing:

# grub

> root (hd0,0)
> setup  (hd0)

> root (hd1,0)
> setup  (hd1)


> root (hd2,0)
> setup  (hd2)

>quit

# reboot

Then if I unplug ANY disk, system still boot on the degraded raid5 array.
That is I have my "nearly" perfect setup (just need a hot spare disk now).

Regards

---

### Post by fjgaude on 2008-07-07
Very good... I've not seen a three-disk raid1 before... have no idea how it can work. But it does, at least for you. On second thought, sure it can work. <smile>

Using mdadm it is easy to add a spare, hot or otherwise.

Congratulations on getting it and running.

---

### Post by windependence on 2008-07-07
Well I think he is talking about RAID 5 there:

> Solved it. recovered my raid 5 in recovry mode from INSTALL cd.

BUT, AFAIK, you can mirror any amount of disks in RAID 1 if you want.

RAID 5 would be my choice but of course YMMV. I used to run all of my OS disks on 3 18.2 gig scsi drives. A bit more space than I needed but I didn't have to worry about 1 drive failure.

-Tim

---

### Post by fjgaude on 2008-07-08
Both raid1 and raid5, Tim... his boot partition is raid1. But by putting grub on all three drives he solved his problem.

---


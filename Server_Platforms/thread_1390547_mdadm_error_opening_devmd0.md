---
title: "mdadm: error opening /dev/md0"
date: 2010-01-25
forum: Server Platforms
---

### Post by Marzuk on 2010-01-25
Total Linux newbie here so any help is welcome.  Extensive use of Google really didn't help.  Using Ubuntu 9.10 server, getting the error in the title.  I am using EC2 and attempting to create a software raid out of 5 EBS volumes.

First, just to verify that /dev/md0 does not exist:

```
~$ sudo ls -a /dev/md*
ls: cannot access /dev/md*: No such file or directory
```

```
~$ sudo mdadm -C /dev/md0 --chunk=256 -n 5 -l 0 /dev/sdh1 /dev/sdh2 /dev/sdh3 /dev/sdh4 /dev/sdh5
```

When I run this command to attempt to create a software RAID from 5 disks, it provides an error.  As far as I can see, it appears to exist, and running this command creates it.

```
mdadm: error opening /dev/md0: No such device or address

~$ ls -l /dev/md*
brw-rw---- 1 root disk 9, 0 2010-01-25 23:35 /dev/md0

~$ sudo mdadm -D /dev/md0
mdadm: cannot open /dev/md0: No such device or address
``` The disks that I am  attempting to use to create the array exist as  well, and are formatted  as xfs.

```
~$ sudo blkid
/dev/sda1: UUID="929326d8-1eb2-4bbd-919e-f65d51745351" TYPE="ext3"
/dev/sda3: TYPE="swap"
/dev/sdh1: UUID="1e061b3b-cb21-4a8f-bf13-43ee5f903fb2" TYPE="xfs"
/dev/sdh2: UUID="0af7bf51-af1b-4c4c-885a-e56813101c3c" TYPE="xfs"
/dev/sdh3: UUID="67b1b543-74ae-466b-b3d3-e18dbd6f099d" TYPE="xfs"
/dev/sdh4: UUID="9f87c734-cb7c-48dc-8999-a69199095833" TYPE="xfs"
/dev/sdh5: UUID="89695182-5d9a-4a70-bec5-bee4fffafed8" TYPE="xfs"
```As a side note:

```
~$ sudo modprobe xfs
FATAL: Module xfs not found.
```This command fails, but obviously I had no issues using mkfs.xfs, and I've mounted a single volume with an xfs filesystem previously without issue.

---

### Post by Mister.Vash on 2010-01-26
check and see if the module is loaded correctly - haven't had to do that in a while, but this link looked it had the right steps:
[http://www.linuxquestions.org/questions/fedora-35/mdadm-fails-to-assemble-my-raid-device-564290/](http://www.linuxquestions.org/questions/fedora-35/mdadm-fails-to-assemble-my-raid-device-564290/)

I didn't notice anything odd with what you were doing, I would recommend trying to see if you can get more information from the command by turning up the verbosity - I expanded all the options from you original as it's easier for me to see what is going on with it that way and added the two verbose options

```
sudo mdadm --verbose --verbose --create /dev/md0 --chunk=256 --raid-devices=5 --level=0 /dev/sdh1 /dev/sdh2 /dev/sdh3 /dev/sdh4 /dev/sdh5
```

---

### Post by Xianath on 2010-01-26
OK several things seem very wrong here.

First, if my understanding of EC2/EBS is correct, your disk space is already redundant at Amazon. Why bother with RAID5? If I got it wrong and that's indeed local storage only mirrored at EC2, then you have a bigger problem because you're planning to RAID5 partitions on the same drive, which of course provides zero redundancy if your drive dies.

Also, what are the contents of /proc/mdstat? The array may indeed exist but be down, so it will need to be either activated or deleted.

Finally, you are attempting to RAID5 partitions that have already been formatted with XFS, i.e. they are of the wrong partition type (83). They need to be of type Linux RAID Auto (fd) for md to recognize them as array members.

Cheers,
Peter

---

### Post by Marzuk on 2010-01-26
I'm attempting to create a 5 disk RAID0 array.

The reason they were formatted with xfs before creating the RAID, is that the instructions I found went step by step and that was one of the steps.  I also walked through a guide that created a partition and marked them fd, but that also yielded the same result.

modprobe md just gives a Fatal: module not found error (or close to).  I googled the crap out of this for 4 hours, and already saw that forum thread and tried the suggested steps there.

------

Actually, after having all the trouble above, I just used a different AMI and modprobe responds as expected and allows me to load modules.  I'll try creating the RAID again and see if this AMI does what I need.

Thats the problem with Linux and newbies I guess.  It seems like a house of cards to me.  I'm sure the previous one would work, if I knew what I was doing.

Thanks for the help though guys.  I was just trying to figure out if there was something obviously wrong.  I don't like to assume that its not user error, because the majority of the time it is :D

---

### Post by Xianath on 2010-01-26
Ubuntu is user-friendly enough to newbies. Creating a software RAID out of cloud storage is not exactly newbie work though. Ask your granny when was the last time she did that :)

Cheers,
Peter

---


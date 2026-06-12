---
title: "LVM or RAID (or both?)"
date: 2012-07-31
forum: Server Platforms
---

### Post by arbiter2x on 2012-07-31
hello,
I'm trying to configure my home-server (it came with Windows server pre-installed, but i want to use ubuntu-server with it)

but I'm having a hard time figuring out, how to set up the file-system.

it's suppose to mainly work as datagrab - but maybe also run small services on top of it (web server, etc.)

I want to have some sort of redundancy for my files (I was thinking RAID1 or 5)
but I also need to be able to expand the file-partition in case I run out of storage and buy additional hard-drives (I was thinking LVM)


- is there some sort of hybrid of both ?

- does it make sense to set up an LVM, create 2-3 partitions on it - and set up a RAID with those paritions? (doesn't RAID need the partitions to be on different drives? if I set up an LVM, aren't they basically on the *same* drive?
it's a slightly confusing subject matter :)

I hope I'm not the first person to struggle with this thought-process ;)


Edit:
I played a little with the ubuntu server installer....and found out that it's not possible to create a MD on a a Logical Volume
I even created 2 volume groups with 1 volume on each - hoping to be able to set up a raid1 ....
...but the installer didn't let me do that either

---

### Post by Irregular Joe on 2012-07-31
On my systems, I setup RAID (1, in my situation) then built LVM on top of the RAID device.  You will still need a small non-RAID partition for /boot (1G is plenty), as Grub cannot boot from RAID.

So, create your RAID device (e.g. md0) then create the LVM physical volume for /dev/md0, and your volume groups and logical volumes on top of that.  This allows you to use LVM's capabilities to extend logical volumes.  Resizing RAID partitions is not as flexible as LVM.

Hope this helps!

---

### Post by arbiter2x on 2012-07-31
alright, so I have created (1 sepearate boot partition and) 2 raid partition on 2 drives (1 on each)

then I created a RAID1-MD with both partitions
then I went ahead and created a new LVM partition on the RAID partition
THEN I created a volume group and a logical volume on that on top of that.
AND THEN I created created an ext4-partition on that LV :p

so far so good.

but what happens if I want to add another drive later on?
how would that process work?

---

### Post by Irregular Joe on 2012-07-31
It sounds like you set up TWO RAID partitions instead of one.  For the 'simplest' configuration, here's my layout:

So, in my implementation, my disks look like this:
/dev/sda: partition 1=ext4(/boot), partition 2=used for RAID.
/dev/sdb: partition 1=ext4(unassigned), partition 2=used for RAID

Now, create the RAID partition that points to /dev/sda2 and /dev/sdb2. This will normally get named /dev/md0.  Use /dev/md0 (rather than /dev/sda2...) for the LVM physical volume and use LVM as normal from there.

My LVM physical volume points to /dev/md0, and so does the LVM volume group. The LVM partitions are assigned within this volume group.

Let me know if there are still questions.

---

### Post by darkod on 2012-07-31
> **arbiter2x said:**
> 

but what happens if I want to add another drive later on?
how would that process work?

If you want to continue having redundancy, you would actually buy two new disks. You install them, set up a single raid partition on both of them, and create a new md device from those two partitions (I am talking about a raid1 case).
Then you add that md device as physical device for LVM, you add it to the VG and it becomes available space for expanding the LVs.

> as Grub cannot boot from RAID.You probably meant grub can't boot from LVM. Of course it can boot from raid, that's the point, your server should still boot if you lose a disk.

To the OP, you actually should have created same sized partitions on both disks, create md device from them and use that device as /boot if you wanted separate /boot. Now you have a single /boot partition on one disk only, so if that disk fails you can't boot even though your / partition is raided and will exist on the other disk.

Earlier for LVM you needed separate /boot outside the LVM (raid or no raid), but in the latest releases this is not needed any more and grub2 can boot from LVM too.

---

### Post by rubylaser on 2012-07-31
LVM is not necessary to support expanding an mdadm array.  mdadm can handle resizing and expansion by itself.  LVM adds one more layer to troubleshoot in this case that really isn't providing an extra features.  LVM has lots of neat features, but I don't see where it's needed in your use case.

Also, if you plan to expand in the future, I would have suggested using RAID5 on for your array.  If you add an extra disk to your RAID1, you don't get extra space, you get extra redundancy.  A RAID5 array would allow you to expand or even reshape to a RAID6 in the future. Or build a (4) disk LVM based RAID10 (a stripe of 2 mdadm RAID1s) as darkod has suggested.

There is no native reshape option to convert a RAID1 to a RAID5, so when the time comes to add another disk, you'll have to use mdadm to create a new (2) disk RAID5 array, and allow it to reshape.  This is a risky procedure and seems like it could be easily avoided by using RAID5 from the beginning.

---


---
title: "HELP! weird problem trying to create swap device"
date: 2008-10-10
forum: Server Platforms
---

### Post by rkleemann on 2008-10-10
Hi,

I'm running Ubuntu Server 8.0.4

I have 4 disks, all of which I've set aside one partition for swap.

It's sda5, sdb5, sdc5, sdd5

All disks are formatted the same:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          15      120456   fd  Linux raid autodetect
/dev/sda2              16       60317   484375815   fd  Linux raid autodetect
/dev/sda3           60318       60801     3887730    5  Extended
/dev/sda5           60318       60801     3887698+  fd  Linux raid autodetect

Originally I simply had /dev/sd[abcd]5 as type Swap. But since I was having these weird problems, I decided to just make a RAID0 device out of the 4 partitions, so now they're all type raid.

None of these partitions are being used at all. They are free and clear.

I currently have 2 raid devices, /dev/md0 is raid1 and /dev/md1 is raid5. ONLY these partitions are being used:

/dev/md0 is raid1 using:
    Number   Major   Minor   RaidDevice State
       0     254        0        0      active sync   /dev/mapper/sda1
       1     254        1        1      active sync   /dev/mapper/sdc1
       2     254        2        2      active sync   /dev/mapper/sdb1
       3     254        3        3      active sync   /dev/mapper/sdd1


/dev/md1 is raid5 using:
    Number   Major   Minor   RaidDevice State
       0     254        4        0      active sync   /dev/mapper/sda2
       1     254        5        1      active sync   /dev/mapper/sdc2
       2     254        6        2      active sync   /dev/mapper/sdb2
       3     254        7        3      active sync   /dev/mapper/sdd2


There are no other raid devices, and nothing else is touching the sd[abcd]5 partitions.

But ANY attempt at using these partitions results in a device busy error. For example:
$ sudo mdadm --create /dev/md2 --level=0 --raid-devices=4 /dev/sd[abcd]5
mdadm: Cannot open /dev/sda5: Device or resource busy
mdadm: Cannot open /dev/sdb5: Device or resource busy
mdadm: Cannot open /dev/sdc5: Device or resource busy
mdadm: Cannot open /dev/sdd5: Device or resource busy
mdadm: create aborted

I would get the same exact error when the devices were of type Swap and I tried to run mkswap on them... 

Could this be because I have LVM over raid and the kernel is confused?

How can I determine WHY the kernel thinks that these partitions are busy? I'm currently unable to enable swap.

please help!

Thanks
Ricardo

---

### Post by fjgaude on 2008-10-10
The devices have superblocks that are of other arrays. Did you create an array from these drives before?

Make sure the old array is --stop and umounted. Then use **mdadm** to --zero-superblock each partition.

---

### Post by rkleemann on 2008-10-10
> **fjgaude said:**
> The devices have superblocks that are of other arrays. Did you create an array from these drives before?

Make sure the old array is --stop and umounted. Then use **mdadm** to --zero-superblock each partition.

Very strange.

This is a brand new install, these drives were never used before...

And it won't let me do this:

$ sudo mdadm --zero-superblock /dev/sda5
mdadm: Couldn't open /dev/sda5 for write - not zeroing

Is there any other way I can diagnose this?

---

### Post by rkleemann on 2008-10-10
More info on this...

I found that the dev mapper had those partitions in its list...

/dev/mapper/sd[abcd]5

But were all inactive in dmsetup.

So I removed them from the mapper.

But even after removing them I still get the same errors

$ sudo mdadm --create /dev/md2 --level=0 --raid-devices=4 /dev/sd[abcd]5
mdadm: Cannot open /dev/sda5: Device or resource busy
mdadm: Cannot open /dev/sdb5: Device or resource busy
mdadm: Cannot open /dev/sdc5: Device or resource busy
mdadm: Cannot open /dev/sdd5: Device or resource busy
mdadm: create aborted

---

### Post by fjgaude on 2008-10-10
What happens when you --stop /dev/md2?

Or when you umount /dev/md2?

As an after thought I vaguely remember that you can't use **mdadm** to make arrays from secondary partitions... I can be wrong here, and I can't ever remember of doing it myself.

---

### Post by rkleemann on 2008-10-10
> **fjgaude said:**
> What happens when you --stop /dev/md2?

Or when you umount /dev/md2?

As an after thought I vaguely remember that you can't use **mdadm** to make arrays from secondary partitions... I can be wrong here, and I can't ever remember of doing it myself.

Well the create never really worked, so /dev/md2 doesn't really exist. And it was never mounted anywhere.

But strange enough, mdadm doesn't complain about the stop:

$ sudo mdadm --stop /dev/md2
mdadm: stopped /dev/md2

Yet it makes no difference. Any attempt to access those partitions fail.

---

### Post by fjgaude on 2008-10-10
The fact that **mdadm** recognized /md2 says it exist. Now umount the /dev/md2 and see what happens in terms of creation.

---

### Post by rkleemann on 2008-10-10
> **fjgaude said:**
> The fact that **mdadm** recognized /md2 says it exist. Now umount the /dev/md2 and see what happens in terms of creation.

The problem is with dmsetup. Somehow the mapper table is taking those devices, even after boot.

Before I attempt to create /dev/md2, it isn't even recognized.

$ sudo umount /dev/md2
umount: /dev/md2: not found

Plus it's not listed in /etc/mdadm/mdadm.conf

When I try to create md2, it gives me the Device busy errors. But still, it's not mounted...

$ sudo umount /dev/md2
umount: /dev/md2: not mounted

The problem is here:
$ sudo dmsetup info /dev/sda5
Name:              sda5
State:             ACTIVE
Tables present:    LIVE
Open count:        0
Event number:      0
Major, minor:      254, 8
Number of targets: 1

So the logical volume mapper has it. It's not being used, not open, but it's taken. I've tried removing it, but it's not working. I don't quite know how to work dmsetup. If I can release these devices from the logical volume manager, I should be ok.

Any idea how to remove that from dmsetup? I've ran the "dmsetup remove" command on all devices, but STILL, even after that, I'm not able to use the devices. Even after removing them and rebooting, the system comes back up with the devices taken in the logical volume.

---

### Post by fjgaude on 2008-10-11
I don't use LVM and have no experience with it, or with dmsetup.

Sorry.

---


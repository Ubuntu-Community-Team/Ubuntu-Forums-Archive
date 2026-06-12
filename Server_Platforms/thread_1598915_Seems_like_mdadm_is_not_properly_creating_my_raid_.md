---
title: "Seems like mdadm is not properly creating my raid 5"
date: 2010-10-17
forum: Server Platforms
---

### Post by tyfius on 2010-10-17
I am trying to set up a RAID-5 on my new server.

I installed 10.04.1 server on a 320GB hard drive.
I attached 3 HDD's of 2TB each, used fdisk to create a partition and set the type to fd (Linux RAID autodetect).
I installed mdadm

When running the command **sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1** I always get the following:
```

Continue creating array? y
raid 5: raid level 5 set md0 active with 2 out of 3 devices, algorithm 2

```

When I issue **sudo cat /proc/mdstat** I see that instead of the expected [3/3] I get a [3/2] and [UU_].

The hard disks are brand new and when running fsck commands I always get the message the disks are OK but for some reason I am getting the impression it's not properly creating my raid.

Am I missing some options or is this normal?

*edit*

When I run **sudo mdmad --examine --scan --verbose** I get the following output:
```

ARRAY /dev/md0 level=raid5 num-devices=3 UUID={someuuid}
  spares=1 devices=/dev/sdc
ARRAY /dev/md0 level=raid5 num-devices=3 UUID={someuuid}
  spares=1 devices=/dev/sdb1,/dev/sdc1,/dev/sda1

```
That doesn't look right either?

What's the safest way to completely recover and clean the 3 hard drives so there is absolutely nothing on them or no special blocks whatsoever?

---

### Post by SeijiSensei on 2010-10-17
> **tyfius said:**
> What's the safest way to completely recover and clean the 3 hard drives so there is absolutely nothing on them or no special blocks whatsoever?

Start first by making sure the partitions are marked as "Linux Raid Autodetect" using fdisk.  Run "sudo fdisk /dev/sda", then at the prompt use the *d*elete command to remove any existing partitions.  If you want to use the entire disk for RAID, then enter "**n**ew", "**p**rimary", enter a "**1**" to create a single partition.  Hit enter twice to assign all the tracks to partition 1.  Now use the "**t**ype" command and enter "**fd**" as the type to mark the partition for RAID.  Finally, enter "**w**rite" to save the partition table.  Repeat for each of the other drives.  (Use the initial letter of each command above, i.e, "n" for "new", etc.)

When you've finished you should be able to create the device with mdadm using the "mdadm --create" command you list above.

---

### Post by bakegoodz on 2010-10-17
I see the problem from mdstat, your missing third drive is a separate broken array. The common hang-up with mdadm is that you can't just recreate a raid array, it doesn't wipe out the existing one. The wipe out the array you need to zero out the super block on each drive. Here are some good commands to use:

umount /dev/md0
mdadm --stop /dev/md0
mdadm --zero-superblock /dev/sda1
mdadm --zero-superblock /dev/sdb1
mdadm --zero-superblock /dev/sdc1
mdadm --zero-superblock /dev/sdc

---


---
title: "How do I recover from mdadm misconfiguration?"
date: 2010-07-09
forum: Server Platforms
---

### Post by hierophant on 2010-07-09
I'm setting up Ubuntu 10.04 Server x64 on a Gateway DX4710.  I installed on a 500GB SATA, using encrypted LVM, added webmin, and used ufw to configure iptables.  All seemed fine.

I then set up RAID1 on two 1TB SATAs.  Using webmin, I created Linux RAID partitions on sdb and sdc.  I then ran ...

sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
sudo mkfs.ext3 /dev/md0
sudo mkdir /data
sudo chmod -R 777 /data
sudo mount /dev/md0 /data

All still seemed fine.  I could see /data in the webmin filesystem list, and had ca. 1.4TB total local disk space.

At that point, I decided that I really wanted an encrypted filesystem on /dev/md0.  I also needed to tweak the fan setup.  And so I shut down, without adding /dev/md0 to fstab.  And it was probably still synching.

Now /dev/md0 is semi missing.  That is ...

sudo mdadm -D /dev/md0   =>  doesn't exist
sudo mdadm -E /dev/sdb1  =>  part of RAID1 with sdc1
sudo mdadm -E /dev/sdc1  =>  part of RAID1 with sdb1

What do I do now?  Can I recover /dev/md0?  Is it just that I didn't add it to fstab?  Can I just do that now?  Or do I need to delete sdb1 and sdc1, and start over?

---

### Post by benderisgreat on 2010-07-09
you assemble a previously created array with ```
mdadm --assemble --scan
``` or ```
mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1
```

Then configure your mdadm.conf with:
```
mdadm --detail --scan >> /etc/mdadm/mdadm.conf 
```

---

### Post by hierophant on 2010-07-09
Thank you, benderisgreat.

It appears that I've dug a deeper hole than that.

Here's what I find (sudoing omitted).

```
mdadm --assemble --scan
```... reports "mdadm /dev/md/0 has been started with 1 drive (out of 2)."

```
 mdadm -D /dev/md0 
```... reports that /dev/md0 is "clean, degraded" and that ...

RaidDevice  State
0                                 active synch      /dev/sdb1
1                removed

I did remove /dev/sdc1 last night, after getting errors that it was busy whenever I attempted anything with /dev/md0.  Although the command apparently failed, reporting that /dev/sdc1 was busy, I guess that it actually succeeded.

```
 mdadm --add /dev/md0 /dev/sdc1 
```... reports "Cannot open /dev/sdc1: Device or resource busy".

```
 mdadm -E /dev/sdb1 
```... reports ...

RaidDevice  State
 0                                 active synch      /dev/sdb1
1                faulty removed

```
 mdadm -E /dev/sdc1 
```... reports ...

 RaidDevice  State
  0                                 active synch      /dev/sdb1
 1                active synch      /dev/sdc1

Using webmin, I deleted the partition /dev/sdc1 and recreated it.  That didn't change anything.

Also, in flailing about last night, I added physical volumes sdb and sdc to the server's LVM volume group.  I did that after md0 had been created, but while it wasn't running.

Now that md0 is running, albeit with only one member, I see "RAID device 0" in the list of physical volumes that I could add to the LVM volume group.  That would be the correct choice, yes?

Attempting to delete sdb and sdc from the volume group, I get errors (same for both) that ...

Couldn't find device with uuid '[uuid1]'.
Couldn't find device with uuid '[uuid2]'.
Cannot change VG [NAME] while PVs are missing!

It appears that the system is storing conflicting information about /dev/sdb1 and /dev/sdc1.  Are there ways to fix that?

Edit:  I have addition information that may be pertinent.

```
mdadm -Q /dev/sdc1
```... reports "device 1 in 2 device mismatch raid1 /dev/md0".

```
mdadm --zero-superblock /dev/sdc1
```... reports "Couldn't open /dev/sdc1 for write - not zeroing"

Edit:  I am at a loss.  

```
dd if=/dev/zero of=/dev/sdc bs=1M
``` ... completed in ca. 3 hr without complaint.

In webmin, I created Linux RAID partition sdc1 on sdc.

```
mdadm --add /dev/md0 /dev/sdc1
``` ... reports "Cannot open /dev/sdc1: Device or resource busy".

???

---

### Post by hierophant on 2010-07-11
I'm tempted to delete my previous post, and will if requested.

I believe that I've identified the cause of the bizarre behavior described above.  I apparently had the disks connected in the wrong order ... 

SATAII0 = sda
SATAII1 = sdb
SATAII2 = CD ROM
SATAII3 = sdc

Anyway, I ended up reinstalling -- several times -- until I actually understood what I was doing.  I used three 1 TB drives, with the following partitioning ...


/dev/md0 = RAID5 sda|sda1+sdb|sdb1+sdc|sdc1 (100MB each)[INDENT]= /boot (ext4)
[/INDENT]/dev/md1 = RAID5 sda|sda2+sdb|sdb2+sdc|sdc2 (1TB each)[INDENT]= mapper/md1_crypt --> lvmgrp
[/INDENT]lvmgrp[INDENT]root (4.7 GB ext4)
swap (11.2 GB)
home (1.8 TB ext4)
[/INDENT]

---

### Post by benderisgreat on 2010-07-11
Do you realize that the partition table resides on the first part of the disc so that a dd if=/dev/zero of=/dev/sda will delete the partition table of that disc (as well as any raid array metadata)?

> I added physical volumes sdb and sdc to the server's LVM volume group.
You were trying to logically devide the drives with lvm on the same logical level that they were partitioned (another way of logical devision). This conflicts.

It is clear from your last post that you have figured out to put the lvm volume group on the raid array. Glad you solved your problem. Just mentioning these two things for clarity's sake (yours or for anyone else who reads this thread).

---

### Post by hierophant on 2010-07-11
Thank you again, benderisgreat.  Adding sdb and sdc to the volume group was indeed pointless and stupid.  And so was thinking that I could get where I wanted (everything except boot in LVM and encrypted) from where I was.  That is, without reinstalling.

The key insights were: (1) keeping boot out of LVM and not encrypted; (2) creating matching partitions on each disk, and a RAID5 array from each set; (3) and encrypting the non-boot RAID5 array before adding it to the volume group.  Although it all seems so obvious now, it wasn't two days ago :redface:

Also, I did intend to nuke sdc with dd, in an attempt to force it to be "unbusy".  Doing so had no effect -- it was still "busy".  I now believe that was caused by sdc being the secondary drive on the second channel, with the CD ROM as primary.  Is that plausible?

How do I mark this solved?

---


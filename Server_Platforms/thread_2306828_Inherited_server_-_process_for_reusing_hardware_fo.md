---
title: "Inherited server - process for reusing hardware for RAID5"
date: 2015-12-19
forum: Server Platforms
---

### Post by Todzilla on 2015-12-19
Hi all

Having recently discovered Ubuntu, I am attempting to put my limited knowledge to the task of building a server. The hardware for the system was previously used for a similar application.

The problem I am experiencing relates to the building of a RAID array. Several attempts have been made to create the array, though part-way through construction the process fails. I am attempting to use 4 x 1TB drives in a RAID 5 configuration I am using Ubuntu 14.04 server from a new install.

Can anyone provide a suggested process for reusing the drives for this application, and for confirming additional system configuration settings?

Also, please advise of any system outputs required to assist with diagnosis/fault-finding. Any assistance is much appreciated!

---

### Post by ian-weisser on 2015-12-19
> **Todzilla said:**
> Several attempts have been made to create the array, though part-way through construction the process fails. I am attempting to use 4 x 1TB drives in a RAID 5 configuration I am using Ubuntu 14.04 server from a new install.

Please tell us what you know about these attempts, and what you know about the failures. 
Did you make the attempts? Someone else?
Hardware or Software RAID?
How did the attempter know about failure? Awful noise? Error message? Describe it in detail.

---

### Post by SeijiSensei on 2015-12-19
Quick overview if you're comfortable with the terminal:

1)  Use fdisk to create a single partition on each disk and mark them as type "fd" so they will be autodetected as RAID members during boot.  In fdisk, use the "t" command to set the type.  Do not format any of the drives as you'll be formatting the entire array later on.

2)  Next create the array with mdadm like this:
```
sudo mdadm --create /dev/md0 --level=5 --raid-devices=4 /dev/sd[defg]1
```
replacing "defg" with the drive letters assigned to each disk, e.g., /dev/sdd, /dev/sde, etc.  See "man mdadm" for details.

3)  Finally format the device with
```
sudo mkfs -t ext4 /dev/md0
```

---

### Post by darkod on 2015-12-19
I second what Sensei said, using mdadm SW raid would be much better in most cases. But you have to take into account that if we are talking about a branded server machine, sometimes they have a raid card or built-in onboard raid that does not allow passing the disks through as ordinary disks. Instead, it insists you have to build the array with its raid.

If you are lucky enough the board not to have any onboard raid, or that it can be disabled, that's perfect for using mdadm SW raid.

---

### Post by Todzilla on 2015-12-20
Thank you for the quick responses, and apologies for the lack of useful detail in the original post.

To clarify, I am using SW raid, with mdadm to create the array.

I have used the instructions kindly offered by Sensei, however, the following is returned upon attempting to create the array:

mdadm: super1.x cannot open /dev/sdd1: Device or resource busy
mdadm: /dev/sdd1 is not suitable for this array.
mdadm: create aborted

---

### Post by darkod on 2015-12-20
If several attempts have been made, you have to be sure that no disk is mounted or array (from old attempts) active. Also the zero the mdadm superblock on all partitions before you start the next attempt.

Check if any arrays are assembled with:
```
cat /proc/mdstat
```

If there are any, you have to stop them, zero the superblocks of partitions that are members, and maybe adjust mdadm.conf not to look to assemble that array any more.

One important thing: Are you doing this while doing the ubuntu installation or you already have the OS running on a separate disk and now are only trying to add an array for the data?

Because it sounds like your OS is already running. In such case sdd1 could be really used for something and busy... Make sure you are using the correct partitions.

---

### Post by SeijiSensei on 2015-12-20
Just to make sure, I was using /dev/sdd, etc., as examples.  How your drives are identified depends on how many there are.  You can list them like this:
```
seiji@linux:~$ dmesg | grep 'logical blocks'
[    0.921123] sd 0:0:0:0: [**sda**] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    0.922305] sd 4:0:0:0: [**sdb**] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)

```
Presumably you had to know these identifiers to use fdisk.

---

### Post by Todzilla on 2015-12-20
I have managed to identify that no disks are mounted or arrays active. After zeroing superblocks, the previously posted error with /dev/sdd1 did not present again, and creating the array commences:

md0 : active raid5 sde1[4] sdd1[2] sdc1[1] sdb1[0]

      2929890816 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [UUU_]

      [>....................]  recovery =  1.7% (17401856/976630272) finish=183.5min speed=87073K/sec


However, at the 5% completion mark, the process again fails:


Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sde1[4](F) sdd1[2](F) sdc1[1](F) sdb1[0](F)
      2929890816 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/0] [____]

unused devices: <none>


Darko, you are correct in assuming that the OS is installed and running on a separate disk (sda).

---

### Post by SeijiSensei on 2015-12-21
The underscore in [UUU_] indicates the last drive in the array, /dev/sdb1, has failed.  You can test this by changing raid-devices to three and leaving it out of the array.  Obviously you'll be giving up 1 TB of storage though. 

You can check the device's status by installing the **smartmontools** package and using smartctl to examine the drive's information.  If you have patience and you're not on deadline, you could run the badblocks utility which will scan the drive and mark bad sectors.  This will likely take a few days on a 1 TB drive.  Otherwise you'll probably need to replace the drive.

---

### Post by MAFoElffen on 2015-12-22
"process for reusing hardware for RAID5"

Looking back at this-- Good feed back so far. 

If mine, if using old disks, it depends on the types of disks and ow old they are. On some. I've done low level formats, then test and verify the disks, before even putting on a partition table. I do that even when using hardware RAID controllers and reusing old disks. On some. I'll partition and put on filesystems, just so I can test them  and see if it's going to hold up. They would get zero's when assembled... but in the meanwhile, will some me if it is worth trying. If I can test an old disk and mark out the bad sectors,

Just saying. Some testing is good. Soemetimes saves a lot of headaches later.

---

### Post by Todzilla on 2015-12-27
Thanks for the assistance so far. I've been offline for several days due to the holidays. SMART status of the drives indicates that they are all serviceable, however I have not run extended tests to indicate any disk errors. 
I have attempted to create the array with only 3 of the 4 drives, but still with no joy. Even omitting different drives results in a create failure at around the 5% mark. I intend to run more comprehensive testing of drives once I am able to access my system again (in another few days).

---


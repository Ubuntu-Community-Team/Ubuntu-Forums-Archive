---
title: "Bringing back data from RAID1 disks"
date: 2012-05-12
forum: Server Platforms
---

### Post by dellarovere on 2012-05-12
Hello Ubuntu Gurus!
I have a problem with my RAID disks and hope someone can help me.
I had a RAID1 configured on 10.04LTS. Unfortunately the system has died and I had to reinstall it.
After the reinstallation the Disk Utility was not correctly recognizing the old RAID array. I think that was because of my stupid decision to give the array the name with space in the middle and that name was stuck in the disks' superblocks. So, after looking around I have found that I can disassociate the disks from the RAID array. I thought I can take the old array apart and then reassemble it from the same components with a new normal name.
I have used mdadm --stop and the mdadm--zero-superblock (thinking, that it would only remove the RAID info form there).
The disks were "released" from the old RAID array, I was able to create a new RAID array, but I am now not seeing any partitions on the array.
I have not formatted disks and I have not formatted the array. But I am unable to mount disks separately, because mount does not recognize the filesystem. Interestingly, if I look at the disks in Disk Utility not as a parts of arrays, it says that there are partitions. But it does not recognize the types or anything.
Have I completely lost the data, or is there a way for me to recover anything?
Any suggestion is greatly appreciated.

---

### Post by darkod on 2012-05-12
I don't know enough to help you with your data recovery. I just want to say, I know you must be impatient but wait for someone who knows more to help you. Don't take any rush decisions. :)

I think the --zero-superblock messed it up since it will tell the disks they are no longer part of a raid array. But there might be a way to bring the data back, I just don't wanna play with it.

PS. I'll try to contact one expert for raid if he's available to help (and depending what his time zone is). :)

---

### Post by rubylaser on 2012-05-12
What are the exact commands that you ran? Zeroing the superblocks is not what you needed to do, but you can recover from it if you re-create the array with the exact same setup as before and you have to pass the --assume-clean option with the create.  If you didn't do that, your array would have resynced with a new setup, and unfortunately, your data is lost at this point.

You have unfortunately, messed with the block device which is just as bad as formatting the filesystem (actually this is worse, because you can still recover data from a formatted filesystem, unless you overwrite the data).

Please let me know what commands you ran.  You can get them like this from the user you ran the commands under.
```
history | grep mdadm
```

---

### Post by rubylaser on 2012-05-12
I just re-read this and realized they're RAID1 disks, so even without mdadm setup properly, you should be able to read the data on the disks  (I just woke up and have the kids climbing all over me, so I'm not at 100% yet).  Unless you formatted these disks as part of the install.  What's the output of 
```
fdisk -l
```
what disks are causing the problem (/dev/sdb, /dev/sdc, etc?)

The good news, is even if you can't get the filesystem to mount (you should be able to), you can use a recovery tool like photorec or scalpel.

---

### Post by dellarovere on 2012-05-12
Thank you very much for encouraging news.

I am interested in [FONT="Courier New"]/dev/sdc1[/FONT] and/or [FONT="Courier New"]/dev/sdd1[/FONT] as they should be identical.

Here is what has been done.
Originally I had the RAID array name as New RAID Array so I have run:


```
mdadm --stop "/dev/md/New RAID Array"
```

That did not work, so I thought I would change the name in [FONT="Courier New"]/etc/mdadm/mdadm.conf[/FONT] to just New and tried again:

```
mdadm --stop "/dev/md/New"
```

That did not work again.

I tried more things:
```
   29  mdadm --assemble /dev/md/New 
   33  mdadm --build /dev/md/New 
   34  mdadm --build /dev/md/md0
   35  mdadm --assemble /dev/md/md0
   36  mdadm --create /dev/md/md0

```

Finally I got to
```
   99  sudo mdadm --examine /dev/md0
  100  sudo mdadm --examine /dev/sdb1
  101  sudo mdadm --examine /dev/sdc1
  102  sudo mdadm --examine /dev/sdd1
  103  sudo mdadm /dev/md0 --stop
  106  sudo mdadm --zero-superblock /dev/sdc1
  107  sudo mdadm --zero-superblock --force /dev/sdc1
  108  sudo mdadm --zero-superblock --force /dev/sdd1
  109  sudo mdadm --zero-superblock --force /dev/sdb1

  125  sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdc1 /dev/sdd1
  126  mdadm --assemble /dev/md0 /dev/sdc1 /dev/sdd1
  127  sudo mdadm --assemble /dev/md0 /dev/sdc1 /dev/sdd1

```

I have not done anyt formatting on [FONT="Courier New"]/dev/sdc[/FONT] or [FONT="Courier New"]/dev/sdd[/FONT] and [FONT="Courier New"]fdisk[/FONT] shows the following:

```


$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ef864

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18895   151768064   83  Linux
/dev/sda2           18895       19458     4519937    5  Extended
/dev/sda5           18895       19458     4519936   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b4de3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5c9a2851

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001   83  Linux

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x73d751ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      182401  1465136001   83  Linux

```

So, supposedly, the data is still there?

Thank you very much!

---

### Post by darkod on 2012-05-12
rubylaser is the expert so lets wait for his verdict. I can't say it's hopeless, but it seems to me it's a big mess the least.

I especially don't like line 125, the mdadm --create you did. You use --create ONLY the first time, when you create the array.
After that, if you intend to keep the data and use the same array, you only assemble it with --assemble. You NEVER run --create again on the same array.
Of course, there are specific exceptions, when you have no other option left, and you can use --create but with another option, --assume-clean which sort of tells it to create new array but in a way use the old one.

Since you simply used --create you created a new array over the old one. But maybe rubylaser knows of a way to get the data back.

I also don't like what fdisk says about sdc1 and sdd1 because they are reported with id '83', standard linux partition. As members of software raid, regardless if it's the new array you created, they should be id 'fd' if I remember correctly, linux raid member.

But again, this might be nothing. In many cases you can simply change the id and they can be recognized as partitions members of the raid. The mdadm --create is getting me more worried.

---

### Post by rubylaser on 2012-05-12
Unfortunately, Darkod is correct.  A create without the --assume-clean option would have caused the disks to sync and would have overwritten the data.  Your only solution at this point would be a file carver like photorec or scalpel from the LiveCD.

---

### Post by darkod on 2012-05-12
> **rubylaser said:**
> Unfortunately, Darkod is correct.  A create without the --assume-clean option would have caused the disks to sync and would have overwritten the data.  Your only solution at this point would be a file carver like photorec or scalpel from the LiveCD.

And what if they never synced?

Because even the new array is not working right now. What if it never worked? Any chance?

On the other hand, the create command from history looks correctly issued, maybe the second array was broken somehow later too. But if it synced when it was issued...

---

### Post by rubylaser on 2012-05-12
Even if it started, it's likely that it screwed the filesystem up.  What's the output of these?

```
cat /proc/mdstat
```
and 
```
mdadm -E /dev/sd[cd]1
```

---

### Post by dellarovere on 2012-05-12
Actually after I have tried creating the new array and it did not work I have run zero-superblock again.

Currently, I get the following outputs:


```
$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>
$ sudo mdadm -E /dev/sd[cd]1
mdadm: No md superblock detected on /dev/sdc1.
mdadm: No md superblock detected on /dev/sdd1.

```

Thank you.

I will start reading manual for data recovery tools.

---

### Post by rubylaser on 2012-05-13
You are correct, you have no superblock metadata on either disk, so they are not  part of an array. What does this give you? 

```
mkdir -p /mnt/sdc
mkdir /mnt/sdd
mount /dev/sdc1 /mnt[/sdc
mount /dev/sdd1 /mnt/sdd
cd /mnt/sdc
ls
```

Was the filesystem ext4 on these disks?

---

### Post by dellarovere on 2012-05-14
Thank you very much for your help.

Here are the results for [FONT="Courier New"]/dev/sdc[/FONT]. The result for [FONT="Courier New"]/dev/sdd[/FONT] are the same.

```
$ sudo mkdir -p /mnt/sdc
greza@piter:~$ sudo mount /dev/sdc1 /mnt/sdc
mount: you must specify the filesystem type
$ sudo mount -t ext4 /dev/sdc1 /mnt/sdc

$ sudo mount -t ext4 /dev/sdc1 /mnt/sdc
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$ sudo mount -t ext3 /dev/sdc1 /mnt/sdc
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$ sudo mount -t ext2 /dev/sdc1 /mnt/sdc
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$ dmesg | tail
[   16.424149]    groups: 0-1 (cpu_power = 1178)
[   16.424162] CPU1 attaching sched-domain:
[   16.424167]  domain 0: span 0-1 level SIBLING
[   16.424173]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   16.424186]   domain 1: span 0-1 level MC
[   16.424191]    groups: 0-1 (cpu_power = 1178)
[   22.604011] eth1: no IPv6 routers present
[  884.252767] EXT4-fs (sdc1): VFS: Can't find ext4 filesystem
[  900.400780] VFS: Can't find ext3 filesystem on dev sdc1.
[  905.040331] VFS: Can't find an ext2 filesystem on dev sdc1.

```

I have also been able to start the file restoration utilities and they are able to recover files. But the files are all with 
funny names and obviously, this is the least desirable path.

Also, if you do not mind, could you explain to me when exactly I have messed up and what I should have done differently in order to get the RAID up and working again with all the data preserved?

I have an uneasy feeling, that I might go through this exercise again in the future and would like to avoid these problems.
Thank you very much.

---

### Post by rubylaser on 2012-05-14
My first obvious suggestion is to have a backup strategy.  A 160GB drive is very small by today's standards and is very easily backed up. Also, zeroing the superblocks and re-creating the array should be the last thing you try.  You should have first stopped any running arrays, and then force assembled the array.  If that didn't work, you had a bigger problem on your hands, and you should then move to mounting the individual disk in a LiveCD and recover all of the data.

I'm glad you're able to recover your files, but you are correct that this is the least desirable way to do it.

---


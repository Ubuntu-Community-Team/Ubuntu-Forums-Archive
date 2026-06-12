---
title: "mhddfs segfault"
date: 2014-11-28
forum: Server Platforms
---

### Post by MakOwner on 2014-11-28
I was copying some data onto an mhddfs mount when the copy stopped with an error about "underlying endpoint no longer exists" and the following message is in the dmesg log:

```

mhddfs[17027]: segfault at 0 ip 0000000000404750 sp 00007ff2277fda40 error 4 in mhddfs[400000+b000]

```

The underlying volumes and filesystems are all mounted with no issue, and this appear to be the only error I can find.

---

### Post by rubylaser on 2014-11-28
About the easiest way to track this down is to mount your mhddfs pool with the logfile option and try to re-create the issue.  Here's how you set it up in your /etc/fstab
```

mhddfs#/media/disk1,/media/disk2,/media/disk3,/media/disk4 /storage fuse defaults,allow_other,nonempty,logfile=/var/log/mhddfs.log 0 0

```

This will create a logfile in /var/log/mhddfs.log

I have seen other's having issues with mhddfs when rsyncing to the pool. 
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=728310](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=728310)

I really wish there was a good kernel based pooling solution on Linux.  AUFS is fast and lightweight, but you have issues with whiteout and opaque files and the need to compile a custom kernel to get NFS exports.  And, mhddfs works really well, but it's FUSE based, so it's slower, harder on the CPU, and users occasionally run into segfaults like you have.

---

### Post by MakOwner on 2014-11-28
I forced a umount and was able to remount without re-booting.
I'm running this with snapraid and then using mhddfs on all of the snapraid non-parity volumes.

I was copying some data from one location in the mhddfs filesystem to another when the issue occurred - I set it up and did the copy again (with no overwrites) and it ran without issue.
It is slow, but I can live with the speed if I can get this built out and test some failure and recovery scenarios.
I have had to start over with snapraid a couple of times because somehow mhddfs will allow a disk volume to fill to the point that snapraid will no longer build out the partiy file complaining it has no more room.

---

### Post by rubylaser on 2014-11-28
Did you create the ext4 filesystem on the parity drive with the largefile option?  This will cause you to lose some inodes, but will still leave plenty for a fileserver, while freeing up many GB of extra storage space.
```

mkfs.ext4 -m 0 -T largefile4 /dev/sdb1

```
You can also use the mlimit=10G on your mhddfs mount point to prevent disks from filling beyond a certain point (set the 10G to whatever amount you'd like it to stop at).

---

### Post by MakOwner on 2014-11-29
The fallocate error is back for snapraid.
I'll try reformatting the two parity volumes as you suggested, but it appears that after a certain amount of data is added, it just craps out and can't big enouhg parity files.

---

### Post by MakOwner on 2014-11-29
That doesn't do the trick either.

```

Saving state to /var/snapraid.content...
Saving state to /mnt/6XW0QL54d01/snapraid.content1...
Saving state to /mnt/6YD05MN6d02/snapraid.content2...
Initializing...
Failed to grow parity file '/mnt/9XW05B85p01/snapraid-1.parity' to size 1503405015040 using fallocate due lack of space.
Files outside the parity:
outofparity /mnt/9XW06E43d04/md5/file_server/ISO/CentOS/CentOS-5.2/CentOS-5.2-x86_64-bin-DVD.iso
WARNING! Without an accessible Parity file, it isn't possible to sync.

```


These are the filesystems/volumes i'm trying to work with for snapraid.
The two parity volumes are the largest two volumes.

/mnt/9XW05B85p01
/mnt/6XW0SK9Wp02

```

Filesystem              1K-blocks       Used  Available Use% Mounted on
/dev/sdj1              1442015700   76927736 1321117456   6% /mnt/6XW05PT6d06
/dev/sdl1              1442015700 1394655688    3389504 100% /mnt/6XW0QL54d01
/dev/sdd1              1464820860      71160 1464733316   1% /mnt/6XW0SK9Wp02
/dev/sdf1              1442015700  918548588  450193852  68% /mnt/6XW0V05Fd05
/dev/sdm1              1442015700 1395215772    2829420 100% /mnt/6YD05MN6d02
/dev/sdk1               384484896      19476  380550126   1% /mnt/9NF0D77Td08
/dev/sdc1               961302560      73364  931909968   1% /mnt/9VP3XWNHd09
/dev/sdi1              1442015700      71160 1397974032   1% /mnt/9XW04HNTd07
/dev/sdh1              1464820860 1464804476          0 100% /mnt/9XW05B85p01
/dev/sde1              1442015700 1368820084          0 100% /mnt/9XW06DVMd03
/dev/sdg1              1442015700 1397016600    1028592 100% /mnt/9XW06E43d04

```

---

### Post by MakOwner on 2014-11-29
So I went back and removed some data from the volumes that were the closest to 100% utilzation, removed all the snapraid content and parity files and restarted sync.
It's syncing now, rather than erroring with the 'can't allocate capacity' on the first parity file.

To me, that's a pretty big issue in that you could potentially fill a protected volume up to a point where snapraid just breaks.
Unless I just don't see it in the table above, to me it looks like the parity drives have more bites available on the parity drives than any other data drive.

---

### Post by rubylaser on 2014-11-29
Parity has overhead based on the block_size in your configuration file.  You need to have extra room for the parity to fit (I'd leave at least 10GB of free space on a data disk at a minimum).  Also, if you have many small files, there will be more overhead, because each file takes up at least as much space as your block_size (default is 256KB).  

The outofparity warnings tell you exactly what files on what disk are making the parity too large to hold on your parity disks.  Just move those files to another disk to create room, and then mount the mhddfs pool with the mlimit=10G option and you shouldn't have an issue with mhddfs filling a data disk beyond the point the SnapRAID can hold the parity.

---

### Post by MakOwner on 2014-11-29
I'm copying data in with many small files right now, and with an mlimit=5G I still get snapraid failures with allocating the first parity file.
Does mhddfs honor the mlimit for root?

Here's the scenario:

mhddfs is aet for an mlimit of 5G, and writes weel past that point on a number of file systems - which is what it is, I suppose, but snapraid then fails sync on not-the-fullest volume.


```


Filesystem              1K-blocks       Used  Available Use% Mounted on
/dev/sdj1              1442015700   85103912 1312941280   7% /mnt/6XW05PT6d06
/dev/sdl1              1442015700 1394692768    3352424 100% /mnt/6XW0QL54d01
/dev/sdd1              1464820860 1435498572   29305904  98% /mnt/6XW0SK9Wp02
/dev/sdf1              1442015700 1364952616    3789824 100% /mnt/6XW0V05Fd05
/dev/sdm1              1442015700 1395252852    2792340 100% /mnt/6YD05MN6d02
/dev/sdk1               384484896      19476  380550126   1% /mnt/9NF0D77Td08
/dev/sdc1               961302560      73364  931909968   1% /mnt/9VP3XWNHd09
/dev/sdi1              1442015700      71160 1397974032   1% /mnt/9XW04HNTd07
/dev/sdh1              1464820860 1464804476          0 100% /mnt/9XW05B85p01
/dev/sde1              1442015700 1365980008    2762432 100% /mnt/9XW06DVMd03
/dev/sdg1              1442015700 1394167188    3878004 100% /mnt/9XW06E43d04

```


snapraid fails here:

```

Failed to grow parity file '/mnt/9XW05B85p01/snapraid-1.parity' to size 1500491546624 using fallocate due lack of space.
Files outside the parity:
outofparity /mnt/9XW06E43d04/md5/file_server/ISO/CentOS/CentOS-4.92/CentOS-4.92-i386-bin-4of6.iso
WARNING! Without an accessible Parity file, it isn't possible to sync.

```


I note that disk 4, (/mnt/9XW06E43d04) has 3,878,004 1k blocks free, yet disk 2 (/mnt/6YD05MN6d02) has only 2,792,340 1k blocks free.
It doesn't cause the failure, disk 4 does.

Both are comprised of exactly 144,2015,700 1k blocks, and both parity disks report 1,464,820,860 1k blocks.


mhddfs bypassing the 5G free space limit is obviously causing issues, but it's really aggravating space issues in snapraid.

---

### Post by rubylaser on 2014-11-29
Yes it does honor the mlimit even for root. You probably want to set a larger mlimit than 5GB with many small files.

---

### Post by MakOwner on 2014-11-30
Forgive me for all the dumb questions, but this one occurred to me today -- if one is to move to larger drives with snapraid, you would replace the two drives with parity files on them first.
I have noticed that the drive UUID is tied to the parity and content, such that it seems that simply copying the parity file off to a new drive, adding to the config, and the running a sync might not suffice for the process.

In my limited amount of testing it seems the --force_empty directive for the sync command (Whihc would be used for any intended disk replacement) essentially forces a sync from scratch over the whole assemblage of drives - is that correct?

Is there another procedure I'm missing?  Some command that foces the assumption of the location of the moved parity file?

---

### Post by rubylaser on 2014-12-01
> **MakOwner said:**
> Forgive me for all the dumb questions, but this one occurred to me today -- if one is to move to larger drives with snapraid, you would replace the two drives with parity files on them first.
I have noticed that the drive UUID is tied to the parity and content, such that it seems that simply copying the parity file off to a new drive, adding to the config, and the running a sync might not suffice for the process.

In my limited amount of testing it seems the --force_empty directive for the sync command (Whihc would be used for any intended disk replacement) essentially forces a sync from scratch over the whole assemblage of drives - is that correct?

Is there another procedure I'm missing?  Some command that foces the assumption of the location of the moved parity file?

SnapRAID handles this situation very well (I've upsized my parity drives 2 times now).  All you need to do is rsync your current parity file to your formatted, new larger disk. Once done, you replace the references to the old smaller parity disk with the new bigger one, and run a snapraid diff.  Everything should "just work" and there should be no reason for a new, complete parity calculation.

---

### Post by MakOwner on 2014-12-08
I'm having issues getting more than one option set for the mhddfs mount.

so this is the example from the man page:
```

 mhddfs#/dir1,/dir2,/dir3 /mnt fuse logfile=/var/log/mhddfs.log 0 0

```

I want to have the logfile option along with the mlimit= option, but when I add it using either spaces or commas (like other filesystems separate options) the mount fails...


Any suggestions?

---

### Post by rubylaser on 2014-12-09
> **MakOwner said:**
> I'm having issues getting more than one option set for the mhddfs mount.

so this is the example from the man page:
```

 mhddfs#/dir1,/dir2,/dir3 /mnt fuse logfile=/var/log/mhddfs.log 0 0

```

I want to have the logfile option along with the mlimit= option, but when I add it using either spaces or commas (like other filesystems separate options) the mount fails...


Any suggestions?

Yes, the format for /etc/fstab needs to look like this.
```

mhddfs#/media/disk1,/media/disk2,/media/disk3,/media/disk4 /storage fuse defaults,allow_other,nonempty,mlimit=10G,logfile=/var/log/mhddfs.log 0 0

```

---

### Post by MakOwner on 2014-12-09
Interesting.  I cut-and-paste'd what you had and it works, when I typed that in manually it didn't.
Typo, I'm sure.  

Anyway the segfault is back.  Appears to occur after a certain number of attempts by midnight commander to handle an already existing symlink in the filesystem to be copied.
What that has to do with anything I don't know, but after a number of "skip" iterations it causes mhddfs to crash.

---

### Post by rubylaser on 2014-12-09
If you wanted to give it a try.  I'm currently back to using AUFS.  I've compiled it myself to support hnotify (I have a reference to how to do it in my SnapRAID tutorial in my signature).  So far, it seems to work really well (still testing for the last few weeks).  I've seen this segfault issue only once on mhddfs volumes, so I'm not a wealth of knowledge here.  Also, there is almost no documentation or discussion about it, so troubleshooting can be difficult.

---

### Post by MakOwner on 2014-12-10
So far, I like the relative simplicity of mhddfs+snapraid, It may just be that mc's inability to properly handle the symlinks in the filesystem is aggravating mhddfs.  I'll be testing using rsync later.

I just ran across an issue with multiple parity disks -- I had a spare disk that was larger than all the other disks in the snapraid configuration, so I moved one of the parity files to the new disk.
I ran check, scrub and sync after changing the disk out, and everything worked fine.

I added some more data to the disks and now sync fails with an out-of-parity message.
I delete the data added and sync works again.

With all data disks 1.5TB or less, and and one parity disk at 1.5 and one at 2TB, this is not a valid configuration, and the parity will grow beyond the size of the 1.5TB drive.

Have you found this to be the case?

---

### Post by rubylaser on 2014-12-10
> **MakOwner said:**
> 
With all data disks 1.5TB or less, and and one parity disk at 1.5 and one at 2TB, this is not a valid configuration, and the parity will grow beyond the size of the 1.5TB drive.

Have you found this to be the case?

How full are your 1.5TB data disks?  I would assume that one or many of them are completely full, and there isn't enough room on the 1.5TB parity disk to hold all the parity (the 2TB disk should be fine).

---

### Post by MakOwner on 2014-12-10
Parity disk end with p0N and data disks end with dNN

This is with a 10G mlimit for mhddfs.
I'm trying again with a 15G limit.


```

Filesystem	Size	Used	Avail	Use%	Mounted
/dev/sdn1	1.9T	1.4T	377G	79%	/mnt/JK1130YAHPL3RTp01
/dev/sdd1	1.4T	1.4T	3.5G	100%	/mnt/6XW0SK9Wp02
/dev/sdl1	1.4T	1.3T	8.9G	100%	/mnt/6XW0QL54d01
/dev/sdm1	1.4T	1.3T	2.6G	100%	/mnt/6YD05MN6d02
/dev/sdh1	1.4T	1.3T	97G	94%	/mnt/9XW05B85d03
/dev/sdg1	1.4T	1.3T	7.8G	100%	/mnt/9XW06E43d04
/dev/sdf1	1.4T	1.3T	6.3G	100%	/mnt/6XW0V05Fd05
/dev/sdj1	1.4T	1014G	320G	77%	/mnt/6XW05PT6d06
/dev/sdi1	1.4T	70M	1.4T	1%	/mnt/9XW04HNTd07
/dev/sde1	1.4T	70M	1.3T	1%	/mnt/9XW06DVMd08
/dev/sdc1	917G	72M	889G	1%	/mnt/9VP3XWNHd17
/dev/sdk1	367G	20M	363G	1%	/mnt/9NF0D77Td18

```

---

### Post by MakOwner on 2014-12-10
Even with 20G available on the disk it complains about, it still fails.

---

### Post by rubylaser on 2014-12-11
You will have to manually move files off the data disks that are too full.  Move about 20GB off /mnt/6XW0QL54d01, /mnt/6YD05MN6d02, /mnt/9XW06E43d04, /mnt/6XW0V05Fd05 onto one of your disks with lots of free space like /mnt/9XW04HNTd07.  Then the sync should succeed.  mhddfs won't re-balance files with the mlimit setting.  It only uses this limit on writing new files.  The disks above are all basically full and would prevent the parity from fitting on a similarly sized disk.

---

### Post by MakOwner on 2014-12-15
Figured it out -- I think.
So, mhddfs ignores the mlimit for the root account and will allow each drives to fill past the mlimit setting.
Aside from this, I suspect any user doing writes on the mhddfs volume when the volume is nearing capacity will be able to override the mlimit too, as mhddfs appears to allow writes to the disk with the most free space, and favors accepting a write over failing a write if there is physical space to accept the write.  

For root, this means because the root user can even write into the root reserve created when you format an ext4 volume for each volume, making the issue worse.

Just a guess, I really don't know - but when I set it up for a non-privileged user to do a large amount of writes into a the mhddfs volume, I get nice even amounts of free space on each volume, but having root write the same data, with the same mlimit setting I get very close to 0 space left on each disk.

---

### Post by Ram_N on 2015-09-23
> **MakOwner said:**
> I was copying some data onto an mhddfs mount when the copy stopped with an error about "underlying endpoint no longer exists" and the following message is in the dmesg log:

```

mhddfs[17027]: segfault at 0 ip 0000000000404750 sp 00007ff2277fda40 error 4 in mhddfs[400000+b000]

```

The underlying volumes and filesystems are all mounted with no issue, and this appear to be the only error I can find.

This was a bug introduced in version 1.39 of mhddfs - I have a fixed version running on my home server now. You can see the patch here - [https://github.com/ram-nat/mhddfs/commit/26d0f119eaa7e3ffaaf330bf29672e13471cb091](https://github.com/ram-nat/mhddfs/commit/26d0f119eaa7e3ffaaf330bf29672e13471cb091)

---

### Post by rubylaser on 2015-10-24
[COLOR=#545454][FONT=Helvetica Neue]For anyone struggling with disconnects with mhddfs, I'd suggest to tryout mergerfs. I have switched away from both AuFS and mhddfs to mergerfs and it works great. It is actively developed, does not segfault and has very good performance for a FUSE based filesystem. I have a simple tutorial that walks through configuring it.[/FONT][/COLOR]
[COLOR=#545454][FONT=Helvetica Neue][http://zackreed.me/articles/92-mergerfs-another-good-option-to-pool-your-snapraid-disks](http://zackreed.me/articles/92-mergerfs-another-good-option-to-pool-your-snapraid-disks)[/FONT][/COLOR]

---


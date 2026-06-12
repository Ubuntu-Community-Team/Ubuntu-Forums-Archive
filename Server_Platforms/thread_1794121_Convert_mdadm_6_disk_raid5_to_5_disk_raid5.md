---
title: "Convert mdadm 6 disk raid5 to 5 disk raid5"
date: 2011-06-30
forum: Server Platforms
---

### Post by dmwyatt on 2011-06-30
I know you can fail and then remove a drive from a RAID5 array.  This leaves the array in a degraded state.

How can you remove a drive and convert the array to just a regular, clean array?

---

### Post by rubylaser on 2011-06-30
Yes, you can do this.  You'll need a newer version of mdadm (>3.1, and kernel >2.6.31), and you'll need to make sure that your filesystem isn't taking up more space than you're going to shrink to.  Can you give the output of these commands?

```
mdadm -V
```

```
mdadm --detail /dev/<your_array_here_probably_md0>
```

```
df -h
```

And this...
```
mount
```

You'll definitely want backups of your important data before trying this.

---

### Post by dmwyatt on 2011-06-30
```
therms@EHUD:~$ mdadm -V
mdadm - v3.1.4 - 31st August 2010
```

```
therms@EHUD:~$ sudo mdadm --detail /dev/md3
[sudo] password for therms:
/dev/md3:
        Version : 1.2
  Creation Time : Sat Dec 11 16:05:27 2010
     Raid Level : raid5
     Array Size : 9767559040 (9315.07 GiB 10001.98 GB)
  Used Dev Size : 1953511808 (1863.01 GiB 2000.40 GB)
   Raid Devices : 6
  Total Devices : 6
    Persistence : Superblock is persistent

    Update Time : Thu Jun 30 17:51:52 2011
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 128K

           Name : EHUD:3  (local to host EHUD)
           UUID : 593eca07:3723b8eb:4a11dd0b:6b750414
         Events : 40873

    Number   Major   Minor   RaidDevice State
       0       8       97        0      active sync   /dev/sdg1
       1       8      161        1      active sync   /dev/sdk1
       3       8      193        2      active sync   /dev/sdm1
       4       8      177        3      active sync   /dev/sdl1
       5       8       17        4      active sync   /dev/sdb1
       6       8       33        5      active sync   /dev/sdc1

```
```
therms@EHUD:~$ mount
/dev/md1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/mapper/vg_pool-pool on /media/LVM Pool type ext4 (rw,nosuid,nodev,uhelper=udisks)
```

The array is currently part of a LVM.  I know I'll need to take care of that first...

---

### Post by rubylaser on 2011-06-30
Yup, since I'm not sure how much of your filesystem is currently in use (need output of df -h), it's hard to know how much you can safely reduce, but the first step is to actually reduce the filesytem, then, you'll need to resize the LVM, then adjust the mdadm array-size, next reduce the number of disks in your array, and finally expand the LVM and then the filesystem to max size again. Like I said, this is involved :)

Here's roughly how you start, once you have a backup of your important data, and you've confirmed available space.

Unmount, and run a filesystem check
```
umount /media/LVM
fsck.ext4 /dev/mapper/vg_pool-pool
```

Then, resize the filesystem make this slightly smaller than you'll resize the LVM to...
```
resize2fs /dev/mapper/vg_pool-pool <size_in_GB_here>G
```

Now, reduce the LVM size...
```
lvreduce -L<size_in_GB_her>G /dev/mapper/vg_pool-pool
```

Now, you can dive into mdadm :)  First change the array-size.  This does not survive a reboot, so we'll do this all in one session.
```
mdadm /dev/md3 --grow --array-size=<new_size_in_bytes_ie_8000000000>
```

Next, you'll need to reduce the number of disks.
```
mdadm /dev/md3 --grow --raid-devices=5 --backup-file=/root/backup
```

Watch the progress
```
cat /proc/mdstat
```
You should end up with a 5 disk RAID5 + 1 hot spare.

Then, remove the hot spare.
```
mdadm --remove /dev/mdX /dev/sdX1
```

Finally, you'll need to grow your LVM back to take up the whole array, and then extend your filesystem likewise.   I have not tested these steps in a virtual machine, but this should give you the idea.  Again, please backup first, then test this in a VM, and finally try it on your real array :)

EDIT: See, I knew I'd forget something, you'll need to reduce the volume group too, prior to shrinking the array (vgreduce)

---

### Post by dmwyatt on 2011-06-30
> **rubylaser said:**
> helpful info

Thanks.  You gave me just the info I needed!

There's no worry about the filesystem size.  The whole reason I need to do this is that I just added the drive to the mdadm array and then found out that I couldn't expand my LVM's ext4 filesystem because it would be larger than 16TB.  See [this thread]("http://ubuntuforums.org/showthread.php?t=1791544") for info about that.

---

### Post by rubylaser on 2011-06-30
Ah, I posted in that thread too, I should have recognized your username.  Hope you can get this working properly.  Good Luck :)

---

### Post by dmwyatt on 2011-07-24
I finally got around to working on this.

I wanted to mention a potential snafu:  The --array-size command takes its parameter in what I think are blocks...*not* in bytes!

If you do:
```
mdadm --detail /dev/md3
``` it will give you:

```
Array Size : 7814047232 (7452.06 GiB 8001.58 GB)
  Used Dev Size : 1953511808 (1863.01 GiB 2000.40 GB)
```

This is the available storage space and the amount used for parity...in a RAID-5 of equal-size disks the parity size is equal to the disk size, so to arrive at the amount to use for --array-size just use ```
parity size * (number of disks you want in the array - 1)
```

---

### Post by rubylaser on 2011-07-25
According to Neil Brown, the developer of mdadm, you don't even need to give mdadm the array size, it calculates it from the number of disks.
[http://www.spinics.net/lists/raid/msg28628.html]("http://www.spinics.net/lists/raid/msg28628.html")

---

### Post by dmwyatt on 2011-08-04
As I just got around to finishing this after waiting 7 days(!) for the md grow operation to finish, I wanted to mention one more caveat for anyone following rubylasers excellent instructions:

This:
```
mdadm  --remove /dev/sdX1
```

should be:

```
mdadm --remove /dev/mdX /dev/sdX1
```


Otherwise everything he mentioned was great, and I owe him my thanks!

---

### Post by rubylaser on 2011-08-04
Great, I'm glad that worked. I'm going to edit my post so that someone doesn't miss that as part of the steps.  7 days is crazy :O  I reshaped mine from a 6 disk RAID5 to a 7 disk RAID6, and it took about 6 hours.  Shrinking must be substantially slower.

---

### Post by dmwyatt on 2011-08-04
I think I spoke a little too soon.

LVM was working fine while I just had the spare in the one array.  I removed the spare (I'm sure I got the right one), but now I can't mount my LVM volume.

If I do a pvdisplay, the md3 array shows this:

```
--- Physical volume ---
  PV Name               /dev/md3
  VG Name               vg_pool
  PV Size               7.27 EiB / not usable 6.00 EiB
  Allocatable           yes
  PE Size               512.00 MiB
  Total PE              2732729023
  Free PE               2732710393
  Allocated PE          18630
  PV UUID               TRI8OY-eG5q-Tyn2-dwbl-oHwq-ibUi-uzEwfj

```

That's obviously not right, but I can't find anything via some Googlin' about mis-reported PV sizes.

edit:  Not sure how it happened, but I fixed it by restoring a metadata backup from before I ever attempted to add this hard drive to begin with.  Used **vcfgrestore**.

---

### Post by rubylaser on 2011-08-04
Glad you got it figured out.  It was either an error, or the server fairies installed a whole bunch of hard drives to get you up to 8 exabytes :)

---

### Post by mosteo on 2012-10-31
Excuse me for chiming in so late in the party. I was researching this scenario and see two potential problems in these (otherwise excellent) steps. I might be wrong, obviously.

Both are related to the shrinking of the pv.

First, vgreduce will remove unused pvs, but an underlying raid device is a single pv, so it will have no effect.

There is, however, a pvresize that allows setting the size of a pv. And some bits in the man page spell trouble:

[FONT="Courier New"][INDENT]RESTRICTIONS
       pvresize will refuse to shrink PhysicalVolume if it has allocated extents after where its new end would be. In the future, it should relocate  these elsewhere in the volume group if there is sufficient free space, like pvmove does.[/INDENT][/FONT]

My interpretation of this is that, even if our lv is now smaller, it might be spread all over the pv. So resizing the array (which is the only pv in play) in this case could mean data loss.

A second point to draw from the above text is that, with the current pvresize command, you might be able to get away with the shrink, but only if your data is (by chance?) physically already only in the parts of the raid that will remain. Otherwise, you won't be able to do the pvresize, and doing the raid reduction would imply data loss.

An indication of the above concerns is that after lvreduce, vgs will still show the full size of the pv (the raid prior to shrink).

I'm pretty new to this, so I might be totally wrong on any of the above. Your thoughts?

---

### Post by mosteo on 2012-10-31
After re-reading your posts, I see the last from @dmwyatt is probably related to what I said. We need to use pvresize to tell lvm what will be the new physical device size once reduced as the last step before mdadm --grow

---

### Post by rubylaser on 2012-10-31
> **mosteo said:**
> After re-reading your posts, I see the last from @dmwyatt is probably related to what I said. We need to use pvresize to tell lvm what will be the new physical device size once reduced as the last step before mdadm --grow

That's a good point and thank you for following up.  This thread shows a very complicated process and one that I really wouldn't even try myself.  Even breaking the array and restoring 8TB from backup would be faster than the 7 day resize that this process took :)

As a sidenote, most home users needing to store this much data are probably trying to store movies and tv shows.  [Snapraid]("http://snapraid.sourceforge.net/") or something like that is probably a better fit.

---


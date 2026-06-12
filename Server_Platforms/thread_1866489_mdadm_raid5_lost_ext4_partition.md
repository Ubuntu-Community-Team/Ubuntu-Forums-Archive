---
title: "mdadm raid5 lost ext4 partition?"
date: 2011-10-21
forum: Server Platforms
---

### Post by zackiv31 on 2011-10-21
So I had a RAID 5 drop a faulty disk and I couldn't get it to come back online.  I performed the following steps to try to rebuild the array correctly:

```

zivester@zives:~$ sudo mdadm --assemble --scan
mdadm: /dev/md0 assembled from 3 drives and 1 spare - not enough to start the array while not clean - consider --force.

zivester@zives:~$ sudo mdadm --create /dev/md0 --assume-clean --level=5 --verbose --raid-devices=4 /dev/sda1 /dev/sdb1 missing /dev/sdd1
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: /dev/sda1 appears to contain an ext2fs file system
    size=-2097251584K  mtime=Mon Oct 17 00:54:31 2011
mdadm: /dev/sda1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Thu Apr 22 20:18:49 2010
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Thu Apr 22 20:18:49 2010
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdd1 appears to contain an ext2fs file system
    size=-1828816128K  mtime=Mon Oct 17 00:45:44 2011
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Thu Apr 22 20:18:49 2010
mdadm: size set to 732570624K
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.

zivester@zives:~$ sudo mdadm --manage /dev/md0 --add /dev/sdc1
mdadm: added /dev/sdc1

```

At this point, I let it rebuild... and all seem to be well (don't worry about the sd[abcd] -> sd[cdef]) My motherboard renamed them when I rebooted.  sdc was the original drive that got kicked out, which is now sde.

```

zivester@zives:/media/bigdisk$ sudo mdadm --detail /dev/md0 
/dev/md0:
        Version : 1.2
  Creation Time : Wed Oct 19 23:43:59 2011
     Raid Level : raid5
     Array Size : 2197711872 (2095.90 GiB 2250.46 GB)
  Used Dev Size : 732570624 (698.63 GiB 750.15 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Thu Oct 20 09:22:57 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : zives:0  (local to host zives)
           UUID : c3911b4c:edf367dd:cb56d8a4:987ba3e1
         Events : 25

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       49        1      active sync   /dev/sdd1
       4       8       65        2      active sync   /dev/sde1
       3       8       81        3      active sync   /dev/sdf1


zivester@zives:/media/bigdisk$ cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid5 sdc1[0] sdf1[3] sde1[4] sdd1[1]
      2197711872 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>

```


But when I try to mount the array, which use to have an ext4 partition on it, it gives me this:
```

zivester@zives:/media/bigdisk$ sudo mount /media/bigdisk
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```


Did I do something wrong?  Is my ext4 partition still there?  Any information to help me try to get this ext4 partition back would be appreciated!

---

### Post by vasile002 on 2011-10-22
When the --create command is used the raid array is recreated and all the contents of the drives are wiped out. No, your ext4 partition is no longer there

---

### Post by BeowulfNode on 2011-10-22
> **vasile002 said:**
> When the --create command is used the raid array is recreated and all the contents of the drives are wiped out. 
except when using the --assume-clean option, then no data is changed until you write to the array, or some other instruction that writes to the array.

That being said, I don't know if your data is still there or not after the rebuild, and if so, how to get it back.

That being said, you probably should have stuck with the --assemble command and not --create

---

### Post by zackiv31 on 2011-10-23
Yah I assumed the --assume-clean option would have kept all my data intact...

I tried for a couple days trying to get --assemble to work on its own, that's why I went back to the create command.

There's gotta be a way to get this data... hmm

---

### Post by FarNorth on 2012-05-15
Hi,

did you ever resolve this without losing all data? Same thing just happened to me.

---

### Post by rubylaser on 2012-05-15
Did you use the --assume-clean option, or did you try to --assemble --force as is the proper first step and what mdadm is suggesting as the next step.  Creating the array with assume clean should be a last option, not the first.

---

### Post by darkod on 2012-05-15
Also, I noticed the original OP tried for mounting:
sudo mount /media/bigdisk

Shouldn't that be:
sudo mount /dev/md0 /media/bigdisk

He never specified what to mount. If you are following the commands literary, watch out for that.

---

### Post by doogy2004 on 2012-05-17
If there is a line in fstab for the file system you can omit the device path.  If the device is not in fstab, then the device path is required by the mount command.

[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

---

### Post by FarNorth on 2012-05-23
Hi rubylaser,

I reassembled without the -clean option. The assembly looked fine. It was rebuilding the array, which took a few hours, but now it states that the array is clean.
The array comes up as an active array with a Clean state.
It just won't mount with the following error message:

mount: wrong fs type, bad option, bad superblock on /dev/md127,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

It is listed in fstab, and it doesn't make a difference whether I mount with the explicit target and filesystem or not.

dmesg says that it can't find the filesystem on the device.

---

### Post by doogy2004 on 2012-05-23
You may need to perform a file system check to clean up any errors in the file system.

[http://linux.die.net/man/8/fsck](http://linux.die.net/man/8/fsck)

---

### Post by darkod on 2012-05-23
If I am not mistaken, using the --create without the --assume-clean would have created a new blank array. It is normal that it shows as clean and working now.

But this new array wouldn't have any FS on it right now simply because it's new. That could explain the no FS error.

If you check it with fdisk or parted, does it say there is ext4 partition on it?

Like:
sudo fdisk -l
sudo parted /dev/md127 print

---

### Post by rubylaser on 2012-05-23
> **FarNorth said:**
> Hi rubylaser,

I reassembled without the -clean option. The assembly looked fine. It was rebuilding the array, which took a few hours, but now it states that the array is clean.
The array comes up as an active array with a Clean state.
It just won't mount with the following error message:

mount: wrong fs type, bad option, bad superblock on /dev/md127,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

It is listed in fstab, and it doesn't make a difference whether I mount with the explicit target and filesystem or not.

dmesg says that it can't find the filesystem on the device.

This is fine, you as long as you tried to assemble or create with --assume-clean should not have caused a resync.  If your array resynced, it's likely your data is lost.  When you use the create --assume-clean option you have to create the array with the same metadata version, chunk size, and disk order as the original array, otherwise it will not work.

[This]("https://raid.wiki.kernel.org/index.php/RAID_Recovery#Restore_array_by_recreating_.28after_multiple_device_failure.29") explains this in more depth.

---

### Post by FarNorth on 2012-05-23
The filesystem check returns the message below. The suggested alternate superblock returns the same message.

[FONT=System]fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext3: Superblock invalid, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/md127

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
[/FONT]

---

### Post by darkod on 2012-05-23
If you remember, I think you better provide the exact command you used to reassemble the array, because sometimes words have dual meaning.

When you say you reassembled without -clean, you mean:

sudo mdadm --create
or
sudo mdadm --assemble

Because there is BIG difference between the two. Since you say without -clean, I assume you didn't use the option --assume-clean so I didn't put it above.
But did you use --create or --assemble????

---

### Post by FarNorth on 2012-05-23
I used mdadm --assemble

---

### Post by rubylaser on 2012-05-23
Earlier you mentioned recreating the array and seeing it resync.  If you had a resync at all, you would have screwed up your filesystem completely.  After what command did you see a resync happen?  An assemble would not cause a rsync and neither would a create with the --assume-clean flag.

---

### Post by FarNorth on 2012-05-24
I also did an mdadm --run
However, I should say that the filesystem errors occurred before that. I tried mounting after reboot, before I tried any of the mdadm commands.
All of this happened just after the upgrade to precise.

---

### Post by FarNorth on 2012-05-25
sudo fdisk -l returns:

Disk /dev/md127: 3000.6 GB, 3000602984448 bytes
2 heads, 4 sectors/track, 732569088 cylinders, total 5860552704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x00000000

Disk /dev/md127 doesn't contain a valid partition table



and

sudo parted /dev/md127 print

gives:

Error: /dev/md127: unrecognised disk label


> **darkod said:**
> If I am not mistaken, using the --create without the --assume-clean would have created a new blank array. It is normal that it shows as clean and working now.

But this new array wouldn't have any FS on it right now simply because it's new. That could explain the no FS error.

If you check it with fdisk or parted, does it say there is ext4 partition on it?

Like:
sudo fdisk -l
sudo parted /dev/md127 print

---


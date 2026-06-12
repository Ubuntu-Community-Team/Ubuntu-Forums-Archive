---
title: "growing software raid 5 with mdadm"
date: 2011-05-13
forum: Server Platforms
---

### Post by highonv8splash on 2011-05-13
Hi all,

So my fileserver initially had 3 1TB drives in RAID 5 configured with mdadm as /dev/md1. (System root is a mirrored raid on /dev/md0) I went to go add a 4th 1TB drive to /dev/md1 and grow the raid 5 accordingly. I was initially following this guide:
[http://scotgate.org/2006/07/03/growing-a-raid5-array-mdadm/](http://scotgate.org/2006/07/03/growing-a-raid5-array-mdadm/)
but ran into issues on the 3rd and 4th commands. I've been trying a few things to remedy the issue since, but no luck. The drive seems to have been added to /dev/md1 properly, but I can't get the filesystem to resize to 3TB. I also am not entirely sure how /dev/md1p1 got created, but it appears to be the primary partition on the logical device /dev/md1.
Relevent information:
```

**fdisk -l /dev/md1**
Disk /dev/md1: 3000.6 GB, 3000606523392 bytes
2 heads, 4 sectors/track, 732569952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 196608 bytes
Disk identifier: 0xda4939fa

    Device Boot      Start         End      Blocks   Id  System
/dev/md1p1              33   488379968  1953519744   83  Linux

```
```

**fdisk -l /dev/md1p1**
Disk /dev/md1p1: 2000.4 GB, 2000404217856 bytes
2 heads, 4 sectors/track, 488379936 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 196608 bytes
Disk identifier: 0x00000000

Disk /dev/md1p1 doesn't contain a valid partition table

```
```

**cat /proc/mdstat**
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdb1[1] sda1[0]
      160079552 blocks [2/2] [UU]

md1 : active raid5 sdf1[1] sde1[3] sdd1[0] sdc1[2]
      2930279808 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

```
```

[B]parted /dev/md1 
print[/B]
Model: Unknown (unknown)
Disk /dev/md1: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      131kB  2000GB  2000GB  primary  ext2

```
```

[B]parted /dev/md1p1
print[/B]
Model: Unknown (unknown)
Disk /dev/md1p1: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  2000GB  2000GB  ext2

```

The filesystem originated as ext3, I believe its showing up as ext2 in some of these results because I disabled the journal when doing some initial troubleshooting. Not sure what the issue is, but I didn't want to blindly perform operations on the filesystem and risk losing my data.

Any help is appreciated!

---

### Post by rubylaser on 2011-05-13
Those directions are almost correct.  Since you have a device named /dev/md1p1, I'm guessing you've rebooted at least once since you added the drive to the array, and that's why you have the awkwardly named device. When you make changes to your array, you need to update your mdadm.conf file to reflect the changes you just made. You can get the info to change your /dev/md1 device from this command.
```
mdadm --detail --scan
```
It will give you 2 lines for each of your arrays, here's mine for an example.
```
root@fileserver:~# mdadm --detail --scan
ARRAY /dev/md0 metadata=0.90 UUID=d4e58776:640274d8:e368bf24:bd0fce41
```
Make the changes to /etc/mdadm/mdadm.conf to reflect the new arrays, and after that, reboot, and your device should come up as /dev/md1 again.

To verify your filesystem type, you can use the mount command like this.
```
mount | grep "^/dev"
```
It should spit out something like this.
```
root@fileserver:~# mount | grep "^/dev"
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
/dev/md0 on /storage type ext4 (rw,noatime)
```

So you can see my array is ext4. You'll want to run at least ext3 on yours so you have a journaled filesystem.

Next, you don't want to run an fsck on a mounted filesystem, and I assume since it's an existing RAID array, you have it mounted somewhere, so the first step is to unmount the array from the path you currently have it mounted on.

```
umount /storage
```
^ Just an example of where I have my array mounted.  Then you can run the fsck on the array depending on if it's ext2,3, or 4.

Once, that completes, you can expand your filesystem...
```
resize2fs /dev/md1
```

---

### Post by highonv8splash on 2011-05-13
I followed per your instructions, but am getting the same issues as before. 
I've updated /etc/mdadm/mdadm.conf to include:
```

ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=ceb8f554:e0df606f:24e43223:3f019718
ARRAY /dev/md1 level=raid5 num-devices=4 metadata=00.90 UUID=a33c77a0:8d96041d:c375812e:2defa627

```

Following the reboot, I still had /dev/md1 and was still receiving errors from these:
```

**resize2fs /dev/md1**
resize2fs 1.41.11 (14-Mar-2010)
Please run 'e2fsck -f /dev/md1' first.

```
```

**e2fsck -f /dev/md1**
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Group descriptors look bad... trying backup blocks...
e2fsck: Bad magic number in super-block when using the backup blocks
e2fsck: going back to original superblock
e2fsck: Device or resource busy while trying to open /dev/md1
Filesystem mounted or opened exclusively by another program?

```

Made sure to verify it wasn't mounted...
```

**mount**
/dev/md0 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```


Anyone have any other ideas?

---

### Post by rubylaser on 2011-05-13
Just a small change to your /etc/mdadm/mdadm.conf so that you don't see an error at the top of a detail scan.  Remove the leading zero from the metadata portion so it looks like this...
```
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=0.90 UUID=ceb8f554:e0df606f:24e43223:3f019718
ARRAY /dev/md1 level=raid5 num-devices=4 metadata=0.90 UUID=a33c77a0:8d96041d:c375812e:2defa627
```
And, have you verified that your new array is running by looking at...
[CODE}cat /proc/mdstat[/CODE]
```
mdadm --detail /dev/md1
```

Also, this section...
```
e2fsck: Group descriptors look bad... trying backup blocks...
e2fsck: Bad magic number in super-block when using the backup blocks
e2fsck: going back to original superblock
```

Does not look good.  What steps did you follow to disable the journal? And, can you mount the filesystem as it is right now before trying to expand to fill the new space.  I'm guessing your array is working fine at this point, and you have a problem with your filesystem.

---

### Post by highonv8splash on 2011-05-13
> **rubylaser said:**
> Just a small change to your /etc/mdadm/mdadm.conf so that you don't see an error at the top of a detail scan.  Remove the leading zero from the metadata portion so it looks like this...
```
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=0.90 UUID=ceb8f554:e0df606f:24e43223:3f019718
ARRAY /dev/md1 level=raid5 num-devices=4 metadata=0.90 UUID=a33c77a0:8d96041d:c375812e:2defa627
```
And, have you verified that your new array is running by looking at...
[CODE}cat /proc/mdstat[/CODE]
```
mdadm --detail /dev/md1
```

Also, this section...
```
e2fsck: Group descriptors look bad... trying backup blocks...
e2fsck: Bad magic number in super-block when using the backup blocks
e2fsck: going back to original superblock
```

Does not look good.  What steps did you follow to disable the journal? And, can you mount the filesystem as it is right now before trying to expand to fill the new space.  I'm guessing your array is working fine at this point, and you have a problem with your filesystem.


I used **tune2fs -O ^has_journal** to remove the journal.

I'm not able to mount /dev/md1, but I can mount /dev/md1p1 fine. The problem with simply mounting /dev/md1p1 is that it's still being recognized by the system as a 2TB filesystem. mdadm --detail and mdstat check out. The array is running but not mounted. --detail is telling me that the /dev/md1 array is 3TB and the superblock is persistent, but again, this is inconsistent with the partition that seems to now be residing on /dev/md1p1.

---

### Post by highonv8splash on 2011-05-13
Per the discussion here:
[http://www.linuxquestions.org/questions/ubuntu-63/raid1-array-says-dev-md0-does-not-have-a-valid-partition-table-wont-auto-mount-757872/](http://www.linuxquestions.org/questions/ubuntu-63/raid1-array-says-dev-md0-does-not-have-a-valid-partition-table-wont-auto-mount-757872/)

I'm going to try running
[B]
e2fsck -cc /dev/md1p1
resize2fs /dev/md1p1
fsck -f /dev/md1p1
[/B]

Wish me luck :-)

---

### Post by rubylaser on 2011-05-13
For it to be named /dev/md1p1, you must have setup a partition on the RAID array.  That's not necessary, but isn't incorrect either.  Those directions should work okay.  Good luck.

---

### Post by ian dobson on 2011-05-13
Hi,

It looks as if your file system is in a msdos partition, and guess what.... a msdos partition is limited to 2tb.

Regards
Ian Dobson

---

### Post by rubylaser on 2011-05-13
Good catch, I don't know how I missed that.
```
Partition Table: msdos
```

---

### Post by highonv8splash on 2011-05-14
Thanks for all the help, both of you. I managed to change the partition table on /dev/md1p1 to GPT and resize it beyond 2TB with gparted. Running smoothly now :-)

---

### Post by ian dobson on 2011-05-15
Hi,

Good to hear. Please mark this thread as solved and maybe include a short howto on how you converted your partitions from mbr to gpt.

Regards
Ian Dobson

---


---
title: "inode/journal issues on 10.4 with ext3 filesystem"
date: 2010-10-12
forum: System76 Support
---

### Post by Pitt Stains on 2010-10-12
Hello,

I have a Gazelle Ultra (gazu1) which is running Ubuntu 10.4 (Lucid Lynx).  Since I upgraded from a previous installation, my filesystem is ext3 rather than ext4.

I'm getting a lot of issues lately with the machine locking up.  I disabled the splash screen so I can see all the crud dumped to the screen and I'm seeing a lot of "orphaned inode removed" and journal rebuilding on my home and root partitions.

This suggests hardware issues to me, but I seem to have a lot of bad luck with hard drives, so I'm starting to wonder if something I'm doing is contributing to their bad behavior.  Things I do that are probably unusual:
[LIST]
[*]I shred (shred -fuz filename) a lot of files instead of simply deleting them
[*]I run Truecrypt to encrypt one of my partitions, but not either of the affected ones
[*]I have some unpartitioned space at the end of my hard drive
[/LIST]
Am I a hazard to hard drives everywhere or just unlucky?  I'm thinking I want to start with a fresh install for 10.10, but I'm wondering if I should even bother with my current hard drive.

Thanks,
-Pitt

---

### Post by isantop on 2010-10-12
Hi.

You may want to try running fsck from a LiveCD. Simply boot from the LiveCD, Click on "Try Ubuntu", then open a terminal (Applications > Accessories > Terminal) and try running the following commands:
```
sudo fsck -f /dev/sda1
sudo fsck -f /dev/sda2
sudo fsck -f /dev/sda3
```
and so on until you have checked each partition on your disk. If any come back with errors (not including swap) then post the outputs here.

---

### Post by Pitt Stains on 2010-10-14
Here are the results:

[SIZE="4"]**SDA1**[/SIZE]
My / partition, which sometimes shows up in pre-boot errors:
```

ubuntu@ubuntu:~$ sudo fsck -f /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 229566/500960 files (4.0% non-contiguous), 1682997/2000084 blocks

```

[SIZE="4"]**SDA2**[/SIZE]
/dev/sda2 is my swap partition, so I skipped that.

[SIZE="4"]**SDA3**[/SIZE]
/dev/sda3 contains /dev/sda5 and /dev/sda6, so I think this is normal:
```

ubuntu@ubuntu:~$ sudo fsck -f /dev/sda3
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3
Could this be a zero-length partition?

```

[SIZE="4"]**SDA4**[/SIZE]
/dev/sda4 is the unallocated space at the end of my hard drive, so I think the following is normal.  If anyone is wondering, the space is there because I thought I might want to install another operating system on this machine sometime, perhaps a different flavor of Linux, but I haven't yet.
```

ubuntu@ubuntu:~$ sudo fsck -f /dev/sda4
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda4

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

[SIZE="4"]**SDA5**[/SIZE]
My /home partition, which sometimes shows up in pre-boot error messages:
```

ubuntu@ubuntu:~$ sudo fsck -f /dev/sda5
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
Superblock last mount time is in the future.
	(by less than a day, probably due to the hardware clock being incorrectly set)  Fix<y>? yes

Superblock last write time is in the future.
	(by less than a day, probably due to the hardware clock being incorrectly set).  Fix<y>? yes

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda5: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda5: 23948/250480 files (13.5% non-contiguous), 754276/1000038 blocks

```

[SIZE="4"]**SDA6**[/SIZE]
This is my Truecrypt volume.  I'm pretty sure the idea is that when it's not mounted, it's supposed to look like unallocated disk space, so I think this is normal.  In any case, sda6 is not showing up in the error messages I'm seeing.

```

ubuntu@ubuntu:~$ sudo fsck -f /dev/sda6
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda6

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

Thanks for looking at this,
-Pitt

---

### Post by Pitt Stains on 2010-10-14
The boot errors look something like this, which is taken from /var/log/messages:

```

EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: sda1: orphan cleanup on readonly fs
EXT3-fs: sda1: 13 orphan inodes deleted
EXT3-fs: recovery complete.
EXT3-fs: mounted filesystem with ordered data mode.

```

I can't find anything similar in the log for sda5, but I feel like the message says something about rebuilding or recreating the journal for sda5.  The only thing in the log is this:

```

kjournald starting.  Commit interval 5 seconds
EXT3 FS on sda5, internal journal
EXT3-fs: mounted filesystem with ordered data mode.

```

The system is locking up so frequently now that it's becoming unusable.  I'll be running from a LiveCD today so I can be at least somewhat productive at work.

---

### Post by isantop on 2010-10-14
Hi.

This is starting to look like a bad hard drive.

Could you look at the SMART data from Disk Utility? I know it has a history of false-positives on bad sectors, but thats what this could be an indication of.

---

### Post by Pitt Stains on 2010-10-15
> **isantop said:**
> 
Could you look at the SMART data from Disk Utility? I know it has a history of false-positives on bad sectors, but thats what this could be an indication of.

I just noticed the Disk Utility menu item in the last week so I'm not familiar with how it works.  I'm running the OS off a Live CD now; I'm assuming the SMART data you're asking for can be accessed this way and doesn't depend on log files or anything else on the disk in question.

Here's what I get under Attributes: Read Error Rate, Spinup Time, Reallocated Sector Good, Spinup Retry Count, and Write Error Rate are assessed as "Good."  The assessment for everything else is "N/A."

I'm going to click "Run Self-test" and see what results.  I'm posting this now in case the test causes my machine to lock up.

---

### Post by Pitt Stains on 2010-10-15
I should add that it lists no bad sectors and the overall assessment is: "Disk is healthy."  Also, I didn't get any feedback from the self-test.  I ran the short test.

---


---
title: "Preventing Ubuntu 9.04 RAID5 array from being assembled"
date: 2009-10-03
forum: Server Platforms
---

### Post by rolnik on 2009-10-03
So I've got three RAID arrays in my Ubuntu 9.04.  Since upgrading from 8.10 to 9.04, the reboot of my RAID5 array has given my system fits. It relies on an external bitmap which mounts to /tmp1 ... except I think, at the time the system boots, it tries to fsck the RAID5 array before /tmp1 is mounted.  Outcome: the reboot takes a detour and drops into an administrative shell complaining about the external bitmap on /dev/sde2.  So I have tried three different mdadm.confs and each gets a bad result on boot up

===== mdadm.conf w/o mention of RAID5 
```
 cat checkfs
Log of fsck -C -R -A -a
Sat Oct  3 09:53:35 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sde2: clean, 13/244320 files, 33681/975948 blocks
fsck.ext3: No such file or directory while trying to open /dev/md2
/dev/md2:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Sat Oct  3 09:53:35 2009
----------------

```===== mdadm.conf w/ RAID5 , but omitting reference to external write-intent bitmap:
tail -8 mdadm.conf
```
 tail -8 mdadm.conf
# by mkconf $Id$
ARRAY /dev/md2 level=raid5 num-devices=4 metadata=00.90 spares=1 UUID=6c4e45d1:acfd2320:665b2eb0:3bdce6ac
# Restart the /dev/md2 manually so that it can rely on the bitmap:
#   mdadm -As /dev/md2
...

``````
$ cat checkfs
Log of fsck -C -R -A -a
Sat Oct  3 10:00:45 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sde2: clean, 13/244320 files, 33681/975948 blocks
/dev/md2: clean, 14883/135528448 files, 10445939/542104752 blocks

Sat Oct  3 10:00:45 2009
----------------

```Yes, the machine boots just fine. Its just that I can't benefit from the performance of an external bitmap (and resyncs are going to take longer when a disk fails).
===== mdadm.conf w/ RAID5 and bitmap
```
# tail -8 mdadm.conf.bak7
# by mkconf $Id$
ARRAY /dev/md2 bitmap=/tmp1/md2bitmap level=raid5 num-devices=4 metadata=00.90 spares=1 UUID=6c4e45d1:acfd2320:665b2eb0:3bdce6ac
...

``````
$ cat checkfs
Log of fsck -C -R -A -a
Sat Oct  3 10:06:15 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sde2: clean, 13/244320 files, 33681/975948 blocks
fsck.ext3: Invalid argument while trying to open /dev/md2
/dev/md2:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Sat Oct  3 10:06:15 2009
----------------

```Again, reboot halts and drops the console into an administrative shell. Once I walk over to the console and tell it to continue, I'm getting the above 'checkfs' output about 'superblock could not be read'

Ultimately, I'd like Ubuntu 9.04 to just leave the /dev/md2 alone and let me manually assemble/mount it.  That way I get a) clean reboots (no more walking over to the console); and b) option to use the external bitmap (both for daily use _and_ for the perilous disk-fail-replace-resync process).  Any ideas how to get Ubuntu to stop messing with my /dev/md2 and _get_ that I if its not in mdadm.conf, then Ubuntu shouldn't automatically be assemble the /dev/md2?

Thanks for your attention.

---

### Post by Xianath on 2009-10-06
Just for kicks, can you cat /etc/mdadm/mdadm.conf in the busybox shell? If it lists your array, then you need to update-initramfs -u once you've booted completely. I've had the opposite problem, and that fixed it.

HTH,
Peter

---

### Post by rolnik on 2009-10-06
Peter, thanks for the suggestion.
I tried a reboot using the 'full bodied' mdadm.conf which specifies the bitmap:
```

...
ARRAY /dev/md2 level=raid5 num-devices=4 metadata=00.90 spares=1 UUID=6c4e45d1:acfd2320:665b2eb0:3bdce6ac

```On boot, I dropped into a maintenance shell.  Some of the error messages on the console were:
```

/dev/sde2: recovering journal
/dev/sde2: clean, 17/244320 files, 33685/975948 Blocks (check in 4 mounts)
fsck.ext3: Invalid argument while trying to open /dev/md2
/dev/md2: 
  The super block could not be read...

  fsck died with exit status 8

```So after I do a 'control - D' at the console, the file systems come up, except that I still have to manually assemble the /dev/md2 and also manually mount /dev/md2 to the /data directory...
So I'm pretty much back where I started.  Long story short, the update-initramfs didn't fix the problem.  I'm hoping that an install of Karmic will put in a fix.  The upgrade from 8.10 to 9.04 was what initially caused this cranky reboot scenario noted above... perhaps the final release of 9.10 will clean it up?

---

### Post by Xianath on 2009-10-07
Interesting! It sounds like an ext3 mount problem more so than a RAID problem. How does your fstab look in busybox? How about /proc/mdstat? Is it possible that md brings up arrays in the wrong order, or otherwise with the wrong device name? Try mounting /data by UUID instead.

Cheers,
Peter

---

### Post by rolnik on 2009-10-08
At boot, and dropping into the busy box, my fstab is as follows:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=cf4e8cfa-34c8-465f-b329-a92085105484 /               ext3    relatime,errors=remount-ro 0       1

# /dev/md1
UUID=43418bcf-833b-424c-bb8a-29597c72fb64 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sde2       /tmp1   ext3    rw      0       2
# /dev/md2:  Upgrade to Ubuntu9.04 seems to have shuffled the UUID used by /dev
UUID=6c4e45d1-acfd2320-665b2eb0-3bdce6ac /data  ext3    rw      0       2

```the file systems:
  /tmp1
and
  /data

do not exist.  So my theory is that there is an issue with the order of mounting.  The Server tries to setup /dev/md2 before /dev/sde2 is mounted to /tmp1.  I tried mounting data using the UUID, but that has not worked, as shown above.

However, I've tried boot with the bitmap placed on /dev/md0 (in /var/log/md2bitmap), and I _still_ can't get the bootup/fstab to assemble/mount the /dev/md2 and/or /data directory.  Though, I still can do a manual assemble:
```

mdadm -As /dev/md2

```
At the end of the day, I need to sequence these mounts and hold off assembling the /dev/md2 as late as possible.  Right now, the only alternative seems to be to manually mount /dev/sde2 to /tmp1 and manually assemble/mount /dev/md2 when /tmp1 becomes available.

---


---
title: "cannot mount existing jmicron Raid 1"
date: 2010-05-28
forum: Server Platforms
---

### Post by pictureaday on 2010-05-28
Hello,

I have recently had a problem with my 10.04 server machine. It will not boot, it seems to be taking forever on the loading screen (normally headless server, but I connected monitor when I couldn't ssh), but that's not why I'm here. 

Knowing that I do rsync backups every night at midnight of my machine I just bit the bullet and formatted my / partition. Reinstall went fine, I turned off automatic updates (I suspect an update caused the problem)  But now I cannot mount my jmicron raid 1, which is where my rsync backup is (doh!).

**sudo fdisk -l**
```

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8d9c2c2b

   Device Boot      Start         End      Blocks   Id  System

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8d9c2c2b

   Device Boot      Start         End      Blocks   Id  System

```

**ls -lh /dev/mapper**
```
total 0
drwxr-xr-x  2 root root      80 2010-05-28 09:25 .
drwxr-xr-x 18 root root    3800 2010-05-28 09:25 ..
crw-rw----  1 root root  10, 59 2010-05-28 08:14 control
brw-rw----  1 root disk 251,  0 2010-05-28 09:25 jmicron_blackRaid

```



**dmraid -r:**
```

/dev/sde: jmicron, "jmicron_blackRaid", mirror, ok, 1953497088 sectors, data@ 0
/dev/sdd: jmicron, "jmicron_blackRaid", mirror, ok, 1953497088 sectors, data@ 0

```

I do believe I formatted it ext3 and I cannot seem to mount it that way.
**sudo mount -t ext3 /dev/mapper/jmicron_blackRaid /media/temp:**
```

mount: wrong fs type, bad option, bad superblock on /dev/mapper/jmicron_blackRaid,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

[B]dmesg | tail:
[/B]```

... (unrelated stuff omitted)
[ 4449.485504] VFS: Can't find ext3 filesystem on dev dm-0.

```

If I remember correctly I had to install something to get it to recognize the partition correctly, but I cannot remember what it was...

Thanks in advanced for the help!

---

### Post by pictureaday on 2010-05-28
ps it is a fakeraid, the more research I do the more I realize how unsupported said raid is. :(

If someone could answer how to get the data off one drive then I will be happy, then I can start over using a software raid. (No worries, this raid was a pilot raid before I committed to using it, so all the data is replaceable, it's just a PITA.

Thanks

---

### Post by mclad on 2010-08-12
I think I have the same problem. I could not install 10.04 on a VIA RAID controller without disconnecting my data drives which are on a Jmicron controller. After successfully installing 10.04 on the VIA RAID 1 array, I reconnected the Jmicron RAID 1 array but I cannot mount it.
 
```
madams@madams-desktop:~$ ls -l /dev/mapper
total 0
crw-rw---- 1 root root  10, 59 2010-08-12 00:12 control
brw-rw---- 1 root disk 252,  6 2010-08-12 08:12 jmicron_JRAID-DATA      ?
brw-rw---- 1 root disk 252,  6 2010-08-12 00:12 jmicron_JRAID-DATA_______
brw-rw---- 1 root disk 252,  0 2010-08-12 00:12 via_bfidghddbd
brw-rw---- 1 root disk 252,  1 2010-08-12 00:12 via_bfidghddbd1
brw-rw---- 1 root disk 252,  2 2010-08-12 00:12 via_bfidghddbd2
brw-rw---- 1 root disk 252,  3 2010-08-12 00:12 via_bfidghddbd3
brw-rw---- 1 root disk 252,  4 2010-08-12 00:12 via_bfidghddbd5
brw-rw---- 1 root disk 252,  5 2010-08-12 00:12 via_bfidghddbd6
madams@madams-desktop:~$ sudo dmraid -ay
RAID set "jmicron_JRAID-DATA      " already active
RAID set "via_bfidghddbd" already active
RAID set "jmicron_JRAID-DATA      1" was not activated
RAID set "via_bfidghddbd1" already active
RAID set "via_bfidghddbd2" already active
RAID set "via_bfidghddbd3" already active
RAID set "via_bfidghddbd5" already active
RAID set "via_bfidghddbd6" already active
```

---


---
title: "Server upgrade from 10.04 to 12.04 and now RAID1 disk reads are slow"
date: 2013-05-30
forum: Server Platforms
---

### Post by droberts on 2013-05-30
I could stream videos off this server on 10.04. After upgrading to 12.04 the read speed is terrible and XBMC is essentially unusable.

This was not a clean install, it was upgraded.

The raid is RAID0.

[FONT=Courier New]cat /proc/mdstat
Personalities : [raid0] [linear] [multipath] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid0 sda[1] sdb[0]
      3907028992 blocks 64k chunks[/FONT]

The drive is pretty full of movies and television shows, but no where near full as yet. Does 12.04 just dislike Archer and Arrested Development?

[FONT=Courier New]hdparm -Tt /dev/md0

/dev/md0:
 Timing cached reads:   1238 MB in  2.00 seconds = 619.19 MB/sec
 Timing buffered disk reads:  36 MB in  4.84 seconds =   7.44 MB/sec[/FONT] <-- GTFO 

Anyone know what I can do?

---

### Post by rubylaser on 2013-05-31
Have you tried to actually write and read some test data to the disk to see real read and write speeds on the box?

```

# Write Speeds
dd if=/dev/zero of=/path/to/mounted/filesystem/testfile.out bs=1M count=10000
sync
# Read Speeds
dd if=/path/to/mounted/filesystem/testfile.out of=/dev/null bs=1M

```

Also, have you checked the SMART data on each disk to make sure that one of your RAID disks isn't failing?
```
smartctl -a /dev/sda
smartctl -a /dev/sdb
```

---

### Post by droberts on 2013-06-02
Rubylaser,

Thank you for your quick reply. Sorry I could not get back here sooner, I was busy at work.

**Write speeds:**
1642+0 records in
1642+0 records out
1721761792 bytes (1.7 GB) copied, 235.239 s, 7.3 MB/s

**Read speeds:**
0 records in
136+0 records out
142606336 bytes (143 MB) copied, 48.8133 s, 2.9 MB/s

smartctl showed no errors on either disk.

---


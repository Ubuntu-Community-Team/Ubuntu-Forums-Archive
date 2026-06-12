---
title: "added previously used 3 TB hard drive, created parition and lost .7 TB"
date: 2016-01-02
forum: Server Platforms
---

### Post by NotQuiteSU on 2016-01-02
I added a new hard drive to my new Ubuntu Server install
```
 
product: WDC WD30EFRX-68A
logical name: /dev/sdb
size: 2794GiB (3TB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 sectorsize=4096

```

I ran fdisk, deleted and created the partition that was there, but now I have the following oddities. The first one previously existed
```

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: The size of this disk is 3.0 TB (3000592982016 bytes).
DOS partition table format can not be used on drives for volumes
larger than (2199023255040 bytes) for 512-byte sectors. Use parted(1) and GUID
partition table format (GPT).


The device presents a logical sector size that is smaller than
the physical sector size. Aligning to a physical sector (or optimal
I/O) size boundary is recommended, or performance may be impacted.

```

I used mkfs to make an ext4 partition of /sdb1 using defaults.

When I ran sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL, I got:

```

NAME   FSTYPE   SIZE MOUNTPOINT LABEL
sdb             2.7T
&#9492;&#9472;sdb1 ext4       2T
sr0            1024M

```

Where did my .7 TB go? And how do I get rid of that error?

---

### Post by nerdtron on 2016-01-02
MBR partition only supports 4 primary partitions per hard drive, and a  maximum partition size of 2TB.  That is why you're only seeing 2TB.

  GUID (GPT disks) can support a volume up to 18 EB (Exabyte’s) or 1 million terabytes.  

And the fdisk utility only support MBR drives. You'll need to use the "parted" utility to repartition as GPT and format the drive. See this link: [http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)

---

### Post by Elishasmantle on 2016-01-02
Hello,

I think if you just use Gparted it will solve the issues.
See this article on same type issue:

[http://askubuntu.com/questions/84538/trouble-creating-3tb-ext4-partition-due-to-msdos-partition-table-imposed-error](http://askubuntu.com/questions/84538/trouble-creating-3tb-ext4-partition-due-to-msdos-partition-table-imposed-error)

Thank You,

elishasmantle

---

### Post by lisati on 2016-01-02
*Thread moved to **Server Platforms**.*

If you use [noparse]```
 and 
``` instead of >  and  it helps preserve the formatting of quoted output.[/noparse]

---

### Post by NotQuiteSU on 2016-01-02
parted worked perfectly! Thanks!

---


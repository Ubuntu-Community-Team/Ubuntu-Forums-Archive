---
title: "RAID 5 Recovery (2 of 3 disks failed)"
date: 2008-10-18
forum: Server Platforms
---

### Post by Joe Jarvis on 2008-10-18
Long story short, two of three disks in my RAID 5 array failed.  I purchased two new drives and used dd_rescue to clone the failed drives.  I was able to get almost NO data from one of the failed drives and almost ALL the data from the other.  Now, when I try to create the RAID array in a degraded state from the one good disk and the good cloned disk, mdadm acts like it doesn't see anything on the cloned disk.  Ideas?  Thanks in advance.

My RAID 5 array:
Slot 0: /dev/sda1
Slot 1: /dev/sdb1
Slot 2: /dev/sdc1

New drives:
/dev/sdd (for cloning sda)
/dev/sde (for cloning sdc)


To clone failed drives, I ran:
sudo dd_rescue -v -l slot0rescue.log /dev/sda /dev/sdd
sudo dd_rescue -v -l slot2rescue.log /dev/sdc /dev/sde


The Slot 0 rescue went pretty well:
```
dd_rescue: (info): /dev/sdd (488386592.0k): EOF
Summary for /dev/sdd -> /dev/sde:
dd_rescue: (info): ipos: 488386592.0k, opos: 488386592.0k, xferd: 488386592.0k
                   errs:    216, errxfer:       108.0k, succxfer: 488386464.0k
             +curr.rate:    49689kB/s, avg.rate:    17689kB/s, avg.load:  8.0%
```

I try to recreate the array using:
sudo mdadm --create /dev/md0 --assume-clean --level=5 --verbose --raid-devices=3 /dev/sdd1 /dev/sdb1 missing

```
joe@jefferson:~$ sudo mdadm --create /dev/md0 --assume-clean --level=5 --verbose --raid-devices=3 /dev/sdd1 /dev/sdb1 missing
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: Cannot open /dev/sdd1: No such device or address
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid5 devices=3 ctime=Sat Oct 18 08:38:04 2008
mdadm: create aborted
```

The partition appears to exist:
```
joe@jefferson:~$ ls /dev/sdd*
/dev/sdd  /dev/sdd1
```

```
joe@jefferson:~$ sudo fdisk -l /dev/sdd

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002c974

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect
```


Any ideas why mdadm is failing?  Did I clone the disk with dd_rescue wrong?

SOLUTION IN POST BELOW

---

### Post by fjgaude on 2008-10-18
Did you try without the **--assume-clean** option?

You might try using the -f force option... and you might even try to simply --assemble -f /dev/md0 the array:

```
sudo mdadm --assemble -f --scan
```

or

```
sudo mdadm --assemble -f /dev/md0 /dev/sdd1 /dev/sdb1 missing
```

I can't say anything about the dd_rescue operation you made, seems okay.

---

### Post by Joe Jarvis on 2008-10-19
I solved my problem.

mdadm looks at /proc/partitions to determine which partitions exist.

If you use dd_rescue to clone a drive, /proc/partitions does not automatically update or include the cloned partitions.

After rebooting, /proc/partitions listed the dd_rescue cloned partitions and the mdadm command in my original post worked.

---

### Post by fjgaude on 2008-10-19
Very good! Glad it all worked out for you... backups, backups are nice. I wouldn't leave home without them. <smile>

---


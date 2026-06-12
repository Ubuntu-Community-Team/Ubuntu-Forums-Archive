---
title: "Problem with mounting raid array"
date: 2009-08-22
forum: Server Platforms
---

### Post by badrunner on 2009-08-22
I have a server with a raid0 array of two disks (its basically a dumping ground for big files so reliability doesnt matter).

Yesterday the server shutdown when the array was being written to due to a power failure, and today when i try to mount, the command just sits there appearing to do nothing for ages and not actually mounting the disk. Any ideas how i can diagnose/repair this, im far from being an expert on raid, i know just enough to be dangerous, so would appreciate any help.

Relevant line from fstab:

/dev/md0  /var/server ext3 noexec 0 0

Output from mdadm:

tom@gandalf:/$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Fri Apr 10 13:34:40 2009
     Raid Level : raid0
     Array Size : 2930271872 (2794.53 GiB 3000.60 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Apr 10 13:34:40 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 0025aff4:e89ee912:e73ef6c3:51f2c869 (local to host gandalf)
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1

---

### Post by badrunner on 2009-08-22
Ah, it seems to have been doing an fsck when mounting, and its mounted ok now, so no problems at all.

---

### Post by fjgaude on 2009-08-22
I'd change the fstab line to:

```
/dev/md0 /var/server ext3 noexec 0 2
```

Assuming it is not a boot disk.

---

### Post by badrunner on 2009-08-22
> **fjgaude said:**
> I'd change the fstab line to:

```
/dev/md0 /var/server ext3 noexec 0 2
```Assuming it is not a boot disk.

Thanks, what exactly does that change mean?

---

### Post by fjgaude on 2009-08-23
I'll paste in what **man fstab** pages have to say about that field:

       The  sixth field, (fs_passno), is used by the fsck(8) program to deter&#8208;
       mine the order in which filesystem checks are done at reboot time.  The
       root  filesystem  should  be specified with a fs_passno of 1, and other
       filesystems should have a fs_passno of 2.  Filesystems within  a  drive
       will  be checked sequentially, but filesystems on different drives will
       be checked at the same time to utilize  parallelism  available  in  the
       hardware.   If  the sixth field is not present or zero, a value of zero
       is returned and fsck will assume that the filesystem does not  need  to
       be checked.

Hope this helps.

---


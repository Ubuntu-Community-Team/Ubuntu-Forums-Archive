---
title: "All RAID levels are slow"
date: 2009-11-09
forum: Server Platforms
---

### Post by netkom on 2009-11-09
Hi all,

I have a new uptodate install of Ubuntu Server LTS 8.04.3. In this machine are 4 sata harddisks. 3 identical 320GB (WDC WD3200SD) and one 400GB (WDC WD4001ABYS). The 400GB disk has been partitioned with /boot, /, swap and 320GB raid autodetect.

I was planning to use the disks as raid5 but write performance was terrible slow (arround 10MB/s using dd if=/dev/zero of=/dev/md0 bs=1024 count=1M). So I looked into it and tried other raid levels. even on raid0 write speed was just around 20MB/s. So I tried each disk by itself. They all were around 65-68MB/s. I then thought there might be some kind of problem when all disks are utilized and ran 4 parallel dd processes, which showed almost no slow down.

Now I'm stuck. Any hints what is going wrong here? Or what else to try?

Thanks
Jonathan

---

### Post by mrsteveman1 on 2009-11-09
Hmmmm

Anything in the kernel log? (dmesg)

---

### Post by fjgaude on 2009-11-09
What does this show:

```
sudo mdadm -D /dev/mdx
```

with 'x' the number of your array.

You are using **mdadm** to create the array?

---

### Post by netkom on 2009-11-10
> **mrsteveman1 said:**
> Hmmmm

Anything in the kernel log? (dmesg)

Nothing I can see. [http://en.pastebin.ca/166483](http://en.pastebin.ca/166483) has the output.



> **fjgaude said:**
> What does this show:

```
sudo mdadm -D /dev/mdx
```

with 'x' the number of your array.

You are using **mdadm** to create the array?

```
netkom@iSCSI1:~$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Mon Nov  9 19:50:19 2009
     Raid Level : raid5
     Array Size : 937705728 (894.27 GiB 960.21 GB)
  Used Dev Size : 312568576 (298.09 GiB 320.07 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Nov  9 21:51:29 2009
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : eaa61cc1:39b63f39:63ebcc44:4ad1de25 (local to host iSCSI1)
         Events : 0.4

    Number   Major   Minor   RaidDevice State
       0       8       19        0      active sync   /dev/sdb3
       1       8        1        1      active sync   /dev/sda1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1

```

Yes, I'm using mdadm. And testing performance again gives
```

root@iSCSI1:/home/netkom# time dd if=/dev/zero of=/dev/md0 bs=1024 count=1M && time sync
1048576+0 records in
1048576+0 records out
1073741824 bytes (1,1 GB) copied, 76,6583 s, 14,0 MB/s

real    1m16.662s
user    0m0.380s
sys     0m13.540s

real    0m0.003s
user    0m0.000s
sys     0m0.000s

```

Out of couriosity I created a RAID 0 with just one disk. As far as I understood numbers shouldn't change to much. Here is the result:

```

root@iSCSI1:/home/netkom# mdadm --create /dev/md0 -l0 -n1 /dev/sda1 --force
mdadm: /dev/sda1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Mon Nov  9 19:50:19 2009
Continue creating array? yes
mdadm: array /dev/md0 started.

root@iSCSI1:/home/netkom# dd if=/dev/zero of=/dev/md0 bs=1024 count=1M
1048576+0 records in
1048576+0 records out
1073741824 bytes (1,1 GB) copied, 51,9947 s, 20,7 MB/s

root@iSCSI1:/home/netkom# mdadm --manage /dev/md0 -S
mdadm: stopped /dev/md0

root@iSCSI1:/home/netkom# dd if=/dev/zero of=/dev/sda1 bs=1024 count=1M
1048576+0 records in
1048576+0 records out
1073741824 bytes (1,1 GB) copied, 17,3929 s, 61,7 MB/s

```

all that was in dmesg at that time was
```

[ 1633.318140] md: md0 stopped.
[ 1633.318171] md: unbind<sdb3>
[ 1633.318178] md: export_rdev(sdb3)
[ 1633.318453] md: unbind<sdd1>
[ 1633.318460] md: export_rdev(sdd1)
[ 1633.318474] md: unbind<sdc1>
[ 1633.318478] md: export_rdev(sdc1)
[ 1633.318490] md: unbind<sda1>
[ 1633.318495] md: export_rdev(sda1)
[ 1692.164933] md: bind<sda1>
[ 1692.196039] md0: setting max_sectors to 128, segment boundary to 32767
[ 1692.196051] raid0: looking at sda1
[ 1692.196055] raid0:   comparing sda1(312568576) with sda1(312568576)
[ 1692.196059] raid0:   END
[ 1692.196061] raid0:   ==> UNIQUE
[ 1692.196063] raid0: 1 zones
[ 1692.196064] raid0: FINAL 1 zones
[ 1692.196069] raid0: done.
[ 1692.196071] raid0 : md_size is 312568576 blocks.
[ 1692.196074] raid0 : conf->hash_spacing is 312568576 blocks.
[ 1692.196076] raid0 : nb_zone is 1.
[ 1692.196079] raid0 : Allocating 8 bytes for hash.
[ 1835.615064] md: md0 stopped.
[ 1835.615094] md: unbind<sda1>
[ 1835.615103] md: export_rdev(sda1)

```

So I'm lost here... I couldn't find any evidence on the net that write performance is sooo bad using software raid.

Thanks

---

### Post by fjgaude on 2009-11-10
Well, what you have may be normal... what does this show:

```
sudo hdparm -tT /dev/md0
```

I checked an array I have with dd and I only got 20 MB/sec write. With aboe test I got 147 MB/sec read. Let's see what you get.

---

### Post by netkom on 2009-11-10
Well,
I get 
```

netkom@iSCSI1:~$ sudo hdparm -tT /dev/md0

/dev/md0:
 Timing cached reads:   1752 MB in  2.00 seconds = 875.69 MB/sec
 Timing buffered disk reads:  452 MB in  3.00 seconds = 150.55 MB/sec

```

What level is your array?

I somewhat refuse to see that as normal. We got a QNAP NAS here, which runs some sort of (embedded) i686 linux. There I get on an RAID 5 96.542 MB/s using dd. (While serving ~10 VMs over iSCSI).
```

[/share/tmp] # time dd if=/dev/zero of=test.dd bs=1024 count=1M && time sync
1048576+0 records in
1048576+0 records out

real    0m9.758s
user    0m0.338s
sys     0m5.005s

real    0m1.364s
user    0m0.000s
sys     0m0.060s

```

Even thought it *might* be normal for an RAID5, why is an RAID0 with **one** disk slower (20MB/s) compared to ~60MB/s for the disk itself?

---

### Post by fjgaude on 2009-11-10
Okay, just everything I can remember... you may be need to use a **dd** command like this to test speed:

```
time dd bs=1M count=1000 if=/dev/zero of=1000M.bin
```

That way the data goes to a file and not to who-knows-where on the array or drive.

The file will be in the same directory from which the dd command was given.

---

### Post by fjgaude on 2009-11-10
Using the suggested command on a four-drive, raid5 array, I got 90 MB/sec write with the hdparm test showing it to read at 150 MB/sec.

This seems about right... I've always through the write speed of a raid5 array was about that of a single drive in the array. It's a little better than that, for in the test array the drives, each, are about 60 MB/sec.

So it seems the mystery is likely solved, eh?

---

### Post by netkom on 2009-11-10
Ok. Problem was the blocksize I see... Thanks

---

### Post by fjgaude on 2009-11-10
Very good! Out of curiosity I ran a test on a four-drive raid5 that uses 100 MB/sec drives and got 180 MB/sec write with over 240 MB/sec read (I was hoping for about 300 MB/sec read <sigh>).

So we can see the write speed being close to that of two drives in raid0.

---


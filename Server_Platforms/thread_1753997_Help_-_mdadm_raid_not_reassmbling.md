---
title: "Help - mdadm raid not reassmbling"
date: 2011-05-09
forum: Server Platforms
---

### Post by carstenw on 2011-05-09
Hi there,

I desperately need some help/advice with my mdadm raid. It was built using four 1 TB disks in RAID5 mode with no spare disk, each attached to an onboard SATA port. Yesterday, it suddenly stopped working. Each individual disk seems OK, but the array won't assemble by rebooting. Needless to say, the problem occurred after a huge amount of data changed and before the next backup.

I don't like posting long outputs, but in this case I will do and hope this will help to come to a solution as soon as possible.

I am using Ubuntu 10.04.2 LTS.


Command:
mdadm --assemble -v --no-degraded -u 568512ee:565410b0:3dcfe939:c4310215 /dev/md0

Output:

mdadm: no RAID superblock on /dev/sdc1
mdadm: /dev/sdc1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdc has wrong uuid.
mdadm: no RAID superblock on /dev/sdd1
mdadm: /dev/sdd1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdd
mdadm: /dev/sdd has wrong uuid.
mdadm: no RAID superblock on /dev/sdb1
mdadm: /dev/sdb1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdb
mdadm: /dev/sdb has wrong uuid.
mdadm: no RAID superblock on /dev/sda1
mdadm: /dev/sda1 has wrong uuid.
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sda has wrong uuid.
mdadm: /dev/sdc2 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdd2 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdb2 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sda2 is identified as a member of /dev/md0, slot 3.
mdadm: added /dev/sdc2 to /dev/md0 as 0
mdadm: added /dev/sdb2 to /dev/md0 as 1
mdadm: added /dev/sdd2 to /dev/md0 as 2
mdadm: added /dev/sda2 to /dev/md0 as 3
mdadm: /dev/md0 assembled from 1 drive (out of 4), but not started.


Command:
mdadm --examine /dev/sda2

Output:

/dev/sda2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 568512ee:565410b0:3dcfe939:c4310215
  Creation Time : Thu Nov 12 16:53:28 2009
     Raid Level : raid5
  Used Dev Size : 976557376 (931.32 GiB 999.99 GB)
     Array Size : 2929672128 (2793.95 GiB 2999.98 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon May  9 15:43:14 2011
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 2b0022a6 - correct
         Events : 18332

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8        2        3      active sync   /dev/sda2

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       8        2        3      active sync   /dev/sda2


Command:
mdadm --examine /dev/sdb2

Output:

/dev/sdb2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 568512ee:565410b0:3dcfe939:c4310215
  Creation Time : Thu Nov 12 16:53:28 2009
     Raid Level : raid5
  Used Dev Size : 976557376 (931.32 GiB 999.99 GB)
     Array Size : 2929672128 (2793.95 GiB 2999.98 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon May  9 03:15:02 2011
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 2aff2b94 - correct
         Events : 18323

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       18        1      active sync   /dev/sdb2

   0     0       0        0        0      removed
   1     1       8       18        1      active sync   /dev/sdb2
   2     2       8       50        2      active sync   /dev/sdd2
   3     3       8        2        3      active sync   /dev/sda2


Command:
mdadm --examine /dev/sdc2

Output:

/dev/sdc2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 568512ee:565410b0:3dcfe939:c4310215
  Creation Time : Thu Nov 12 16:53:28 2009
     Raid Level : raid5
  Used Dev Size : 976557376 (931.32 GiB 999.99 GB)
     Array Size : 2929672128 (2793.95 GiB 2999.98 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon May  9 01:32:30 2011
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 2aff0c83 - correct
         Events : 16517

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       34        0      active sync   /dev/sdc2

   0     0       8       34        0      active sync   /dev/sdc2
   1     1       8       18        1      active sync   /dev/sdb2
   2     2       8       50        2      active sync   /dev/sdd2
   3     3       8        2        3      active sync   /dev/sda2


Command:
mdadm --examine /dev/sdd2

Output:

/dev/sdd2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 568512ee:565410b0:3dcfe939:c4310215
  Creation Time : Thu Nov 12 16:53:28 2009
     Raid Level : raid5
  Used Dev Size : 976557376 (931.32 GiB 999.99 GB)
     Array Size : 2929672128 (2793.95 GiB 2999.98 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon May  9 03:15:02 2011
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 2aff2bb6 - correct
         Events : 18323

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       50        2      active sync   /dev/sdd2

   0     0       0        0        0      removed
   1     1       8       18        1      active sync   /dev/sdb2
   2     2       8       50        2      active sync   /dev/sdd2
   3     3       8        2        3      active sync   /dev/sda2



What shall I do? Please help.

Kind Regards
Carsten

---

### Post by rubylaser on 2011-05-09
What do you have in /etc/mdadm/mdadm.conf?  First, I'd stop all mdadm arrays that are running, and, if all your disks are intact and showing the same UUID (they are), I'd just force the array back together like this.

```
mdadm --assemble --run --force /dev/md0 /dev/sd[abcd]2
```

---

### Post by carstenw on 2011-05-09
Thanx for the fast reply,

my mdadm.conf is:

DEVICE partitions
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR root
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=568512ee:565410b0:3dcfe939:c4310215


Couldn't I loose any data by forcing the array? For it is RAID5 I could only afford one disk failing during this....

Can I reassemble in Read-Only mode and do some checks before I possibly blow my data away?

---

### Post by rubylaser on 2011-05-09
Your mdadm.conf file looks fine.

When the UUID's are matched up, which they are, you're not going to blow away any disks.  This will basically tell mdadm to put the disks back together.  There won't be a problem, either they will go back together properly, or fail to assemble which also won't hurt anything.

You can pass the --readonly option if you like, but as long as you have heathly disks (passes SMART tests), assembling without this option is fine.  Without assembling the array, there is no way to know if data is intact or not. 

I'm going to guess that you had a soft disconnect of a drive where it fell out of the array (maybe a bad cable, or power issue).  This is the proper way to put the array back together.  Your array shouldn't need to resync after reassembling, so after it brings the array up, just mount it, and backup your critical data.

---

### Post by carstenw on 2011-05-11
OK,

this gave a lot of additional information, for my problem was very similar:

[http://www.linuxquestions.org/questions/linux-general-1/raid5-with-mdadm-does-not-ron-or-rebuild-505361/](http://www.linuxquestions.org/questions/linux-general-1/raid5-with-mdadm-does-not-ron-or-rebuild-505361/)

Owing to rubylaser's words, I confidently started the task. First I double checked the individual disks. I used parted and fdisk to make sure I can access the disks and their information. Then

```
mdadm --misc --examine /dev/sd[abcd]2

```
and

```
mdadm --misc -QD /dev/sd[abcd]2

```
The events line showed three out of four drives with the same number. That looked good. Then I issued

```
mdadm --assemble --run --force /dev/md0 /dev/sd[abcd]2

```
which led me to an Input/Output error.

Ok, next I tried to out-comment md0 in mdadm.conf and rebooted the system

```
mdadm --stop /dev/md0
mdadm --assemble --no-degraded --force /dev/md0 /dev/sd[abcd]2

```
and yes, despite prior attempts I could successfully assemble the array. I took the chance to put the array into read-only mode to be safe

```
mdadm --misc -o /dev/md0

```
Let's try to stop and restart the array

```
mdadm --stop /dev/md0
mdadm --assemble --run --force /dev/md0 /dev/sd[abcd]2

```
It works! But still one drive is shown as not there

```
mdadm --misc -D /dev/md0

```
Ok, re-add the disk

```
mdadm --re-add /dev/md0 /dev/sdd2
mdadm --misc -D /dev/md0

```
It is re-syncing. Great! And best: I could mount it!!!

Next thing was to back it up as fast as I could ;-))

But: what happend??? Still I can not tell! Maybe some of you guys have an idea. What I can say: there was no power outage. The hardware is guarded by an UPS. Nobody touched it. In the logs you can see this:

```
May  1 00:57:01 pinguin kernel: [570515.997791] md: data-check of RAID array md0
May  1 00:57:01 pinguin kernel: [570515.997794] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
May  1 00:57:01 pinguin kernel: [570515.997796] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for data-check.
May  1 00:57:01 pinguin kernel: [570515.997802] md: using 128k window, over a total of 976557376 blocks.
May  1 05:35:56 pinguin kernel: [587251.261702] md: md0: data-check done.

(no array related things up to)

May  9 01:33:02 pinguin kernel: [1263876.985318] md: super_written gets error=-5, uptodate=0
May  9 01:33:03 pinguin mdadm[1298]: Fail event detected on md device /dev/md0, component device /dev/sdc2
May  9 03:15:35 pinguin kernel: [1270029.827472] md: super_written gets error=-5, uptodate=0
May  9 03:15:35 pinguin kernel: [1270029.832378] md: super_written gets error=-5, uptodate=0
May  9 03:15:35 pinguin mdadm[1298]: Fail event detected on md device /dev/md0, component device /dev/sdb2
May  9 03:15:35 pinguin mdadm[1298]: Fail event detected on md device /dev/md0, component device /dev/sdd2

```

So what happened?

Kind regards
Carsten

---

### Post by rubylaser on 2011-05-11
Is there anything else in the log?  It looks like the disks are soft disconnecting (maybe bad SATA cables, or controller). Was your data intact, and able to be backed up before the array crapped out again?

---

### Post by carstenw on 2011-05-11
I can't see anymore information in the logs which could be related to the array, controllers, hard disk errors, etc. So I guess this is it.

Glad, I have been able to double :-) backup all my data yesterday. Everything is still intact, even the last updated data. Since today 07:30 the array is running in read-write mode again and so far there are no indications of any problem in the logs.

Very strange - one for the X Files maybe.

C.

---


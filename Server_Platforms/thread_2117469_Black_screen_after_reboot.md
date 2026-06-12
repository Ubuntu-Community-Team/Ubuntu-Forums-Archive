---
title: "Black screen after reboot"
date: 2013-02-18
forum: Server Platforms
---

### Post by potmos79 on 2013-02-18
Hi, im a novice linux user haveing some trouble with my server.
Im running Ubuntu server 12.04.2, on a software raid 5.
After finally installing and booting (48 hours of googeling, reading and headscratching), it worked perfectly. But after a month im unable to ssh, or find it on the network. I go down to the basement, hook it up to a screen and keyboard to see whats wrong.
It gets to grub, and autoselects ubuntu, then the screen goes black, and nothing happens.
I try the rescue mode, and it ask me if i want to boot into degraded raid, it times out, choosing no while im contemplating the question. Then i get this:
ALERT! /dev/disk/by-uuid/ffc194d3-a7a7-4996-9eb6-d2ee41bf5cb4 does not exist
Dropping to shell!

Thinking there is something awry with my raid, I reboot, push e in grub and add the line bootdegraded=true to my default, and boot, as I wait triumphantly for everything to work, the screen goes black and nothing happens.

Anyone have any suggestions on what to try?

my setup is 3x 3Tb disk 
sda/b/c 1 bios grub
sda/b/c 2 raided swap
sda/b/c 3 root

ok, didi a bit of reading, bootet into a live cd, and tried the following:
mdadm --examine /dev/sda2
mdadm --examine /dev/sdb2
mdadm --examine /dev/sdc2
mdadm --examine /dev/sda3
mdadm --examine /dev/sdb3
mdadm --examine /dev/sdc3

and here i noticed something, they all seemes to be ok except sdc3:

/dev/sdc3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 4e79e911:8963aa50:19c5bc6b:dd4762ae
           Name : vilde:1
  Creation Time : Sat Jan 26 18:40:24 2013
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 5844641792 (2786.94 GiB 2992.46 GB)
     Array Size : 11689281536 (5573.88 GiB 5984.91 GB)
  Used Dev Size : 5844640768 (2786.94 GiB 2992.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 34d137c8:aa7ffd1a:4eeb6669:c8d6a680

    Update Time : Sun Feb 17 11:37:51 2013
       Checksum : b2632459 - correct
         Events : 58

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : ..A ('A' == active, '.' == missing)

sudo mdadm --assemble /dev/md1 /dev/sda3 /dev/sdb3 /dev/sdc3 -v
mdadm: looking for devices for /dev/md1
mdadm: cannot open device /dev/sda3: Device or resource busy
mdadm: /dev/sda3 has no superblock - assembly aborted

sudo mdadm --stop /dev/md1

sudo mdadm --assemble /dev/md1 /dev/sda3 /dev/sdb3 /dev/sdc3 -vmdadm: looking for devices for /dev/md1
mdadm: /dev/sda3 is identified as a member of /dev/md1, slot 0.
mdadm: /dev/sdb3 is identified as a member of /dev/md1, slot 1.
mdadm: /dev/sdc3 is identified as a member of /dev/md1, slot 2.
mdadm: added /dev/sda3 to /dev/md1 as 0
mdadm: added /dev/sdb3 to /dev/md1 as 1
mdadm: added /dev/sdc3 to /dev/md1 as 2
mdadm: /dev/md1 assembled from 1 drive - not enough to start the array.

sudo mdadm --assemble --force /dev/md1 /dev/sda3 /dev/sdb3 /dev/sdc3 -v
mdadm: looking for devices for /dev/md1
mdadm: /dev/sda3 is identified as a member of /dev/md1, slot 0.
mdadm: /dev/sdb3 is identified as a member of /dev/md1, slot 1.
mdadm: /dev/sdc3 is identified as a member of /dev/md1, slot 2.
mdadm: forcing event count in /dev/sda3(0) from 49 upto 58
mdadm: forcing event count in /dev/sdb3(1) from 49 upto 58
mdadm: added /dev/sdb3 to /dev/md1 as 1
mdadm: added /dev/sdc3 to /dev/md1 as 2
mdadm: added /dev/sda3 to /dev/md1 as 0
mdadm: /dev/md1 has been started with 3 drives.

---


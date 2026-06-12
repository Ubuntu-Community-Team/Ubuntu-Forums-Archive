---
title: "Shutdown/Reboot &quot;busy device&quot; message with raid1 array of four disk"
date: 2008-01-14
forum: Server Platforms
---

### Post by frankabel on 2008-01-14
Hi all,

I install Gutsy server and setup all systems partitions as radi1 (/, /boot, /var) during the installation. All seen ok, I just read after type "sudo reboot" a message like " error unmount /dev/md2 device busy", I really can't read it well, because disappear fast.

I'm really a little worry about that message regard so important partition.

Any comment?

Salute
Frank Abel

---

### Post by fozy on 2008-01-14
If your system hasn't been up for long it could still be building the array.  If you check mdstat ($ cat /proc/mdstat) you should be able to see if the status of the array.

---

### Post by frankabel on 2008-01-15
Thanks for you reply fozy.

I really don't think that, just look below the output of the commands executed just with few seconds of difference. All seen like the raid go to active and clean state in intervals of seconds. If clean mean what I think that mean, the array isn't still building. Beside, what I have mounted there is the /var partition of a fresh gutsy server installation, I mean isn't a heavy load partition, yet ;)

[PHP]sudo mdadm --query --detail /dev/md2
[sudo] password for frankabel:
/dev/md2:
        Version : 00.90.03
  Creation Time : Mon Jan 14 05:36:49 2008
     Raid Level : raid1
     Array Size : 3903680 (3.72 GiB 4.00 GB)
  Used Dev Size : 3903680 (3.72 GiB 4.00 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Tue Jan 15 06:04:12 2008
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

           UUID : d9fa5425:7655f7ff:b792e1c8:e3aaaffc
         Events : 0.5

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3
       2       8       35        2      active sync   /dev/sdc3
       3       8       51        3      active sync   /dev/sdd3
[/PHP]

[PHP]sudo mdadm --query --detail /dev/md2
/dev/md2:
        Version : 00.90.03
  Creation Time : Mon Jan 14 05:36:49 2008
     Raid Level : raid1
     Array Size : 3903680 (3.72 GiB 4.00 GB)
  Used Dev Size : 3903680 (3.72 GiB 4.00 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Tue Jan 15 06:04:15 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

           UUID : d9fa5425:7655f7ff:b792e1c8:e3aaaffc
         Events : 0.4

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3
       2       8       35        2      active sync   /dev/sdc3
       3       8       51        3      active sync   /dev/sdd3
[/PHP]

Thanks again!

Salute
Frank Abel

---


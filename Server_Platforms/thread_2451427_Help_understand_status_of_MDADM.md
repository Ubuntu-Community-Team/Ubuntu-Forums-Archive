---
title: "Help understand status of MDADM"
date: 2020-10-04
forum: Server Platforms
---

### Post by volkswagner on 2020-10-04
Greetings,

I have two RAID 10 arrays with four disks and one spare.
The RAID was configured during install.

I'm trying to understand if I had a failure and it used my spare.
What's confusing is md0 shows five devices and md1 shows four
devices. I expected to see md1 with five devices and one failed
device.

Checking smart on /dev/sdc shows problems so I believe there
is/was a failure, but it doesn't appear to be indicated via mdadm.

If sdc failed, shouldn't this be indicated by 'mdadm --detail' showing
one failed device with five total???



```
root@kvm01:~# smartctl -H /dev/sda
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.9.0-13-amd64] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Health Status: OK

root@kvm01:~# smartctl -H /dev/sdb
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.9.0-13-amd64] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Health Status: OK

root@kvm01:~# smartctl -H /dev/sdc
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.9.0-13-amd64] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Health Status: FAILURE PREDICTION THRESHOLD EXCEEDED [asc=5d, ascq=0]

root@kvm01:~# smartctl -H /dev/sdd
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.9.0-13-amd64] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Health Status: OK

root@kvm01:~# smartctl -H /dev/sde
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.9.0-13-amd64] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Health Status: OK
```





```
root@kvm01:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Wed Oct 23 15:53:19 2019
     Raid Level : raid10
     Array Size : 581632 (568.00 MiB 595.59 MB)
  Used Dev Size : 290816 (284.00 MiB 297.80 MB)
   Raid Devices : 4
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Sun Oct  4 06:25:33 2020
          State : clean 
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : near=2
     Chunk Size : 512K

           Name : unassigned-hostname:0
           UUID : b40656f2:95159a63:b22dc5eb:0e72a9e5
         Events : 72

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync set-A   /dev/sda1
       1       8       17        1      active sync set-B   /dev/sdb1
       2       8       33        2      active sync set-A   /dev/sdc1
       3       8       49        3      active sync set-B   /dev/sdd1

       4       8       65        -      spare   /dev/sde1
root@kvm01:~# mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Wed Oct 23 15:54:04 2019
     Raid Level : raid10
     Array Size : 1171273728 (1117.01 GiB 1199.38 GB)
  Used Dev Size : 585636864 (558.51 GiB 599.69 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Sun Oct  4 10:41:06 2020
          State : clean 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : near=2
     Chunk Size : 512K

           Name : unassigned-hostname:1
           UUID : 3b5ffd70:1bd56ef8:318e4d33:7da49443
         Events : 17714

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync set-A   /dev/sda2
       1       8       18        1      active sync set-B   /dev/sdb2
       4       8       66        2      active sync set-A   /dev/sde2
       3       8       50        3      active sync set-B   /dev/sdd2
```


EDIT:
Thank goodness for long log retention :)

I see back in July the device was failed.

```
Jul 24 11:20:19 kvm01 kernel: [19855254.899813] md/raid10:md1: read error corrected (8 sectors at 262152 on sdc2)
Jul 24 11:20:22 kvm01 kernel: [19855257.809044] sd 0:0:2:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 24 11:20:22 kvm01 kernel: [19855257.809058] sd 0:0:2:0: [sdc] tag#0 Sense Key : Hardware Error [current] 
Jul 24 11:20:22 kvm01 kernel: [19855257.809063] sd 0:0:2:0: [sdc] tag#0 Add. Sense: No defect spare location available
Jul 24 11:20:22 kvm01 kernel: [19855257.809068] sd 0:0:2:0: [sdc] tag#0 CDB: Read(10) 28 00 25 1c 6a 10 00 00 40 00
Jul 24 11:20:22 kvm01 kernel: [19855257.852386] md/raid10:md1: sdc2: Raid device exceeded read_error threshold [cur 21:max 20]
Jul 24 11:20:22 kvm01 kernel: [19855257.852388] md/raid10:md1: sdc2: Failing raid device
Jul 24 11:20:23 kvm01 kernel: [19855257.974756] md: recovery of RAID array md1
```

So question still remains: "why doesn't mdadm --detail reflect this failure?"

Was it too long ago???

Additionally, why isn't sdc1 failed for md0?

What is the best path to fix?
Should I manually fail sdc1 (or sdc) so I can replace it
and make its replacement the new spare?

---

### Post by TheFu on 2020-10-04
If you have an MTA configured, then any fault with mdadm or smartctl will send an email within 24 hours of the issue.

Sorry, I'm not expert on mdadm and don't use RAID10, so can't comment on those questions.

---

### Post by volkswagner on 2020-10-04
> **TheFu said:**
> If you have an MTA configured, then any fault with mdadm or smartctl will send an email within 24 hours of the issue.



Thanks,

Yes that's what I was doing today for all of my servers and when I ran the
test email, I got "[COLOR="#0000FF"]A SparesMissing event had been detected on md device /dev/md/1[/COLOR]"

---

### Post by darkod on 2020-10-04
I am not expert on mdadm too, but we have to consider that it works with partitions (usually, and in your case, yes).

My logic in this situation is that not whole of sdc failed. Your message logs does mention some parts about sdc but it says only sdc2 was detected as failed. So if the partition in md0 is considered good, no reason md0 to complain.

---

### Post by volkswagner on 2020-10-05
> **darkod said:**
> I am not expert on mdadm too, but we have to consider that it works with partitions (usually, and in your case, yes).

My logic in this situation is that not whole of sdc failed. Your message logs does mention some parts about sdc but it says only sdc2 was detected as failed. So if the partition in md0 is considered good, no reason md0 to complain.

I understand it only failed the partition. What I don't understand is why the disk count changed. 
I expect to see a failed drive and no spare with a total of five drives for md1.

---

### Post by darkod on 2020-10-05
Well I can't offer and good explanation why, but in this case it looks to me like sdc2 was considered not only Failed but also Removed. I believe in such case it will not show in the count of md1 any more. Usually you would do the --remove of failed member yourself, but...

---


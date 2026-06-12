---
title: "Ubuntu Lost hard drive sector"
date: 2016-04-25
forum: System76 Support
---

### Post by DerekdeClercq on 2016-04-25
I upgraded my server from 15.10 to 16.04 but did a clean install on a new disk. After the new installation the existing Raid 6 array failed to mount. Upon futher inspection it did not add 2 of the drives into the array. 
```
root@frikkie:~# mdadm --detail /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Mon Aug  4 14:45:22 2014
     Raid Level : raid6
     Array Size : 14650667520 (13971.97 GiB 15002.28 GB)
  Used Dev Size : 2930133504 (2794.39 GiB 3000.46 GB)
   Raid Devices : 7
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Mon Apr 25 20:42:16 2016
          State : clean, degraded
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : frikkie:127  (local to host frikkie)
           UUID : f3c63f2e:1639f650:690f15e0:7ec38f13
         Events : 2874602

    Number   Major   Minor   RaidDevice State
      10       8       32        0      active sync   /dev/sdc
       7       8        0        1      active sync   /dev/sda
       4       0        0        4      removed
       3       8       81        3      active sync   /dev/sdf1
       8       0        0        8      removed
       6       8       16        5      active sync   /dev/sdb
       8       8       64        6      active sync   /dev/sde
```


When I try and add them back I get the follow error:
mdadm: /dev/sdh not large enough to join array

Long story short it seems that the 2 disks which were removed from the array is now reporting 1 less cylinder than the other drives:
```

root@frikkie:~# sfdisk -g /dev/sd[a-h]
/dev/sda: **364801 **cylinders, 255 heads, 63 sectors/track
/dev/sdb: **364801 **cylinders, 255 heads, 63 sectors/track
/dev/sdc: **364801 **cylinders, 255 heads, 63 sectors/track
/dev/sdd: 243201 cylinders, 255 heads, 63 sectors/track
/dev/sde: **364801 **cylinders, 255 heads, 63 sectors/track
/dev/sdf: **364801 **cylinders, 255 heads, 63 sectors/track
/dev/sdg: **364800 **cylinders, 255 heads, 63 sectors/track
/dev/sdh: **364800 **cylinders, 255 heads, 63 sectors/track

```
The strange part is that these drives are exactly the same as some of the drives still in the array and working. In my config /dev/sdg and /dev/sdh is the drives removed. /dev/sda is a drive still in the array
**/sda**

```

root@frikkie:~# smartctl /dev/sda -a
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-21-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Model Family:     Seagate SV35
Device Model:     ST3000VX000-1CU166
Serial Number:    Z1F55F11
LU WWN Device Id: 5 000c50 06752c9f5
Firmware Version: CV23
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Form Factor:      3.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Mon Apr 25 20:53:12 2016 SAST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

**/dev/sdg**
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-21-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Model Family:     Seagate SV35
Device Model:     ST3000VX000-1CU166
Serial Number:    Z1F5BGFW
LU WWN Device Id: 5 000c50 06752c270
Firmware Version: CV23
User Capacity:    3,000,588,754,432 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Form Factor:      3.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Mon Apr 25 20:54:58 2016 SAST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

```
The problem is I cant just recreate the array is it is around 90% full and I dont have enough spare drives around to copy the data off and copy it back on and cant loose the data, thought raid 6 would be good for that :(

Is there any way to tell ubuntu to change the number of cylinders back?

If I have a look at the drive using hdparm it says both disks has the same number of sectors just that the 2 drives seem to be under reporting by exactly 1 cylinder less
```

root@frikkie:~# hdparm --dco-identify  /dev/sdh

/dev/sdh:
DCO Checksum verified.
DCO Revision: 0x0002
The following features can be selectively disabled via DCO:
        Transfer modes:
                 mdma0 mdma1 mdma2
                 udma0 udma1 udma2 udma3 udma4 udma5 udma6
        Real max sectors: 5860533168
        ATA command/feature sets:
                 SMART self_test error_log security HPA
                 streaming selective_test conveyance_test
                 WRITE_UNC_EXT
        SATA command/feature sets:
                 interface_power_management SSP
root@frikkie:~# hdparm --dco-identify  /dev/sda

/dev/sda:
DCO Checksum verified.
DCO Revision: 0x0002
The following features can be selectively disabled via DCO:
        Transfer modes:
                 mdma0 mdma1 mdma2
                 udma0 udma1 udma2 udma3 udma4 udma5 udma6
        Real max sectors: 5860533168
        ATA command/feature sets:
                 SMART self_test error_log security HPA
                 streaming selective_test conveyance_test
                 WRITE_UNC_EXT
        SATA command/feature sets:
                 interface_power_management SSP
root@frikkie:~#

```
Any suggestions, hints would be greatly appreciated

---

### Post by TheFu on 2016-04-26
Haven't seen the change in cylinder count before.

Please edit the OP and use "code tags" so that cmd output lines up in these forums. Much easier to read. More people will look closely too.

There is no substitute for backups. There are many things that can fail with RAID and backups are the way to fix them. RAID doesn't replace the need for backups.  RAID is for HA, only. Nothing else.  Backups can solve many more issues that RAID. Sometimes RAID is just a way to write corrupt data to multiple places concurrently. ;(  At least with versioned backups, there is a chance that the corrupted data will be noticed within the number of versions you backup, so it can be corrected.

Seagate - ah - seagate. You used to be the only disks I'd buy, then your management lied and denied for almost 2 yrs after a serious design issue happened. Returned to you once since then seagate, and that disk failed at 13 months old, 1 month AFTER the warranty was over.  Fool me once ... 

I'd check the power and sata/eSATA cables (swap them). Reseat on both ends too.  If that didn't solve it, run **badblocks** and see if those disks are failing and have lost enough to warrant complete replacement.  What does the SMART data show? How has that data changed over the least 12 months?   I'd probably order 2 more drives - non-seagate too. I'm partial to Hitachi 7200s, but WD and Toshiba are used here too. Slower/Green drives are used for backups over USB3.  RAID is SATA or eSATA or Infiniband (don't ask why) connections, never USB.  Oddly, some pre-lies Seagate drives 6x320G have been working great all this time. They are too old to trust for anything but sneaker-net and DVR use, but they still work and haven't shown any signs of failure.

Make a backup solution a top priority - tape or more disks. Using complex storage, without any redundancy (like now), is asking for data loss.  I've been buying 2x HDDs for the last 8 yrs - if I can't afford 2, I can't afford 1. For media, I use rsync to mirror the media to a backup disk. Had a tape system for years, but it became more costly than the $88 4TB Hitachis that go on sale every quarter.  For OS, settings, documents and other storage needs, I use rdiff-backup and keep 60-120 days of versioned backups.  I do use RAID for VMs where a failure would be bad.  Only issues I've had with it were due to cables coming loose (vibration) a few times.  

I've completely ignored the 16.04 issue. Sorry - don't have that here and plan to wait at least 2-3 months before trying it to let the early adopters find most of the issues.  That does bring up an idea - can you boot a 15.10 distro (live cd), install the mdadm packages, manually assemble the array then mount it? That would prove to me that it was a 16.04 issue, not HW. Just a thought.

I'd be worried about any data corruption which happened since the last time the system was booted too.  
Wish I could help more and I hope the issue is just a bad connection or failing cables.

---

### Post by DerekdeClercq on 2016-04-26
Hi TheFu, thanks a lot for the post and help. I also updated the original post as per your suggestion. Didnt even know about code tags :)

Seagate... sigh, yea I hear you. Up to now I have been lucky, only 1 drive would fail at a time in within warranty, so just kept on replacing them and the Raid helped so I didnt loose any data

And Backups, agree 100%. But this is for personal stuff , and finding an affordable backup solution for 13T is not so easy on this side of the world. So my reasoning was I can cope with up to 2 drives failing simultaneously, HA, of course the raid lost the 2 drives last night, and then one drive actually died today. ddrescue managed to get everything off except 80k so forced it back in and praying it was not an important 80k

Swapped cables like you would not believe. But did get to the bottom of the original problem. It seems that the drive somehow got kicked out of the array, probably a cable isssue, but when it did NPA was enabled, and I could see it using ```
hdparm -N /dev/sdx[CODE] turning it off using [CODE]hdparm -N p<size from before> /dev/sdx
``` gave me the full size back, and I could add it back into the array

Being as lucky as I am , when the raid was busy rebuilding was when the 3rd drive failed, hence ddrescue, forceing it into the array and all sorts of bad ideas

I dont think 16.04 was the issue, boothing back into the origianl 15.10 disk which I kept didnt help any on that side. Still not sure why the HPA option came on , and only on those drives, but guess that is one of life's mysteries

I guess there is no real way to as mdadm to perform an integrity check. Plan to do a xfs_check when I am done on the file system. Can at least see the file names, and mount it, so hopefully it is ok, assuming I have 80k missing across one or more filles, but all in all that is not something I should complain about

Thanks again for the help

---

### Post by TheFu on 2016-04-26
Glad it mostly worked out.  

Don't know where you are in the world, but I've seen a disk factory in Thailand from the freeway, which is the other side of the world for me. ;)  Didn't check pricing there - oddly, HDDs weren't really in my thoughts when visiting palaces, temples and other tourist things there.

I run weekly array scrubs for the mdadm RAID set here. The cmd inside root's crontab
```
12 4 * * 3 /usr/share/mdadm/checkarray --all --idle
```
Usually runs until 9am Wednesday. /usr/share/doc/mdadm/README.checkarray explains. Not sure how much it helps. In theory, it runs monthly automatically.

---

### Post by DerekdeClercq on 2016-04-26
South Africa on this side, our currency just lost 30% to the rest of the workd :/

awesome, never heard of checkarray so now I have so reading to do. Thx a lot for the help

---

### Post by TheFu on 2016-04-26
> **DerekdeClercq said:**
> South Africa on this side, our currency just lost 30% to the rest of the workd :/

awesome, never heard of checkarray so now I have so reading to do. Thx a lot for the help

30%!   Need to look at visiting again!  Wow - the 5 yr RAND chart is scary.  Little bump recently, but still ... 

Spent a few weeks in/around Cape Town a few years ago.  Lots of history (good and bad). Spoke at the CTLUG. Good group!  Nice enough place, though we didn't wander outside the tourist areas alone at night - it was early June, so daylight was limited.  Need to get back there - climb up table mountain, do the safari thing, and see other parts of the country. 

There's lots of great food there - tried [The Test Kitchen]("http://www.thetestkitchen.co.za/") for lunch. Amazing experience.  Robben Island is sorta like [MLK's memorial]("https://www.nps.gov/malu/index.htm") in my town.  Had to do it.
[Alexander's]("https://alexanderbar.co.za/") - a bar in downtown has a phone system on the tables written in python by one of the owners. Fun stuff. Tell Ed we said hello from [ATL/Churchhill Grounds]("http://www.churchillgrounds.com/").

I am not affiliated with any of these places, beside through friendship/happy customer.

Is November nice? Sorry - turning this into SA Travel thread. ;)

---

### Post by DerekdeClercq on 2016-04-26
Yea, or President played the markets for himself, the charts are really scary :(

If you are from pretty much anywhere SA is a cheap holiday, except for the flights, and those are not that bad really

Cape Town is certainly more of the exception to the rule, its in the Western Cape which is the only province run by a different political party. Johannesburg where I am from is a different story

For the most part if you common sense you can avoid the most violent crime, don't flash cash, wander off by yourself at night etc, goes for most of the word, just if you get it wrong crime tends to be more violent here

From you experiences I think you have the right places on the list for a holiday, only a 2 hour flight from Cape Town to Johannesburg, another hour or so to the Kurger park.

My recommendation would be Cape Town, surrounding areas, wine lands etc. Then maybe Kruger etc up north, avoid the Pretoria/Johannesburg area, not much to see there

History wise I think you will find we don't really have a lot, not compared to Europe and Asia. Not may buildings over a 100yrs even. Nature and weather wise I think is the best

November is summer, so for Cape Town that would mean moderate temperatures mostly not as much chance of rain as winter. Rest of the country the first rains should have fallen already and can be hot. Kruger park could start hitting around 40C, although not extremely high humidity. If rains have shown up then it would likely be a lot greener than winter.

Winter is around May - July but compared to most of the word doesn't really count, daytime temperatures typically over 10C in the middle of winder except maybe for a day or two

Hope it helps, and if you do come over you have a great time

---


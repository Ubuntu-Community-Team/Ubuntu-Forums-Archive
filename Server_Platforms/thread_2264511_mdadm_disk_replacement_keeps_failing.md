---
title: "mdadm disk replacement keeps failing"
date: 2015-02-08
forum: Server Platforms
---

### Post by h-b-jensen on 2015-02-08
Hi,

I have a Raid 5 setup thats been running for years. About 3 time I had a disk fail, and replaced it with a new one. I'm no Linux expert so I have been working mainly through webmin doing all this. 

2 months ago I had another disk fail, and I replaced it with a used disk I had laying around (according to sticker its almost 6 years old). At the same time I decided to reinstall the OS. I'm now running [COLOR=#393939][FONT=arial]Ubuntu Linux 14.10[/FONT][/COLOR]. 

A week ago I noticed degraded performance so I checked s.m.a.r.t status, and the the last added disk had 394 errors. I decided to buy a new one and swapped it in yesterday. This process went differently than usual. After boot madam didn't recover the raid. I got it back up by:
```
sudo [COLOR=#000000]mdadm --stop /dev/md127[/COLOR]
```
and 
```
[COLOR=#000000][FONT=sans-serif]mdadm --assemble --force /dev/md127[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif] /dev/sda2[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif] /dev/sdb2[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif] /dev/sdc2[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif] /dev/sdd2[/FONT][/COLOR]
```

The raid came up and started to rebuild itself. Speed was ok but after some hours someting happened.
```
[FONT=Menlo]henrik@ocean:~$ sudo mdadm --detail /dev/md127[/FONT][FONT=Menlo][sudo] password for henrik: [/FONT]
[FONT=Menlo]/dev/md127:[/FONT]
[FONT=Menlo]        Version : 0.90[/FONT]
[FONT=Menlo]  Creation Time : Sun Jan 16 16:54:05 2011[/FONT]
[FONT=Menlo]     Raid Level : raid5[/FONT]
[FONT=Menlo]     Array Size : 5766792000 (5499.64 GiB 5905.20 GB)[/FONT]
[FONT=Menlo]  Used Dev Size : 1922264000 (1833.21 GiB 1968.40 GB)[/FONT]
[FONT=Menlo]   Raid Devices : 4[/FONT]
[FONT=Menlo]  Total Devices : 4[/FONT]
[FONT=Menlo]Preferred Minor : 127[/FONT]
[FONT=Menlo]    Persistence : Superblock is persistent[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]    Update Time : Sun Feb  8 07:58:01 2015[/FONT]
[FONT=Menlo]          State : clean, FAILED [/FONT]
[FONT=Menlo] Active Devices : 2[/FONT]
[FONT=Menlo]Working Devices : 3[/FONT]
[FONT=Menlo] Failed Devices : 1[/FONT]
[FONT=Menlo]  Spare Devices : 1[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]         Layout : left-symmetric[/FONT]
[FONT=Menlo]     Chunk Size : 64K[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]           UUID : 6b4d814c:5c337c42:e68158d3:bcc31e01[/FONT]
[FONT=Menlo]         Events : 0.371442[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]    Number   Major   Minor   RaidDevice State[/FONT]
[FONT=Menlo]       0       0        0        0      removed[/FONT]
[FONT=Menlo]       2       0        0        2      removed[/FONT]
[FONT=Menlo]       2       8       34        2      active sync   /dev/sdc2[/FONT]
[FONT=Menlo]       3       8       50        3      active sync   /dev/sdd2[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]       4       8        2        -      faulty   /dev/sda2[/FONT]
[FONT=Menlo]       5       8       18        -      spare   /dev/sdb2[/FONT]
[FONT=Menlo]henrik@ocean:~$ sudo mdadm --detail /dev/md127[/FONT]
```

I rebooted and the raid didn't come up. I assembled it again and the same thing happened after some hours.

The disk I replaced is /dev/sdb. Why is it set as spare? Is it working as part of the raid? 

Should I replace /dev/sda now? It seems to have a fine s.m.a.r.t report.

The raid is up and I can access the data. But this situation is not stable. Any advice is appreciated.

/Henrik

---

### Post by h-b-jensen on 2015-02-08
Update: Once the raid has entered the state indicated above, I can't access my files. If I stop and re-assemble it, I can get to the files. All critical files are on Crashplan. Right now I'm copying the rest to another drive. Once it's all safe, I'll wipe the raid altogether create it from scratch. Better do a check of the disks before creating the new one.

---

### Post by darkod on 2015-02-08
Did you check its status before you forced it to assemble? It might have given you some points what is bothering it.

Before forcing it you should probably try something like 'mdadm --assemble --scan' but if there are issues with the array that will probably fail. Never the less, it's the first step to try assembling it without forcing it.

If you have a current copy of all the data you can try recreating it from scratch, as you say...

---


---
title: "ZFS issue system online no files showing"
date: 2018-01-04
forum: Server Platforms
---

### Post by mike.lussier on 2018-01-04
The server  went down after a patch and when it came backup only one of the three ZFS pools came back up. I powered down again and brought the system up and now all three are showing online. One shows degraded. When I check the directories there are no files. 

 root@mediaserver:/# zpool status
  pool: MASTER-EXPORT
 state: ONLINE
  scan: scrub repaired 140K in 0h17m with 0 errors on Sun Dec 10 00:41:02 2017
config:

    NAME                                          STATE     READ WRITE CKSUM
    MASTER-EXPORT                                 ONLINE       0     0     0
      raidz2-0                                    ONLINE       0     0     0
        ata-WDC_WD40EZRZ-00WN9B0_WD-WCC4E7CS738N  ONLINE       0     0     0
        ata-ST4000DM005-2DP166_ZGY0B2KT           ONLINE       0     0     0
        ata-ST4000DM000-1F2168_S3014GX0           ONLINE       0     0     0
        ata-ST4000DM005-2DP166_ZGY0B2G5           ONLINE       0     0     0
        ata-TOSHIBA_HDWD130_85JAWA6GS             ONLINE       0     0     0
        ata-TOSHIBA_HDWD130_85JBN6ZGS             ONLINE       0     0     0
        ata-WDC_WD30EZRX-00MMMB0_WD-WCAWZ2998711  ONLINE       0     0     0

errors: No known data errors

  pool: MOVIES-EXPORT
 state: DEGRADED
status: One or more devices could not be used because the label is missing or
    invalid.  Sufficient replicas exist for the pool to continue
    functioning in a degraded state.
action: Replace the device using 'zpool replace'.
   see: [http://zfsonlinux.org/msg/ZFS-8000-4J](http://zfsonlinux.org/msg/ZFS-8000-4J)
  scan: scrub repaired 0 in 4h10m with 0 errors on Sun Oct  8 04:34:50 2017
config:

    NAME                                 STATE     READ WRITE CKSUM
    MOVIES-EXPORT                        DEGRADED     0     0     0
      raidz2-0                           DEGRADED     0     0     0
        12821447247894784016             UNAVAIL      0     0     0  was /dev/disk/by-id/ata-ST33000651AS_Z290V48B-part1
        ata-TOSHIBA_HDWD130_85IBGP2GS    ONLINE       0     0     0
        ata-TOSHIBA_HDWD130_85JBK50GS    ONLINE       0     0     0
        ata-ST4000DM000-1F2168_S301477M  ONLINE       0     0     0

errors: No known data errors

  pool: TVRAID-EXPORT
 state: ONLINE
  scan: scrub repaired 0 in 6h2m with 0 errors on Sun Dec 10 06:26:27 2017
config:

    NAME                                          STATE     READ WRITE CKSUM
    TVRAID-EXPORT                                 ONLINE       0     0     0
      raidz2-0                                    ONLINE       0     0     0
        ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0M36MY4  ONLINE       0     0     0
        ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0M5LYAK  ONLINE       0     0     0
        ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0M7MYH6  ONLINE       0     0     0
        ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0M9C3TZ  ONLINE       0     0     0

errors: No known data errors

root@mediaserver:/#  zfs list
NAME            USED  AVAIL  REFER  MOUNTPOINT
MASTER-EXPORT   133G  12.1T   133G  /MASTER-EXPORT
MOVIES-EXPORT  2.45T  2.65T  2.45T  /MOVIES-EXPORT
TVRAID-EXPORT  2.00T  3.10T  2.00T  /TVRAID-EXPORT

root@mediaserver:/home/mediaserver# zpool list
NAME            SIZE  ALLOC   FREE  EXPANDSZ   FRAG    CAP  DEDUP  HEALTH  ALTROOT
MASTER-EXPORT    19T   200G  18.8T         -     0%     1%  1.00x  ONLINE  -
MOVIES-EXPORT  10.9T  5.06T  5.81T         -    24%    46%  1.00x  DEGRADED  -
TVRAID-EXPORT  10.9T  4.13T  6.74T         -    17%    37%  1.00x  ONLINE  -

---

### Post by howefield on 2018-01-04
Thread moved to the "*Server Platforms*" forum.

---

### Post by mike.lussier on 2018-01-05
I recently updated my mediaserver and this required a reboot. When the server came backup only one of  the three ZFS pools came back up. I preformed a shutdown and powered the server backup again . Now all three are showing online. One of the three shows as degraded. 

When  I check the directories there are no files in any of them. What has happened here ?  

 root@mediaserver:/# zpool status
  pool: MASTER-EXPORT
 state: ONLINE
  scan: scrub repaired 140K in 0h17m with 0 errors on Sun Dec 10 00:41:02 2017
config:

    NAME                                          STATE     READ WRITE CKSUM
    MASTER-EXPORT                                 ONLINE       0     0     0
      raidz2-0                                    ONLINE       0     0     0
        ata-WDC_WD40EZRZ-00WN9B0_WD-WCC4E7CS738N  ONLINE       0     0     0
        ata-ST4000DM005-2DP166_ZGY0B2KT           ONLINE       0     0     0
        ata-ST4000DM000-1F2168_S3014GX0           ONLINE       0     0     0
        ata-ST4000DM005-2DP166_ZGY0B2G5           ONLINE       0     0     0
        ata-TOSHIBA_HDWD130_85JAWA6GS             ONLINE       0     0     0
        ata-TOSHIBA_HDWD130_85JBN6ZGS             ONLINE       0     0     0
        ata-WDC_WD30EZRX-00MMMB0_WD-WCAWZ2998711  ONLINE       0     0     0

errors: No known data errors

  pool: MOVIES-EXPORT
 state: DEGRADED
status: One or more devices could not be used because the label is missing or
    invalid.  Sufficient replicas exist for the pool to continue
    functioning in a degraded state.
action: Replace the device using 'zpool replace'.
   see: [http://zfsonlinux.org/msg/ZFS-8000-4J](http://zfsonlinux.org/msg/ZFS-8000-4J)
  scan: scrub repaired 0 in 4h10m with 0 errors on Sun Oct  8 04:34:50 2017
config:

    NAME                                 STATE     READ WRITE CKSUM
    MOVIES-EXPORT                        DEGRADED     0     0     0
      raidz2-0                           DEGRADED     0     0     0
        12821447247894784016             UNAVAIL      0     0     0  was /dev/disk/by-id/ata-ST33000651AS_Z290V48B-part1
        ata-TOSHIBA_HDWD130_85IBGP2GS    ONLINE       0     0     0
        ata-TOSHIBA_HDWD130_85JBK50GS    ONLINE       0     0     0
        ata-ST4000DM000-1F2168_S301477M  ONLINE       0     0     0

errors: No known data errors

  pool: TVRAID-EXPORT
 state: ONLINE
  scan: scrub repaired 0 in 6h2m with 0 errors on Sun Dec 10 06:26:27 2017
config:

    NAME                                          STATE     READ WRITE CKSUM
    TVRAID-EXPORT                                 ONLINE       0     0     0
      raidz2-0                                    ONLINE       0     0     0
        ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0M36MY4  ONLINE       0     0     0
        ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0M5LYAK  ONLINE       0     0     0
        ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0M7MYH6  ONLINE       0     0     0
        ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0M9C3TZ  ONLINE       0     0     0

errors: No known data errors

root@mediaserver:/#  zfs list
NAME            USED  AVAIL  REFER  MOUNTPOINT
MASTER-EXPORT   133G  12.1T   133G  /MASTER-EXPORT
MOVIES-EXPORT  2.45T  2.65T  2.45T  /MOVIES-EXPORT
TVRAID-EXPORT  2.00T  3.10T  2.00T  /TVRAID-EXPORT

root@mediaserver:/home/mediaserver# zpool list
NAME            SIZE  ALLOC   FREE  EXPANDSZ   FRAG    CAP  DEDUP  HEALTH  ALTROOT
MASTER-EXPORT    19T   200G  18.8T         -     0%     1%  1.00x  ONLINE  -
MOVIES-EXPORT  10.9T  5.06T  5.81T         -    24%    46%  1.00x  DEGRADED  -
TVRAID-EXPORT  10.9T  4.13T  6.74T         -    17%    37%  1.00x  ONLINE  -

---

### Post by mike.lussier on 2018-01-05
Can anyone explain why this fix work ? 

zpool export MASTER-EXPORT
zpool import -d /dev/disk/by-id MASTER-EXPORT

zpool export TVRAID-EXPORT
zpool import -d /dev/disk/by-id TVRAID-EXPORT

zpool export MOVIES-EXPORT
zpool import -d /dev/disk/by-id MOVIES-EXPORT

---

### Post by cariboo on 2018-01-05
Merged similar threads.

---


---
title: "How to find hard drives to add to ZFS pool."
date: 2016-10-10
forum: Server Platforms
---

### Post by craig02 on 2016-10-10
I have a zpool that had 2 spares.  2 drives failed and I replace/removed the spares into the pool.  I have replaced the 2 bad drives in the chassis.  I cannot find the drives to add them as spares for the pool.  The controller "sees" them at boot.

Any tips on how to get these drives added as spares?  Thx!

Ubuntu 14.04.3
ZFS: Loaded module v0.6.5.3-1~trusty, ZFS pool version 5000, ZFS filesystem version 5

pool: tankz2
 state: ONLINE
status: The pool is formatted using a legacy on-disk format.  The pool can
    still be used, but some features are unavailable.
action: Upgrade the pool using 'zpool upgrade'.  Once this is done, the
    pool will no longer be accessible on software that does not support
    feature flags.
  scan: resilvered 607G in 14h50m with 0 errors on Fri Sep 30 06:50:55 2016
config:


    NAME                        STATE     READ WRITE CKSUM
    tankz2                      ONLINE       0     0     0
      raidz2-0                  ONLINE       0     0     0
        scsi-2001b4d2013330251  ONLINE       0     0     0
        scsi-2001b4d2013135530  ONLINE       0     0     0
        scsi-2001b4d2013330213  ONLINE       0     0     0
        scsi-2001b4d2019823308  ONLINE       0     0     0
        scsi-2001b4d2013332298  ONLINE       0     0     0
        scsi-2001b4d2013130711  ONLINE       0     0     0
        scsi-2001b4d2013135559  ONLINE       0     0     0
        scsi-2001b4d2013131505  ONLINE       0     0     0
        scsi-2001b4d201313058a  ONLINE       0     0     0
        scsi-2001b4d2013134785  ONLINE       0     0     0
        scsi-2001b4d201903d852  ONLINE       0     0     0
      raidz2-1                  ONLINE       0     0     0
        scsi-2001b4d20cba67200  ONLINE       0     0     0
        scsi-2001b4d202b7a7b00  ONLINE       0     0     0
        scsi-2001b4d20bb027000  ONLINE       0     0     0
        scsi-2001b4d20abed7700  ONLINE       0     0     0
        scsi-2001b4d20abe27d00  ONLINE       0     0     0
        scsi-2001b4d20ab9d7a00  ONLINE       0     0     0
        scsi-2001b4d20aa777d00  ONLINE       0     0     0
        scsi-2001b4d20aa777200  ONLINE       0     0     0
        scsi-2001b4d20bb587100  ONLINE       0     0     0
        scsi-2001b4d20ab1c7000  ONLINE       0     0     0
        scsi-2001b4d2013133712  ONLINE       0     0     0


errors: No known data errors

---

### Post by Vegan on 2016-10-10
[COLOR="#FF0000"]sudo lshw -class disk[/COLOR]

this will show you all disks the OS can see

---

### Post by craig02 on 2016-10-11
> **Vegan said:**
> [COLOR=#FF0000]sudo lshw -class disk[/COLOR]

this will show you all disks the OS can see

Thanks!  The drives did show up there.

What I eventually needed to get the SCSI IDs to add to pool was:
```
ls -l /dev/disk/by-id
```

---


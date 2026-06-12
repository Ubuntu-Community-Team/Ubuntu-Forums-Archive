---
title: "Convert ZFS Z1 to Z2?"
date: 2014-03-01
forum: Server Platforms
---

### Post by L473X on 2014-03-01
Hey all, 

I'm running Ubuntu 12.04.3 LTS utilizing the  zfs-fuse 0.6.9-1build1 package. Wondering if it's possible to transform a Z1 pool to Z2 using a couple of additional disks. My configuration is as follows.

```

NAME    SIZE  ALLOC   FREE    CAP  DEDUP  HEALTH  ALTROOT
media  7.25T  4.74T  2.51T    65%  1.00x  ONLINE  -
  pool: media
 state: ONLINE
 scrub: none requested
config:


        NAME                                                     STATE     READ WRITE CKSUM
        media                                                    ONLINE       0     0     0
          raidz1-0                                               ONLINE       0     0     0
            disk/by-id/ata-WDC_WD20EARS-00MVWB0_WD-WMAZA4037604  ONLINE       0     0     0
            disk/by-id/ata-WDC_WD20EARS-00MVWB0_WD-WMAZA4037653  ONLINE       0     0     0
            disk/by-id/ata-WDC_WD20EARS-00MVWB0_WD-WMAZA4037517  ONLINE       0     0     0
            disk/by-id/ata-WDC_WD20EARS-00MVWB0_WD-WMAZA3640056  ONLINE       0     0     0

```

---

### Post by tgalati4 on 2014-03-01
It looks possible to simply add disks to the array and have them add to the mirror redundancy according to FreeBSD's [zpool manpage]("http://www.freebsd.org/cgi/man.cgi?query=zpool&sektion=8&n=1").  I presume similar capability exists in the linux port.  But you will have to test it.  Of course any zpool operations can put your data at risk.  Remember RAID is not a backup strategy.

---

### Post by rubylaser on 2014-03-02
No it's not possible.  You can add individual disks or vdevs to an existing pool, but you can't reshape a pool like you can with mdadm, snapraid, or other hardware raid solutions.  Reshaping inflexibility is really one of ZFS's only shortcomings.  To move to a raidz2, you would need to backup your data and create a new raidz2 pool.

---

### Post by lukeiamyourfather on 2014-03-04
ZFS doesn't support migration. If you want RAID Z2 you'll need to create the vdev/pool again with that configuration. It's possible to create a already degraded RAID Z/Z2/Z3 using sparse files at creation time, remove the sparse files, and then later replace the sparse files with actual disks.

[http://jeanbruenn.info/2011/01/18/setting-up-zfs-with-3-out-of-4-discs-raidz/](http://jeanbruenn.info/2011/01/18/setting-up-zfs-with-3-out-of-4-discs-raidz/)

I wouldn't recommend doing this though because it increases the risk of losing data, especially if the degraded state leaves zero redundancy (why even bother with ZFS at that point).

---


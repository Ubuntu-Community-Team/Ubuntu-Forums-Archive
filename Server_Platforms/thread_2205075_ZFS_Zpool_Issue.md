---
title: "ZFS Zpool Issue"
date: 2014-02-11
forum: Server Platforms
---

### Post by alzyee on 2014-02-11
When replacing a failed drive in a raidz configuration I typed 
```
sudo zpool add PoolName /dev/NewDrive
```
To my dismay this added it as a new part of the raid. How do I remove "sdb" from pool without destroying the raid?

Additional information about system:
Raidz w/ 6 total drives (basically 5+1 for parity) named Disk2

Output of  zpool status after disconnecting sdb as a test and finding this breaks the raid.
```
sudo zpool status Disk2

      NAME                                                       STATE     READ WRITE CKSUM
        Disk2                                                      FAULTED      0     0     0  corrupted data
          raidz1-0                                                 DEGRADED     0     0     0
            disk/by-id/ata-Hitachi_HDS723020BLA642_MN1220F320V0UD  ONLINE       0     0     0
            disk/by-id/ata-ST3000DM001-9YN166_S1F0HKQJ             ONLINE       0     0     0
            disk/by-id/ata-Hitachi_HDS723020BLA642_MN1220F31VJ58D  ONLINE       0     0     0
            disk/by-id/ata-Hitachi_HDS723020BLA642_MN1220F32268AD  ONLINE       0     0     0
            disk/by-id/ata-Hitachi_HDS723020BLA642_MN1220F3214VSD  ONLINE       0     0     0
            disk/by-id/ata-Hitachi_HDS723020BLA642_MN1220F32253WD  UNAVAIL      0     0     0  cannot open
          sdb                                                      FAULTED      0     0     0  corrupted data
```

---

### Post by Frogs Hair on 2014-02-13
***Moved Per Request***

---

### Post by lukeiamyourfather on 2014-02-27
ZFS doesn't allow for the removal of a vdev from a storage pool, they can only grow not shrink. I believe you'll have to start from scratch again if you want to remove vdev "sdb" from the pool. For future reference the proper command to replace a failed disk is below.

```
sudo zpool replace *BAD DISK* *GOOD DISK*
```

In your case it would look something like this assuming the replacement disk was similar (where the last five digits of the ID would be something else).

```
sudo zpool replace ata-Hitachi_HDS723020BLA642_MN1220F32253WD ata-Hitachi_HDS723020BLA642_MN1220F32XXXXX
```

Always use a unique name when adding devices whether this is /dev/disk/by-id or another method like the /etc/vdev_id.conf file. Also read the manual first before you do anything with "sudo" in the command.

```
man zpool
```

---


---
title: "ZFS DEGRADED Help"
date: 2018-02-01
forum: Server Platforms
---

### Post by mmitchell-indigex on 2018-02-01
Hi I had multiple drives fail in my ZFS array with in a day or so. I shutdown and got new drives installed and let the host scrub the data. The pool is currently working, but I am unable to remove the old failed drive ID's now. Any suggestions would be really appreciated. Bellow is the current output of zpool status. I understand that I have data errors and that those won't be able to be recovered. This is an internal file based backup server that does daily snapshots that roll off after 30 days so I expect that after the drive issue is resolved all data errors should be gone in 30 days. 

In my searching the best "solution" I can find is just to rebuild the pool. Unfortunately, I don't have the hardware to do that without first destroying this pool. While I do have other copies of this data, I would prefer to not have to rebuild this pools and wait for it to copy the data again.

```
~# zpool status  pool: backup
 state: DEGRADED
status: One or more devices has experienced an error resulting in data
        corruption.  Applications may be affected.
action: Restore the file in question if possible.  Otherwise restore the
        entire pool from backup.
   see: http://zfsonlinux.org/msg/ZFS-8000-8A
  scan: scrub repaired 0 in 14h28m with 412 errors on Fri Jan 26 22:49:09 2018
config:


        NAME                                   STATE     READ WRITE CKSUM
        backup                                 DEGRADED     0     0   854
          raidz1-0                             ONLINE       0     0     0
            sdi                                ONLINE       0     0     0
            sde                                ONLINE       0     0     0
            sdh                                ONLINE       0     0     0
            sdd                                ONLINE       0     0     0
          raidz1-1                             DEGRADED     0     0 1.67K
            sdj                                ONLINE       0     0     0
            replacing-1                        DEGRADED     0     0     0
              7990249564917294300              UNAVAIL      0     0     0  was /dev/disk/by-id/ata-ST3000DM008-2DM166_Z504M5B1-part1
              sdc                              ONLINE       0     0     0
            spare-2                            DEGRADED     0     0     0
              41413732360099735                UNAVAIL      0     0     0  was /dev/sdg1
              ata-ST3000DM008-2DM166_Z504M9L4  ONLINE       0     0     0
            sdf                                ONLINE       0     0     0
        spares
          ata-ST3000DM008-2DM166_Z504M9L4      INUSE     currently in use


errors: 412 data errors, use '-v' for a list



```

Any ideas or help is greatly appreciated.

---

### Post by darkod on 2018-02-01
Can something from here help you?

I think you needed to "remove" the old disk before actually replacing it, or something like that... Anyway, these links seem to have what you need.

[https://askubuntu.com/questions/305830/replacing-a-dead-disk-in-a-zpool](https://askubuntu.com/questions/305830/replacing-a-dead-disk-in-a-zpool)
[https://docs.oracle.com/cd/E19253-01/819-5461/gbcet/index.html](https://docs.oracle.com/cd/E19253-01/819-5461/gbcet/index.html)

---

### Post by mmitchell-indigex on 2018-02-02
Thanks for the quick reply, unfortunately these did not help. Whenever I try to detach, offline, remove a drive I get: "cannot [offline, detach, remove] [drive number]: no valid replicas". Even though zpool status show that the replacement drive is good and online.

For example:

```
zpool detach backup 41413732360099735
cannot detach 41413732360099735: no valid replicas
```

or 
```

zpool offline backup 7990249564917294300
cannot offline 7990249564917294300: no valid replicas

```

---

### Post by darkod on 2018-02-02
Can you post the output of the following commands (put sudo in front if not running as root):
```
zpool status
zdb
```

---

### Post by mmitchell-indigex on 2018-02-02
Sure can. Thanks for taking a look.

```

~# zpool status
  pool: backup
 state: DEGRADED
status: One or more devices has experienced an error resulting in data
        corruption.  Applications may be affected.
action: Restore the file in question if possible.  Otherwise restore the
        entire pool from backup.
   see: http://zfsonlinux.org/msg/ZFS-8000-8A
  scan: scrub repaired 0 in 14h28m with 412 errors on Fri Jan 26 22:49:09 2018
config:


        NAME                                   STATE     READ WRITE CKSUM
        backup                                 DEGRADED     0     0   854
          raidz1-0                             ONLINE       0     0     0
            sdi                                ONLINE       0     0     0
            sde                                ONLINE       0     0     0
            sdh                                ONLINE       0     0     0
            sdd                                ONLINE       0     0     0
          raidz1-1                             DEGRADED     0     0 1.67K
            sdj                                ONLINE       0     0     0
            replacing-1                        DEGRADED     0     0     0
              7990249564917294300              UNAVAIL      0     0     0  was /dev/disk/by-id/ata-ST3000DM008-2DM166_Z504M5B1-part1
              sdc                              ONLINE       0     0     0
            spare-2                            DEGRADED     0     0     0
              41413732360099735                UNAVAIL      0     0     0  was /dev/sdg1
              ata-ST3000DM008-2DM166_Z504M9L4  ONLINE       0     0     0
            sdf                                ONLINE       0     0     0
        spares
          ata-ST3000DM008-2DM166_Z504M9L4      INUSE     currently in use


errors: 412 data errors, use '-v' for a list

```

```

~# zdb
backup:
    version: 5000
    name: 'backup'
    state: 0
    txg: 8835884
    pool_guid: 18125415157003437429
    errata: 0
    hostid: 8323329
    hostname: 'zfs-server'
    vdev_children: 2
    vdev_tree:
        type: 'root'
        id: 0
        guid: 18125415157003437429
        children[0]:
            type: 'raidz'
            id: 0
            guid: 12858025102235220981
            nparity: 1
            metaslab_array: 35
            metaslab_shift: 36
            ashift: 12
            asize: 12002313371648
            is_log: 0
            create_txg: 4
            children[0]:
                type: 'disk'
                id: 0
                guid: 17037524781439355558
                path: '/dev/disk/by-id/ata-ST3000DM001-1CH166_Z1F2P3P1-part1'
                whole_disk: 1
                DTL: 4294
                create_txg: 4
            children[1]:
                type: 'disk'
                id: 1
                guid: 5772654082808727230
                path: '/dev/disk/by-id/ata-ST3000DM008-2DM166_ZA507CEP-part1'
                whole_disk: 1
                DTL: 16134
                create_txg: 4
            children[2]:
                type: 'disk'
                id: 2
                guid: 7181558114421077261
                path: '/dev/disk/by-id/ata-ST3000DM001-1ER166_Z5038LH8-part1'
                whole_disk: 1
                DTL: 4288
                create_txg: 4
            children[3]:
                type: 'disk'
                id: 3
                guid: 15621813875067958851
                path: '/dev/disk/by-id/ata-ST3000DM001-1CH166_Z1F1J3GJ-part1'
                whole_disk: 1
                DTL: 4287
                create_txg: 4
        children[1]:
            type: 'raidz'
            id: 1
            guid: 12967754437773242754
            nparity: 1
            metaslab_array: 39
            metaslab_shift: 36
            ashift: 12
            asize: 12002313371648
            is_log: 0
            create_txg: 6
            children[0]:
                type: 'disk'
                id: 0
                guid: 11409800855953706233
                path: '/dev/disk/by-id/ata-ST3000DM001-1ER166_Z501STC8-part1'
                whole_disk: 1
                DTL: 518
                create_txg: 6
            children[1]:
                type: 'replacing'
                id: 1
                guid: 5167781461166575267
                whole_disk: 0
                create_txg: 6
                children[0]:
                    type: 'disk'
                    id: 0
                    guid: 7990249564917294300
                    path: '/dev/disk/by-id/ata-ST3000DM008-2DM166_Z504M5B1-part1'
                    whole_disk: 1
                    not_present: 1
                    DTL: 53
                    create_txg: 6
                children[1]:
                    type: 'disk'
                    id: 1
                    guid: 25763228075033572
                    path: '/dev/disk/by-id/ata-ST3000DM008-2DM166_Z5053C82-part1'
                    whole_disk: 1
                    DTL: 16390
                    create_txg: 6
                    resilver_txg: 8835881
            children[2]:
                type: 'spare'
                id: 2
                guid: 1343664196537971701
                whole_disk: 0
                create_txg: 6
                children[0]:
                    type: 'disk'
                    id: 0
                    guid: 41413732360099735
                    path: '/dev/disk/by-id/ata-ST3000DM001-1CH166_Z1F1HEHK-part1'
                    whole_disk: 1
                    DTL: 4291
                    create_txg: 6
                children[1]:
                    type: 'disk'
                    id: 1
                    guid: 6860405596614517340
                    path: '/dev/disk/by-id/ata-ST3000DM008-2DM166_Z504M9L4-part1'
                    whole_disk: 1
                    is_spare: 1
                    DTL: 7134
                    create_txg: 6
                    resilver_txg: 8504809
            children[3]:
                type: 'disk'
                id: 3
                guid: 6729700817208874470
                path: '/dev/disk/by-id/ata-ST3000DM001-1ER166_Z5013EJJ-part1'
                whole_disk: 1
                DTL: 4290
                create_txg: 6
    features_for_read:
        com.delphix:hole_birth
        com.delphix:embedded_data



```

---

### Post by darkod on 2018-02-02
I haven't worked too much with zfs unfortunately, but what I think is the situation is:

1. Your raidz1-1 array is degraded because a disk failed. It looks like 7990249564917294300 is being replaced (or was replaced) by sdc. But I think you still need to manually mark it as offline. Until you do that it keeps saying 'replacing' like the process never finished.

2. Looking at your two spares, 41413732360099735 is also bad (unavailable) and the other spare is good and in use (is it the sdc disk maybe???). Again I think you need to remove the bad spare. You can't use it when it says unavailable anyway.

Unfortunately you tried that and got errors for both commands. I reread your original post again and it seems you simply shut down and replaced the drives, right? You didn't offline them first? From what I read now quickly it's best to offline the unavailable disks first.

I think your replacing actually never finished correctly, from one reason or another. And from the zdb output, it looks to me like the unavailable disk 7990249564917294300 needs to be replaced with the new disk 25763228075033572.

If that is what you think too, you can try something like:
```
zpool replace backup 7990249564917294300 25763228075033572
```

Check the zpool status and see if it starts resilvering. Did you check if it did resilvering after you replaced the disks? Because I think if it didn't, that's a sure sign the replacement actually never finished...

If the above works we'll deal with the spare disks later.

---

### Post by mmitchell-indigex on 2018-02-05
Thanks for the suggestions darkod, but yes it did resilver after putting in the disks.

```
~# zpool replace backup 7990249564917294300 25763228075033572cannot open '25763228075033572': no such device in /dev
must be a full path or shorthand device name
```

So I tried full name:

```
~# zpool replace backup 7990249564917294300 /dev/disk/by-id/ata-ST3000DM008-2DM166_Z5053C82invalid vdev specification
use '-f' to override the following errors:
/dev/disk/by-id/ata-ST3000DM008-2DM166_Z5053C82-part1 is part of active pool 'backup'

```

This concerns me a bit just due to the status of the drive already being online.

---

### Post by darkod on 2018-02-05
Unfortunately this is beyond my ZFS knowledge... It seems the failed disks are in sort of inconsistent state in the ZFS because they weren't offlined before being replaced. Maybe ZFS is really sensitive to that process. Or you hit some weird bug...

You better ask for more specialized help on zfs forums. It doesn't matter you are running it on ubuntu, if they have some advice with zfs commands to run, it should probably work.

---

### Post by mmitchell-indigex on 2018-02-05
Thanks for your time and help looking into this. I'll try that next.

---


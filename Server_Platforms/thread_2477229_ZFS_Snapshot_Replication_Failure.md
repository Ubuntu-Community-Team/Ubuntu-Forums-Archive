---
title: "ZFS Snapshot Replication Failure"
date: 2022-07-18
forum: Server Platforms
---

### Post by venom85 on 2022-07-18
I have two nearly identical file servers that use ZFS pools consisting of seven 4 TB disks in RaidZ2. One of them is my primary onsite storage server, and the other is an offsite backup (currently on the same LAN for maintenance/recovery purposes though). Each of the disks is a single vdev, very straightforward. I have a fully-updated Ubuntu Server 20.04.4 LTS, and I have used this setup going all the way back to 16.04.

Here is the pool status:

```
  pool: data state: ONLINE
  scan: scrub repaired 0B in 2 days 09:35:05 with 0 errors on Mon Jul  4 07:35:08 2022
config:


        NAME                        STATE     READ WRITE CKSUM
        data                        ONLINE       0     0     0
          raidz2-0                  ONLINE       0     0     0
            wwn-0x50014ee263fbe71e  ONLINE       0     0     0
            wwn-0x50014ee209508354  ONLINE       0     0     0
            wwn-0x50014ee2b478c476  ONLINE       0     0     0
            wwn-0x50014ee2b76abed3  ONLINE       0     0     0
            wwn-0x50014ee20e58397f  ONLINE       0     0     0
            wwn-0x5000c50050004ae2  ONLINE       0     0     0
            wwn-0x50014ee2100e228d  ONLINE       0     0     0


errors: No known data errors
```

My system creates a snapshot every 2 hours, after which it replicates it to the backup server. The command I use to send the snapshots is (example):

```
/sbin/zfs send -v -p -R -I data@20220709-060001 data@20220709-080001 | /usr/bin/lz4c | /usr/bin/ssh  -o BatchMode=yes -o StrictHostKeyChecking=no -o ConnectTimeout=7 nas2.example.com /usr/bin/lz4c -d | /sbin/zfs receive -F data && echo 'Snapshot replicated successfully'
```

Again, this has been running successfully for years, and no changes have been made to any of the snapshot management.

Recently, at least within the last few months, the snapshots have shown up strangely in my replication logs and have triggered the disappearance of my descendant datasets. The snapshots are named as you see in the previous command: pool[/dataset]@timestamp. So the pool's name is 'data', and I have descendent datasets such as 'mysql' and 'influxdb'. Here is the full listing:

```
NAME                TYPE        MOUNTPOINT                      AVAIL   USED  USEDSNAP  USEDDS  USEDREFRESERV  USEDCHILD
data                filesystem  /data                           64.7G  16.2T      803G   15.1T             0B       350G
data/ds1            filesystem  /family_datasets/ds1            64.7G   115G        0B    115G             0B         0B
data/ds2            filesystem  /family_datasets/ds2            83.9G  20.8G        0B   20.8G             0B         0B
data/ds3            filesystem  /family_datasets/ds3            88.8G  15.9G        0B   15.9G             0B         0B
data/influxdb       filesystem  /var/lib/influxdb               69.1G  95.5G     8.64G   86.9G             0B         0B
data/mysql          filesystem  /var/lib/mysql                  64.7G  54.1G     34.4G   19.8G             0B         0B
```

Typically, I use the recursive option to get all of those to replicate correctly. However, when I do that now, instead of seeing a list of correct snapshot mnames that will be replicated at the start of the command, I get this:

```
send from @20220712-220002 to data@20220713-000001 estimated size is 184M
send from @20220713-000001 to data@20220713-020001 estimated size is 398M
send from @20220713-020001 to data@20220713-040001 estimated size is 151M
send from @20220713-040001 to data@20220713-060002 estimated size is 98.6M
send from @20220713-060002 to data@20220713-080001 estimated size is 49.0M
...
```

Notice the "from" name is just the @timestamp, as opposed to the pool (and dataset, if applicable) name. When I allow that to replicate, it blows away all descendent datasets on the target. Does anybody have any suggestions for what I can look at or why this might be happening? I have already started over once, doing a full re-replication to reset my backup system. As soon as I finish the first replication and do a dry run on the incremental, it resumes the same behavior. Thanks for any help you can provide me!

---


---
title: "ZFS : Unable to get rid of error in a pool"
date: 2017-07-07
forum: Server Platforms
---

### Post by thegarbz@yahoo.com.au on 2017-07-07
Hi all,

I'm having a problem with one of my ZFS pools. A quick history: The pool had a failing drive that started throwing smart errors followed a day later by checksum errors. So I ran out and bought another drive and started the replacement process. During the resilvering process one of the other drives in the 3 drive raidz1 array threw a transient I/O error resulting in an error on a single file. No problem I have backups and it's a media server so I'm not attached to the file anyway.

Activities leading up to this point:
```
2017-07-04.20:50:30 zpool scrub pool2
2017-07-04.21:31:35 zpool clear pool2
2017-07-05.17:02:21 zpool offline pool2 ata-WDC_WD20EZRX-00D8PB0_WD-WMC4N1544956
2017-07-05.17:05:03 zpool import -c /etc/zfs/zpool.cache -aN
2017-07-05.17:19:51 zpool replace pool2 ata-WDC_WD20EZRX-00D8PB0_WD-WMC4N1544956 /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K2AZ74F7
2017-07-06.08:08:00 zpool clear pool2
2017-07-06.08:25:01 zpool offline pool2 ata-WDC_WD20EZRX-00D8PB0_WD-WMC4N1544956
2017-07-06.08:26:51 zpool detach pool2 ata-WDC_WD20EZRX-00D8PB0_WD-WMC4N1544956
2017-07-06.23:03:38 zpool scrub pool2
2017-07-06.23:03:38 zpool clear pool2
2017-07-07.07:30:45 zpool scrub -s pool2
2017-07-07.07:35:51 zpool scrub pool2
2017-07-07.07:35:58 zpool scrub -s pool2
2017-07-07.07:36:13 zpool clear -F pool2
2017-07-07.18:58:26 zpool import -c /etc/zfs/zpool.cache -aN
2017-07-07.19:02:21 zpool offline pool2 ata-WDC_WD40EFRX-68N32N0_WD-WCC7K2AZ74F7
2017-07-07.19:06:50 zpool clear pool2
2017-07-07.19:14:28 zpool online pool2 ata-WDC_WD40EFRX-68N32N0_WD-WCC7K2AZ74F7

```

So a bit of debugging is happening in there already. Here are my questions.:
1. After replacing the drive I was stuck with the drive not actually removing from the system. The replace command was supposed to do this automatically on completion from what I have read. Anyway a quick offline and a detach followed by ... A Resilver? For some reason the drive decided to resilver twice. Is this a sign of something?
2. The sequence of scrubs, clear, scrub cancels, clear -F, offline and online were attempts to fix the problem below. 
3. I don't understand where the "import" command is coming from. My other pool doesn't have import commands. EDIT1: The import command coincides with reboots. I don't understand why only pool2 is showing these and not pool1.
4. I cycled the power to my server today. It's now doing a complete resilver AGAIN on the same drive. What gives?
5. When I ran zpool history, pool1 showed up instantly.  Pool2 took a long time to respond. EDIT1: Due to resilvering in progress. 

6. And finally the biggest concern, I can't clear the error in the file on my pool: 
```
root@zeus:~# zpool status -vx  
pool: pool2
 state: ONLINE
status: One or more devices is currently being resilvered.  The pool will
        continue to function, possibly in a degraded state.
action: Wait for the resilver to complete.
  scan: resilver in progress since Fri Jul  7 19:14:14 2017
    2.70T scanned out of 4.95T at 146M/s, 4h29m to go
    915G resilvered, 54.45% done
config:

        NAME                                          STATE     READ WRITE CKSUM
        pool2                                         ONLINE       0     0    10
          raidz1-0                                    ONLINE       0     0    38
            ata-WDC_WD40EFRX-68N32N0_WD-WCC7K2AZ74F7  ONLINE       0     0     0  (resilvering)
            ata-ST2000DM001-9YN164_Z1E0TDHM           ONLINE       0     0     0
            ata-WDC_WD20EARX-00PASB0_WD-WCAZA6682714  ONLINE       0     0     0

errors: Permanent errors have been detected in the following files:
        pool2/a:<0x2f007>

```

As you can see it is still resilvering, but more importantly I have checksum errors and a file error pointing to an inode. Now I can't clear these errors. This is the state the system has been in after every scrub and resilver for the past few days. It has persisted through reboots and through attempts to kill every program accessing that file system. A clear will make all the errors go away, but a scrub will bring up that inode reference again. As far as I can tell from all the documentation that inode is supposed to clear itself through a scrub when nothing is accessing the (presumably) deleted file. But I can't get rid of it. 

So in summary:
[LIST=1]
[*]Any idea how to clear the error.
[*]Any idea why i'm resilvering again after a relatively innocuous reboot, and is it related to the constant "import" commands I see in my history which aren't present in any other pool?
[/LIST]

Thanks in advance for any help. I'm running out of Google fu at this point. I am however open to a few days more effort before I destroy the entire pool and recovery from a backup.

---

### Post by thegarbz@yahoo.com.au on 2017-07-08
Okay some further debugging:

**History taking too long issue:**
Is a result of running history while a resilver is in progress. This morning it ran fine.

**Import issue:**
The "import -c /etc/zpool.cache -aN" coincides with reboots. What I don't understand is the difference between Pool1 and Pool2 on my server in this case. From the code below you can see that Pool1 doesn't have the import line in it's history. Also below you can see that pool2 has a spontaneous scan in its history that I also don't understand. Is this because the pool has errors? One of the scans triggered the resilver yesterday. 

```
root@zeus:~# zpool history pool1 -i
2017-07-05.17:04:49 [txg:9280129] open pool version 5000; software version 5000/5; uts zeus 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64
2017-07-05.17:04:54 [txg:9280131] import pool version 5000; software version 5000/5; uts zeus 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64
2017-07-07.18:58:17 [txg:9314620] open pool version 5000; software version 5000/5; uts zeus 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64
2017-07-07.18:58:18 [txg:9314622] import pool version 5000; software version 5000/5; uts zeus 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64

```

And pool2
```
root@zeus:~# zpool history pool2 -i
2017-07-07.18:58:20 [txg:9262870] open pool version 5000; software version 5000/5; uts zeus 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64
2017-07-07.18:58:20 [txg:9262872] import pool version 5000; software version 5000/5; uts zeus 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64
2017-07-07.18:58:26 zpool import -c /etc/zfs/zpool.cache -aN
2017-07-07.18:58:26 [txg:9262874] scan setup func=2 mintxg=3 maxtxg=9230266
2017-07-07.19:02:21 zpool offline pool2 ata-WDC_WD40EFRX-68N32N0_WD-WCC7K2AZ74F7
2017-07-07.19:05:47 [txg:9262960] scan done complete=0
2017-07-07.19:05:47 [txg:9262960] scan setup func=2 mintxg=3 maxtxg=9262959
2017-07-07.19:06:50 zpool clear pool2

2017-07-07.19:07:12 zpool online pool2 ata-WDC_WD40EFRX-68N32N0_WD-WCC7K2AZ74F7
2017-07-07.19:14:14 [txg:9263058] scan setup func=2 mintxg=3 maxtxg=9263056
2017-07-08.07:09:11 [txg:9271095] scan done complete=1

```


**And to the one I can't fix yet: The unclearable error.**

Using zdb to explore the file gives me some more valuable information:
```

root@zeus:~# zdb -dddd pool2/a 0x2f007
Dataset pool2/a [ZPL], ID 42, cr_txg 25, 2.60T, 876432 objects, rootbp DVA[0]=<0:2a0618d8000:2000> DVA[1]=<0:4183b66a000:2000> [L0 DMU objset] fletcher4 uncompressed LE contiguous unique double size=800L/800P birth=9266472L/9266472P fill=876432 cksum=d333e0b7d:fc6b89555bb:b0c9612902930:5b968548af711ef


    Object  lvl   iblk   dblk  dsize  lsize   %full  type
    192519    4    16K   128K  2.34G  2.34G  100.00  ZFS plain file
                                        168   bonus  System attributes
        dnode flags: USED_BYTES USERUSED_ACCOUNTED
        dnode maxblkid: 19197
        path    ???<object#192519>
        uid     115
        gid     125
        atime   Tue Jul  4 20:43:33 2017
        mtime   Tue Jul  4 20:44:20 2017
        ctime   Tue Jul  4 20:44:20 2017
        crtime  Tue Jul  4 19:58:20 2017
        gen     9215301
        mode    100640
        size    2516284283
        parent  192518
        links   0
        pflags  40800000004


^C

```

What's with the ^C? Well the command seems to lock up. zdb -dddd is supposed to also show the block that the file was previously assigned to but after letting this command sit and stew for a few minutes it simply doesn't show. 

The prevailing information on the internet says that this is due to a deleted file that is locked. Well we when I check the zpool's deletion queue you can actually see it is ready to be deleted:
```
root@zeus:~# zdb -dddd pool2/a 3
Dataset pool2/a [ZPL], ID 42, cr_txg 25, 2.60T, 876432 objects, rootbp DVA[0]=<0:2a0618d8000:2000> DVA[1]=<0:4183b66a000:2000> [L0 DMU objset] fletcher4 uncompressed LE contiguous unique double size=800L/800P birth=9266472L/9266472P fill=876432 cksum=d333e0b7d:fc6b89555bb:b0c9612902930:5b968548af711ef


    Object  lvl   iblk   dblk  dsize  lsize   %full  type
         3    1    16K  8.50K      0  8.50K  100.00  ZFS delete queue
        dnode flags: USED_BYTES USERUSED_ACCOUNTED
        dnode maxblkid: 0
        microzap: 8704 bytes, 1 entries


                2f007 = 192519

```

But this is supposed to happen automatically when the file becomes free. However the file is not locked by any process and persists through reboots:
```
root@zeus:~# lsof |grep -c 192519
0
root@zeus:~# zfs umount pool2/a
root@zeus:~# zfs mount pool2/a

```

By all accounts reboots, unmounts, clearing processes, and a scrub should have removed this error by now but so far to no avail. Also for some reason I the block reference is still missing in zdb.

---

### Post by thegarbz@yahoo.com.au on 2017-07-08
More debugging:

Something is fundamentally screwed. The resilver took place just fine, everything is listed as online however if I copy a file from the array I see: 

```


--------------------------------------------  -----  -----  -----  -----  -----  -----
pool2                                         4.90T   550G    324      0  40.1M      0
  raidz1                                      4.90T   550G    324      0  40.1M      0
    ata-WDC_WD40EFRX-68N32N0_WD-WCC7K2AZ74F7      -      -    206      0   1.1M      0
    ata-ST2000DM001-9YN164_Z1E0TDHM               -      -    188      0  17.1M      0
    ata-WDC_WD20EARX-00PASB0_WD-WCAZA6682714      -      -    130      0  11.4M      0
--------------------------------------------  -----  -----  -----  -----  -----  -----

```

That is a major imbalance and it looks like the new drive isn't being read at all. So I figured what the hell I'll try off-lining something, I have full redundancy anyway. 

```

root@zeus:/# zpool offline pool2 ata-ST2000DM001-9YN164_Z1E0TDHM
cannot offline ata-ST2000DM001-9YN164_Z1E0TDHM: no valid replicas

root@zeus:/# zpool offline pool2  ata-WDC_WD40EFRX-68N32N0_WD-WCC7K2AZ74F7

root@zeus:/# zpool status pool2
  pool: pool2
 state: DEGRADED
status: One or more devices has experienced an error resulting in data
        corruption.  Applications may be affected.
action: Restore the file in question if possible.  Otherwise restore the
        entire pool from backup.
   see: http://zfsonlinux.org/msg/ZFS-8000-8A
  scan: resilvered 1.64T in 11h54m with 2 errors on Sat Jul  8 07:09:11 2017
config:


        NAME                                          STATE     READ WRITE CKSUM
        pool2                                         DEGRADED     0     0     0
          raidz1-0                                    DEGRADED     0     0     0
            ata-WDC_WD40EFRX-68N32N0_WD-WCC7K2AZ74F7  OFFLINE      0     0     0
            ata-ST2000DM001-9YN164_Z1E0TDHM           ONLINE       0     0     0
            ata-WDC_WD20EARX-00PASB0_WD-WCAZA6682714  ONLINE       0     0     0


errors: 1 data errors, use '-v' for a list

```

So zfs seems to recognise that despite being resilvered (twice, and taking a long time each time) the new drive does not contain a valid replica of the previous files!!!!! I can only offline the new drive, not the existing ones.

---


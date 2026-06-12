---
title: "mdadm won't assemble an array that I *think* is clean... help?"
date: 2010-12-26
forum: Server Platforms
---

### Post by ljwobker on 2010-12-26
upgraded from 9.10 to 10.4, and somewhere in the process I managed to get my raid5 array out of whack, and I'm not entirely sure how.

The array was created with level 5, 3 devices (sda1, sdb1, sdc1), each a 1TB drive with a single partition on it.  Note that sd[abc] are the raid devices, and sdd is the boot drive.

When I try to assemble the array, I get something like this:

```
root@lwobker-fs:~# mdadm --assemble /dev/md0 /dev/sd[acb]1
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.
```which clearly is not what I'm looking for.  I *think* somehow I've gotten the superblocks out of sync, but I'm not smart enough to figure out what exactly is going on.  I've started with what I think is the basic info for troubleshooting (fdisk, mdadm examine, proc/mdstat, etc)... I can provide whatever else is needed...

muchas gracias for any help here...

**fdisk -l:**  (bonus question... anyone know why the devices are in a,c,b order instead of a,b,c?)
```
root@lwobker-fs:~# fdisk -l | grep dev
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
/dev/sda1               1      121108   972799978+  83  Linux
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
/dev/sdc1               1      121108   972799978+  83  Linux
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
/dev/sdb1               1      121108   972799978+  83  Linux
Disk /dev/sdd: 8011 MB, 8011120640 bytes

```**cat /proc/mdstat**:
```
root@lwobker-fs:~# cat /proc/mdstat
Personalities : 
unused devices: <none>
```**subset of mdadm --examine:**  [B]NOTE that the "State" lines do not appear to agree with each other, and neither do the Update times.  Everything else in --examine appears to be the same on all drives (full output a little lower)...

[/B]```
root@lwobker-fs:~# mdadm --examine /dev/sd[abc]1 | egrep 'dev|Update|Role|State'
/dev/sda1:
          State : clean
    Update Time : Sun Dec 26 00:18:30 2010
   Device Role : Active device 2
   Array State : ..A ('A' == active, '.' == missing)
/dev/sdb1:
          State : clean
    Update Time : Tue Sep 28 18:59:45 2010
   Device Role : Active device 1
   Array State : AAA ('A' == active, '.' == missing)
/dev/sdc1:
          State : clean
    Update Time : Sun Dec 26 00:16:28 2010
   Device Role : Active device 0
   Array State : A.A ('A' == active, '.' == missing)
```**mdadm --examine:**
```

root@lwobker-fs:~# mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 1.1
    Feature Map : 0x0
     Array UUID : f82a311d:93d4f3a1:cd359611:8b50ce19
           Name : lwobker-fs:0  (local to host lwobker-fs)
  Creation Time : Fri Feb 12 11:58:25 2010
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 1945599693 (927.73 GiB 996.15 GB)
     Array Size : 3891197952 (1855.47 GiB 1992.29 GB)
  Used Dev Size : 1945598976 (927.73 GiB 996.15 GB)
    Data Offset : 264 sectors
   Super Offset : 0 sectors
          State : clean
    Device UUID : f4035780:5bd340e6:21d9468d:f944050b

    Update Time : Sun Dec 26 00:18:30 2010
       Checksum : d332943d - correct
         Events : 8060

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : ..A ('A' == active, '.' == missing)
root@lwobker-fs:~# mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.1
    Feature Map : 0x0
     Array UUID : f82a311d:93d4f3a1:cd359611:8b50ce19
           Name : lwobker-fs:0  (local to host lwobker-fs)
  Creation Time : Fri Feb 12 11:58:25 2010
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 1945599693 (927.73 GiB 996.15 GB)
     Array Size : 3891197952 (1855.47 GiB 1992.29 GB)
  Used Dev Size : 1945598976 (927.73 GiB 996.15 GB)
    Data Offset : 264 sectors
   Super Offset : 0 sectors
          State : clean
    Device UUID : 2c1050e8:eb321107:f37b8b8a:b9fc56d2

    Update Time : Tue Sep 28 18:59:45 2010
       Checksum : 201fe374 - correct
         Events : 1310

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAA ('A' == active, '.' == missing)
root@lwobker-fs:~# mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.1
    Feature Map : 0x0
     Array UUID : f82a311d:93d4f3a1:cd359611:8b50ce19
           Name : lwobker-fs:0  (local to host lwobker-fs)
  Creation Time : Fri Feb 12 11:58:25 2010
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 1945599693 (927.73 GiB 996.15 GB)
     Array Size : 3891197952 (1855.47 GiB 1992.29 GB)
  Used Dev Size : 1945598976 (927.73 GiB 996.15 GB)
    Data Offset : 264 sectors
   Super Offset : 0 sectors
          State : clean
    Device UUID : e0b77465:531d19cd:e5609b47:326babe8

    Update Time : Sun Dec 26 00:16:28 2010
       Checksum : 37223f9a - correct
         Events : 8050

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : A.A ('A' == active, '.' == missing)

```

---

### Post by ljwobker on 2010-12-27
In case anyone searches and stumbles across this... the solution (at least in my case) was:

1) one of the drives had been detached multiple months ago-- I wasn't aware of this and it complicated the issue.


2) to use the "force" switch to force assembly of the array with the two "good" drives.  I did this:

```
mdadm --assemble -force /dev/md0 /dev/sda1 /dev/sdc1 
```(the two "good" partitions) were sda1 and sdc1,  then --re-add back in the sdb1 device.

About 10 hours of rebuilding later, I have a happily humming 3 drive array again.  (whee!)

---


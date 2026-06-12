---
title: "ubuntu14 installation, caused raid10 array to stay inactive"
date: 2014-10-28
forum: Server Platforms
---

### Post by rollyah on 2014-10-28
I have two raid arrays on my system:
[LIST=1] 
[*]raid1: /dev/sdd1 /dev/sdh1 
[*]raid10: /dev/sde1 /dev/sda1 /dev/sdf1 /dec/sdb1 /dev/sdc1 /dev/sdg1  
[/LIST]

two disks had bad sectors: sdd and sdf <<-- they both got hot swapped. i added sdf back to raid10 and recovery took place but adding sdd1 to raid1 proved to be troublesome
as i didn't have anything important on '/' i formatted and installed ubuntu 14 on raid1 

now system is up on raid 1, **but** raid10 (md127) is inactive

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : inactive sde1[2](S) sdg1[8](S) sdc1[6](S) sdb1[5](S) sdf1[4](S) sda1[3](S)
      17580804096 blocks super 1.2
       
md2 : active raid1 sdh4[0] sdd4[1]
      2921839424 blocks super 1.2 [2/2] [UU]
      [==>..................]  resync = 10.4% (304322368/2921839424) finish=672.5min speed=64861K/sec
      
md1 : active raid1 sdh3[0] sdd3[1]
      7996352 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sdh2[0] sdd2[1]
      292544 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>


```

if i try to assemble md127 
```
mdadm --assemble /dev/md127 /dev/sde1 /dev/sda1 /dev/sdf1 /dec/sdb1 /dev/sdc1 /dev/sdg1  
```
i get this:
```
assembled from 5 drives and 1 rebuilding - not enough to start the array
```


what does it mean ? is my data lost ? 

if i examine one of the md127 raid 10 array disks it shows this:

```
mdadm --examine /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : ab90d4c8:41a55e14:635025cc:28f0ee76
           Name : ubuntu:data  (local to host ubuntu)
  Creation Time : Sat May 10 21:54:56 2014
     Raid Level : raid10
   Raid Devices : 8

 Avail Dev Size : 5860268032 (2794.39 GiB 3000.46 GB)
     Array Size : 11720534016 (11177.57 GiB 12001.83 GB)
  Used Dev Size : 5860267008 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : a2a5db61:bd79f0ae:99d97f17:21c4a619

    Update Time : Tue Oct 28 10:07:18 2014
       Checksum : 409deeb4 - correct
         Events : 8655

         Layout : near=2
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAAAAAA ('A' == active, '.' == missing)

```


**Used Dev Size : 5860267008 (2794.39 GiB 3000.46 GB)** <<--- does this mean i still have my data ? 



any help on how to solve this is appreciated

---


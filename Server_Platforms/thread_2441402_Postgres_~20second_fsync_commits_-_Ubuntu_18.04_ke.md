---
title: "Postgres ~20second fsync commits - Ubuntu 18.04 kernel 5.3.0-26"
date: 2020-04-23
forum: Server Platforms
---

### Post by priit3344 on 2020-04-23
Pre word and spec description.




Dell bare metal blades.
OS - 5.3.0-26-generic #28~18.04.1-Ubuntu server.  Installed top of RAID1 SSD hard disks
Databases and other non OS related stuff comes over FCOE <<<--->>> Netapp SSD disks. 


On top of Ubuntu we are using LXC containers to serve Different PG 10-12 ver instances.


Problem Description. 


As much as we love to use LXC containers we cannot figure out what is causing us expensive 20s fsync commits. Well actually I have my doubts on FCOE but there is
no good way to prove it and solve. So the main problem is that at some X point I see from perf trace such long fsync commits


448518504.667 (20419.143 ms): postmaster/19996 fsync(fd: 3</var/lib/pg_wal/archive_status>)                          = 0
448538979.500 (20423.963 ms): postmaster/19996 fsync(fd: 3</var/lib/pg_wal/archive_status>)                          = 0
448538971.725 (20431.760 ms): postmaster/19046 fsync(fd: 444</var/lib/pg_wal/xlogtemp.29141>)                        = 0
448560529.836 (21398.736 ms): postmaster/19372 fsync(fd: 20</var/lib/pg_wal/xlogtemp.13932>)                         = 0
448560540.753 (21387.800 ms): postmaster/19996 fsync(fd: 3</var/lib/pg_wal/archive_status>)                          = 0
448602760.972 (20133.112 ms): postmaster/19372 fsync(fd: 20</var/lib/pg_wal/xlogtemp.13932>)                         = 0
448623009.417 (20373.001 ms): postmaster/19996 fsync(fd: 3</var/lib/pg_wal/archive_status>)                          = 0
448622998.519 (20383.886 ms): postmaster/22137 fsync(fd: 26</var/lib/pg_wal/xlogtemp.30142>)                         = 0
448645268.889 (20629.215 ms): postmaster/19996 fsync(fd: 3</var/lib/pg_wal/archive_status>)                          = 0
448645263.299 (20634.792 ms): postmaster/18749 fsync(fd: 419</var/lib/pg_wal/xlogtemp.29097>)                        = 0
448668234.041 (20191.750 ms): postmaster/19372 fsync(fd: 20</var/lib/pg_wal/xlogtemp.13932>)                         = 0
448668238.215 (20187.558 ms): postmaster/19996 fsync(fd: 3</var/lib/pg_wal/archive_status>)                          = 0
448688567.132 (20338.312 ms): postmaster/19996 fsync(fd: 3</var/lib/pg_wal/archive_status>)                          = 0


and those 20sec commits pull db performance very low. I see tons of different locks and so on. And this behaivour has been on all the new kenrnel versions I´ve tested. 


The only working combination I could achieve was Centos 7.6 + Kernel 3.10 and LXC containers on top of it. But Centos with old Kernel cant get along well and there are a lot of LXC/LXD daemon related issues. But in general this has been the only working combinatio.   I´ve tried Centos + newer kernels (4 and 5)  and the same 20s commits starts to happen.


The last combination what we are currently using  (mentioned in spec) it works util some moment where the acutal load kicks in and fsync commits are getting back to 20s which is bad. 






So Can anyone come up with some ideas what to try OR FCoE itself is a mix of coctail with Ubuntu and LXC and there is no point of using it ? 
Maybe threre are some Kernel parameters to tune OR some specific FCOE driver configuration ? Im out of ideas bymyself here. 






Happy to share more information and answer the questions.

---

### Post by SeijiSensei on 2020-04-23
Have you tried running one of the servers on bare metal?  Does it have the same performance problems?

---


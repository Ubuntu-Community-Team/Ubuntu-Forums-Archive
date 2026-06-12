---
title: "multipathd stops at /dev/sdz"
date: 2012-03-05
forum: Server Platforms
---

### Post by upnix on 2012-03-05
Running an up-to-date Ubuntu 10.04.4 LTS.

Using iSCSI, I'm mapping various volumes to this Ubuntu server. Each volume as 8 paths to the server, so many /dev/sd* devices are being made. However, multipath seems to ignore any device after /dev/sdz. There are more devices there for sure (/dev/sdaa, /dev/sdab, etc), but they're not being used by multipath.

Example:
```

root@hostname:/vmfs# ls -1 /dev/sda*
/dev/sda
...
/dev/sdaa1
/dev/sdab
/dev/sdab1
/dev/sdac
/dev/sdac1
...
root@hostname:/vmfs# multipath -ll
Database3 (200173800018b0202) dm-6 IBM     ,2810XIV       
[size=992G][features=1 queue_if_no_path][hwhandler=0]
\_ round-robin 0 [prio=3][active]
 \_ 7:0:0:4  sdl 8:176  [active][ready]
 \_ 6:0:0:4  sdk 8:160  [active][ready]
 \_ 5:0:0:4  sdm 8:192  [active][ready]
Database2 (200173800018b01e8) dm-1 IBM     ,2810XIV       
[size=992G][features=1 queue_if_no_path][hwhandler=0]
\_ round-robin 0 [prio=3][active]
 \_ 7:0:0:3  sdi 8:128  [active][ready]
 \_ 5:0:0:3  sdj 8:144  [active][ready]
 \_ 6:0:0:3  sdh 8:112  [active][ready]
Database1 (200173800018b01ff) dm-0 IBM     ,2810XIV       
[size=992G][features=1 queue_if_no_path][hwhandler=0]
\_ round-robin 0 [prio=4][active]
 \_ 7:0:0:2  sdg 8:96   [active][ready]
 \_ 5:0:0:2  sdf 8:80   [active][ready]
 \_ 6:0:0:2  sdd 8:48   [active][ready]
 \_ 8:0:0:2  sdz 65:144 [active][ready]
system (200173800018b01fe) dm-9 IBM     ,2810XIV       
[size=960G][features=1 queue_if_no_path][hwhandler=0]
\_ round-robin 0 [prio=6][active]
 \_ 7:0:0:1  sde 8:64   [active][ready]
 \_ 6:0:0:1  sdb 8:16   [active][ready]
 \_ 5:0:0:1  sdc 8:32   [active][ready]
 \_ 10:0:0:1 sdy 65:128 [active][ready]
 \_ 8:0:0:1  sdw 65:96  [active][ready]
 \_ 9:0:0:1  sdx 65:112 [active][ready]
Database2_1 (200173800018b0205) dm-7 IBM     ,2810XIV       
[size=992G][features=1 queue_if_no_path][hwhandler=0]
\_ round-robin 0 [prio=3][active]
 \_ 7:0:0:5  sdn 8:208  [active][ready]
 \_ 6:0:0:5  sdo 8:224  [active][ready]
 \_ 5:0:0:5  sdp 8:240  [active][ready]
mpath9 (200173800018b0207) dm-8 IBM     ,2810XIV       
[size=992G][features=1 queue_if_no_path][hwhandler=0]
\_ round-robin 0 [prio=3][active]
 \_ 7:0:0:7  sds 65:32  [active][ready]
 \_ 5:0:0:7  sdv 65:80  [active][ready]
 \_ 6:0:0:7  sdu 65:64  [active][ready]
mpath8 (200173800018b0206) dm-4 IBM     ,2810XIV       
[size=992G][features=1 queue_if_no_path][hwhandler=0]
\_ round-robin 0 [prio=3][active]
 \_ 7:0:0:6  sdq 65:0   [active][ready]
 \_ 5:0:0:6  sdt 65:48  [active][ready]
 \_ 6:0:0:6  sdr 65:16  [active][ready]
root@hostname:/vmfs# ls -1 /dev/mapper/
control
Database1
Database-part1
Database2
Database2_1
Database_1-part1
Database2-part1
Database3
Database3-part1
mpath8
mpath8-part1
mpath9
mpath9-part1
system
system-part1

```

Now this is after a machine reboot. If I map another volume, rescan and restart multipathd, the /dev/sd* devices shows up, but nothing in /dev/mapper/. After a restart, the new volume will show up, but drive letters get shuffled, and some volumes will now only have 3 paths. Again, never registering anything after /dev/sdz.


Anyone know what's going on here?

Edit: I should add, I can mount these individual /dev/sdaa,b,c devices. So I'm fairly confident it's a problem with multipath and not iSCSI.

---


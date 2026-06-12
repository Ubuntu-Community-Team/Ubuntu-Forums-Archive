---
title: "RAID 5 crashed on Synology - deleted wrong drive by mistake"
date: 2019-09-16
forum: Server Platforms
---

### Post by jgaitan85 on 2019-09-16
[COLOR=#000000]Hello everyone,
new to this forum. I been reading other issues and have seen good results with the help of everyone involved. hoping we can end up with a smiley face on my issue too
here is what happened step by step

Synology NAS complained about bad drive. 
I purchased new drive and was replacing it
when doing so I ended up removing drive 4 instead of 2
doing so synology formatted the drive at removal and thats when I saw all red everywhere.
I put back the drive and the whole system just wasnt working anymore.
the failing drive still in there along with the other 3 drives that are good, but the formatted one is seen by the raid as spare now.
I attempted to mount with a USB to sata sabrent cable I have but windows wont mount with this table errors and mac doesnt see the drive. I tried the same with Kali thumbdrive I have and doesnt see it either. starting to think the adapter isnt compatible.
so I started to dig a little more and saw I can ssh into synology to see the status of the drives. here is the output as I know its the info most other issues have requested. 

OUTPUT

[/COLOR]**admin@JAGNAS001**:**~**$ cat /proc/mdstat
Personalities : [linear] [raid0] [raid1] [raid10] [raid6] [raid5] [raid4] 
md2 : active raid5 sda3[0] sde3[4] sdc3[2] sdb3[6](E)
      11701777664 blocks super 1.2 level 5, 64k chunk, algorithm 2 [5/4] [UEU_U]
      
md1 : active raid1 sde2[4] sdd2[3] sdc2[2] sdb2[1] sda2[0]
      2097088 blocks [5/5] [UUUUU]
      
md0 : active raid1 sda1[0] sdc1[2] sde1[4]
      2490176 blocks [5/3] [U_U_U]
      
unused devices: <none>
**admin@JAGNAS001**:**~**$ 

[COLOR=#000000]
[/COLOR][COLOR=#000000][/COLOR][COLOR=#000000]unused devices: <none>[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]**admin@JAGNAS001**:**~**$ ls -al /dev | grep sd[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]crw-------  1 root   root    2,  61 Sep 16 15:17 pty**sd**[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,   0 Sep 16 15:18 **sd**a[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,   1 Sep 16 15:18 **sd**a1[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,   2 Sep 16 15:18 **sd**a2[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,   3 Sep 16 15:18 **sd**a3[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,  16 Sep 16 15:18 **sd**b[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,  17 Sep 16 15:18 **sd**b1[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,  18 Sep 16 15:18 **sd**b2[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,  19 Sep 16 15:18 **sd**b3[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,  32 Sep 16 15:18 **sd**c[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,  33 Sep 16 15:18 **sd**c1[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,  34 Sep 16 15:18 **sd**c2[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,  35 Sep 16 15:18 **sd**c3[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,  48 Sep 16 15:18 **sd**d[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,  49 Sep 16 15:18 **sd**d1[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,  50 Sep 16 15:18 **sd**d2[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,  51 Sep 16 15:18 **sd**d3[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,  64 Sep 16 15:18 **sd**e[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,  65 Sep 16 15:18 **sd**e1[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,  66 Sep 16 15:18 **sd**e2[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]brw-------  1 root   root    8,  67 Sep 16 15:18 **sd**e3[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]crw-------  1 root   root    3,  61 Sep 16 15:17 tty**sd**[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]**admin@JAGNAS001**:**~**$ sudo mdadm --examine /dev/sda1[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]Password: [/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]/dev/sda1:[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]          Magic : a92b4efc[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]        Version : 0.90.00[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]           UUID : 230a753a:a709e178:3017a5a8:c86610be[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]  Creation Time : Fri Dec 31 19:00:07 1999[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Raid Level : raid1[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]  Used Dev Size : 2490176 (2.37 GiB 2.55 GB)[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Array Size : 2490176 (2.37 GiB 2.55 GB)[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Raid Devices : 5[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]  Total Devices : 4[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]Preferred Minor : 0[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]    Update Time : Mon Sep 16 15:35:12 2019[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]          State : clean[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000] Active Devices : 4[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]Working Devices : 4[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000] Failed Devices : 1[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]  Spare Devices : 0[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]       Checksum : 2dd95c6 - correct[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]         Events : 8816841[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]      Number   Major   Minor   RaidDevice State[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]this     0       8        1        0      active sync   /dev/sda1[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   0     0       8        1        0      active sync   /dev/sda1[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   1     1       8       49        1      active sync   /dev/sdd1[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   2     2       8       33        2      active sync   /dev/sdc1[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   3     3       0        0        3      faulty removed[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   4     4       8       65        4      active sync   /dev/sde1[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]**admin@JAGNAS001**:**~**$[/COLOR]
[COLOR=#000000]

[/COLOR][COLOR=#000000][/COLOR][COLOR=#000000]**admin@JAGNAS001**:**~**$ sudo mdadm --examine /dev/sd[a,b,c,d,e]3[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]/dev/sda3:[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]          Magic : a92b4efc[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]        Version : 1.2[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]    Feature Map : 0x0[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Array UUID : c88e0a98:99d03307:6762f5cb:f8c11a08[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]           Name : NAS001:2[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]  Creation Time : Thu Jan  8 20:48:15 2015[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Raid Level : raid5[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Raid Devices : 5[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000] Avail Dev Size : 5850889120 (2789.92 GiB 2995.66 GB)[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Array Size : 11701777664 (11159.68 GiB 11982.62 GB)[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]  Used Dev Size : 5850888832 (2789.92 GiB 2995.66 GB)[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]    Data Offset : 2048 sectors[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Super Offset : 8 sectors[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Unused Space : before=1968 sectors, after=288 sectors[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]          State : clean[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]    Device UUID : 9f72288a:c59c541a:87c3b3cf:eaefffe6[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]    Update Time : Mon Sep 16 15:55:17 2019[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]       Checksum : b7e76fef - correct[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]         Events : 33219[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]         Layout : left-symmetric[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Chunk Size : 64K[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Device Role : Active device 0[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Array State : AAA.A ('A' == active, '.' == missing, 'R' == replacing)[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]/dev/sdb3:[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]          Magic : a92b4efc[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]        Version : 1.2[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]    Feature Map : 0x0[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Array UUID : c88e0a98:99d03307:6762f5cb:f8c11a08[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]           Name : NAS001:2[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]  Creation Time : Thu Jan  8 20:48:15 2015[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Raid Level : raid5[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Raid Devices : 5[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000] Avail Dev Size : 5850889120 (2789.92 GiB 2995.66 GB)[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Array Size : 11701777664 (11159.68 GiB 11982.62 GB)[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]  Used Dev Size : 5850888832 (2789.92 GiB 2995.66 GB)[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]    Data Offset : 2048 sectors[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Super Offset : 8 sectors[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Unused Space : before=1968 sectors, after=288 sectors[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]          State : clean[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]    Device UUID : ae0fc38b:fdea028b:40dd7a9e:7a7bc987[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]    Update Time : Mon Sep 16 15:55:17 2019[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]       Checksum : 99c103d5 - correct[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]         Events : 33219[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]         Layout : left-symmetric[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Chunk Size : 64K[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Device Role : Active device 1[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Array State : AAA.A ('A' == active, '.' == missing, 'R' == replacing)[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]/dev/sdc3:[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]          Magic : a92b4efc[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]        Version : 1.2[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]    Feature Map : 0x0[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Array UUID : c88e0a98:99d03307:6762f5cb:f8c11a08[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]           Name : NAS001:2[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]  Creation Time : Thu Jan  8 20:48:15 2015[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Raid Level : raid5[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Raid Devices : 5[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000] Avail Dev Size : 5850889120 (2789.92 GiB 2995.66 GB)[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Array Size : 11701777664 (11159.68 GiB 11982.62 GB)[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]  Used Dev Size : 5850888832 (2789.92 GiB 2995.66 GB)[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]    Data Offset : 2048 sectors[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Super Offset : 8 sectors[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Unused Space : before=1968 sectors, after=288 sectors[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]          State : clean[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]    Device UUID : 6c0db7ef:0eed53d8:6e23ce05:eb8ba02a[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]    Update Time : Mon Sep 16 15:55:17 2019[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]       Checksum : 553056ef - correct[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]         Events : 33219[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]         Layout : left-symmetric[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Chunk Size : 64K[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Device Role : Active device 2[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Array State : AAA.A ('A' == active, '.' == missing, 'R' == replacing)[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]/dev/sde3:[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]          Magic : a92b4efc[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]        Version : 1.2[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]    Feature Map : 0x0[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Array UUID : c88e0a98:99d03307:6762f5cb:f8c11a08[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]           Name : NAS001:2[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]  Creation Time : Thu Jan  8 20:48:15 2015[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Raid Level : raid5[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Raid Devices : 5[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000] Avail Dev Size : 5850889120 (2789.92 GiB 2995.66 GB)[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Array Size : 11701777664 (11159.68 GiB 11982.62 GB)[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]  Used Dev Size : 5850888832 (2789.92 GiB 2995.66 GB)[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]    Data Offset : 2048 sectors[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Super Offset : 8 sectors[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Unused Space : before=1968 sectors, after=288 sectors[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]          State : clean[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]    Device UUID : e612e7cb:074c0986:acefe40e:64357751[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]    Update Time : Mon Sep 16 15:55:17 2019[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]       Checksum : f03311b - correct[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]         Events : 33219[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]         Layout : left-symmetric[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]     Chunk Size : 64K[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]
[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Device Role : Active device 4[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000]   Array State : AAA.A ('A' == active, '.' == missing, 'R' == replacing)





[/COLOR]
**admin@JAGNAS001**:**~**$ mdadm --detail /dev/md0
mdadm: must be super-user to perform this action
**admin@JAGNAS001**:**~**$ sudo su
Password: 
ash-4.3# 
ash-4.3# 
ash-4.3# mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Fri Dec 31 19:00:07 1999
     Raid Level : raid1
     Array Size : 2490176 (2.37 GiB 2.55 GB)
  Used Dev Size : 2490176 (2.37 GiB 2.55 GB)
   Raid Devices : 5
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent


    Update Time : Mon Sep 16 17:08:00 2019
          State : clean, degraded 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0


           UUID : 230a753a:a709e178:3017a5a8:c86610be
         Events : 0.8820225


    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       -       0        0        1      removed
       2       8       33        2      active sync   /dev/sdc1
       -       0        0        3      removed
       4       8       65        4      active sync   /dev/sde1
ash-4.3# mdadm --detail /dev/md1
/dev/md1:
        Version : 0.90
  Creation Time : Mon Sep 16 17:00:55 2019
     Raid Level : raid1
     Array Size : 2097088 (2047.94 MiB 2147.42 MB)
  Used Dev Size : 2097088 (2047.94 MiB 2147.42 MB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 1
    Persistence : Superblock is persistent


    Update Time : Mon Sep 16 17:02:14 2019
          State : active 
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0


           UUID : 8d264f49:b58795d8:5e6e66ba:be97946a (local to host JAGNAS001)
         Events : 0.20


    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2
       2       8       34        2      active sync   /dev/sdc2
       3       8       50        3      active sync   /dev/sdd2
       4       8       66        4      active sync   /dev/sde2
ash-4.3# mdadm --detail /dev/md2
/dev/md2:
        Version : 1.2
  Creation Time : Thu Jan  8 20:48:15 2015
     Raid Level : raid5
     Array Size : 11701777664 (11159.68 GiB 11982.62 GB)
  Used Dev Size : 2925444416 (2789.92 GiB 2995.66 GB)
   Raid Devices : 5
  Total Devices : 4
    Persistence : Superblock is persistent


    Update Time : Mon Sep 16 17:03:05 2019
          State : clean, FAILED 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 64K


           Name : NAS001:2
           UUID : c88e0a98:99d03307:6762f5cb:f8c11a08
         Events : 33272


    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       6       8       19        1      faulty active sync   /dev/sdb3
       2       8       35        2      active sync   /dev/sdc3
       -       0        0        3      removed
       4       8       67        4      active sync   /dev/sde3
ash-4.3# mdadm --detail /dev/md3
mdadm: cannot open /dev/md3: No such file or directory
ash-4.3#

---

### Post by jgaitan85 on 2019-09-16
also 

ash-4.3# blkid
/dev/sda1: UUID="230a753a-a709-e178-3017-a5a8c86610be" TYPE="linux_raid_member" PARTUUID="a83226e2-6992-4b2f-871e-873f9c50587e"
/dev/sda2: UUID="8d264f49-b587-95d8-5e6e-66babe97946a" TYPE="linux_raid_member" PARTUUID="f8f0352c-24f9-4408-9982-4e25ce6b32bf"
/dev/sda3: UUID="c88e0a98-99d0-3307-6762-f5cbf8c11a08" UUID_SUB="9f72288a-c59c-541a-87c3-b3cfeaefffe6" LABEL="NAS001:2" TYPE="linux_raid_member" PARTUUID="310ddd9f-6d2c-4e95-b35a-73dfa2d40c22"
/dev/sdb1: UUID="230a753a-a709-e178-3017-a5a8c86610be" TYPE="linux_raid_member" PARTUUID="03d7a135-90c7-4bb0-86a6-c037573716f9"
/dev/sdb2: UUID="8d264f49-b587-95d8-5e6e-66babe97946a" TYPE="linux_raid_member" PARTUUID="449fd326-9517-4f4b-b17f-854a24404caa"
/dev/sdb3: UUID="c88e0a98-99d0-3307-6762-f5cbf8c11a08" UUID_SUB="ae0fc38b-fdea-028b-40dd-7a9e7a7bc987" LABEL="NAS001:2" TYPE="linux_raid_member" PARTUUID="d4c662fd-9ad0-4191-9875-884988de0403"
/dev/sdc1: UUID="230a753a-a709-e178-3017-a5a8c86610be" TYPE="linux_raid_member" PARTUUID="47a0ac82-5660-4325-9c7a-1234d7db3afd"
/dev/sdc2: UUID="8d264f49-b587-95d8-5e6e-66babe97946a" TYPE="linux_raid_member" PARTUUID="4bb8a14b-815f-4df9-ba65-d77b9ca0e300"
/dev/sdc3: UUID="c88e0a98-99d0-3307-6762-f5cbf8c11a08" UUID_SUB="6c0db7ef-0eed-53d8-6e23-ce05eb8ba02a" LABEL="NAS001:2" TYPE="linux_raid_member" PARTUUID="92117b7e-7173-482f-938d-bc4f5e90e54e"
/dev/sdd1: UUID="230a753a-a709-e178-3017-a5a8c86610be" TYPE="linux_raid_member" PARTUUID="d50f3407-76f7-424d-b90e-4b743fb44976"
/dev/sdd2: UUID="8d264f49-b587-95d8-5e6e-66babe97946a" TYPE="linux_raid_member" PARTUUID="893dce8e-b272-4e37-b520-0a703c8551c7"
/dev/sde1: UUID="230a753a-a709-e178-3017-a5a8c86610be" TYPE="linux_raid_member" PARTUUID="5e5bda60-f000-4a4c-b7a2-d72c11400275"
/dev/sde2: UUID="8d264f49-b587-95d8-5e6e-66babe97946a" TYPE="linux_raid_member" PARTUUID="9359d854-0fc7-4f5a-8c13-39fe3d31498f"
/dev/sde3: UUID="c88e0a98-99d0-3307-6762-f5cbf8c11a08" UUID_SUB="e612e7cb-074c-0986-acef-e40e64357751" LABEL="NAS001:2" TYPE="linux_raid_member" PARTUUID="5336edd1-e1b5-4cf9-8ef1-288192cd3445"
/dev/md0: LABEL="1.41.10-2668" UUID="d9214519-963d-4632-9b07-6cb26810924c" TYPE="ext4"
/dev/md1: UUID="670196c6-ad2c-4735-9720-287037a40550" TYPE="swap"
/dev/md2: LABEL="1.42.6-5021" UUID="81d9e324-1832-4c25-9923-8c9b28613028" TYPE="ext4"
/dev/synoboot1: UUID="17aea0db-d289-447a-a478-8981b4dad132" TYPE="ext2" PARTUUID="7cf1d34e-01"
/dev/synoboot2: UUID="4259ac6e-7788-4a93-847c-afdd5e4c8eca" TYPE="ext2" PARTUUID="7cf1d34e-02"
ash-4.3#

---

### Post by darkod on 2019-09-17
OK, few things I see.

1. There is no sdd3 partition. Not a problem right now, you can assemble raid5 with one member missing. Can deal with that later.
2. The output of --examine on the third partition on each drive is optimistic. All 4 existing members (again, sdd3 does not exist) seem to show 33219 events, identical number.

With the above you can first try to assemble md2. If one of the 4 drives is faulty you might run into issues, that's your biggest problem right now.

From cat /proc/mdstat it seems md2 is assembled, but not in a good way. So first stop it and then try to assemble it again:
```
sudo mdadm --stop /dev/md2
sudo mdadm --assemble --verbose --force /dev/md2 /dev/sda3 /dev/sdb3 /dev/sdc3 /dev/sde3
```

Post the output so we can see what it shows. And please use CODE tags, command output is much easier to read.

---


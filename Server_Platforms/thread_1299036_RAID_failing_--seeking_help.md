---
title: "RAID failing --seeking help"
date: 2009-10-23
forum: Server Platforms
---

### Post by anupindi007 on 2009-10-23
[COLOR=Blue]Hi,
[COLOR=#000099]I was  configured RAID 5 using mdadm utility and [/COLOR][COLOR=#000099]as matter of fact it was working perfectly for quite some time.  [/COLOR][COLOR=#000099]

I am using 6 hard disks of 1TB each for RAID-5 , in that two [/COLOR][COLOR=#000099] on board hard disks[/COLOR][COLOR=#000099]  and external 4 hard disks using San Digital RAID TR4M/TR4M.  [/COLOR][/COLOR]

[COLOR=Blue]RAID is failed and logs says that mdam not able to activate RAID using two hard disk.  Details as follows and seeking your help to  recover the RAID.  

Thanks in advance,
Srinivas
[/COLOR]


**RAID devices as follows**
1. /dev/sda1 931.51GiB
2. /dev/sdb1 931.51GiB
3. /dev/sdd1 931.51GiB
4. /dev/sde1 931.51GiB
5. /dev/sdf1  931.51GiB
6. /dev/sdg1 931.51GiB
 
[B]
[COLOR=#000099]OS installed[/COLOR][/B] **[COLOR=#000099]on[/COLOR]**
/dev/sdc 149.05GiB
             /dev/sdc1 boot        143.62GB
             /dev/sdc2 extended    5.42.62GB
             /dev/sdc5 linux-swap  5.42.62GB

**[COLOR=#000099]# mdadm -V[/COLOR]**
mdadm - v2.6.7 - 6th June 2008

**# cat /etc/mdadm/mdadm.conf**
DEVICE partitions
ARRAY /dev/md0 level=raid5 num-devices=6 metadata=0.90 spares=1 UUID=7395e18d:4088dc27:bd9f1658:0a1d2015
[B]
# mdadm -D /dev/md0
[/B][COLOR=#000000]mdadm: md device /dev/md0 does not appear to be active.[/COLOR][B]
 
# mdadm -As /dev/md0
[/B][COLOR=#000000]mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.[/COLOR][B]


# cat /proc/mdstat[/B]
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
 md0 : inactive sdb1[4](S) sda1[5](S) sdd1[3](S) sdg1[2](S) sdf1[1](S) sde1[0](S)
      5860559616 blocks

unused devices: <none>

**[COLOR=#000099]# fdisk -l[/COLOR]** (shows all devices detected and raid tower all lights shows green too.)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003446c                     

   Device Boot      Start         End      Blocks   Id  System
 /dev/sda1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007e863                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect
 
Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3e3d3e3                     

   Device Boot      Start         End      Blocks   Id  System
 /dev/sdc1   *           1       18749   150601311   83  Linux 
/dev/sdc2           18750       19457     5687010    5  Extended
/dev/sdc5           18750       19457     5686978+  82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
 255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bb77c                     

   Device Boot      Start         End      Blocks   Id  System
  /dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d04e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001   fd  Linux raid autodetect
 
Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dc07c

   Device Boot      Start         End      Blocks   Id  System
  /dev/sdf1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
 255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ce5ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      121601   976760001   fd  Linux raid autodetect
 


[COLOR=#000099]# /var/log/syslog  and /var/log/kern.log also shows[/COLOR]
784 Oct 21 11:05:27 dcerouter kernel: [ 1871.858674] md: md0 stopped.
785 Oct 21 11:05:27 dcerouter kernel: [ 1871.858705] md: unbind<sdb1>
 786 Oct 21 11:05:27 dcerouter kernel: [ 1871.859507] md: export_rdev(sdb1)
787 Oct 21 11:05:27 dcerouter kernel: [ 1871.859618] md: unbind<sda1>
788 Oct 21 11:05:27 dcerouter kernel: [ 1871.860253] md: export_rdev(sda1)
 789 Oct 21 11:05:27 dcerouter kernel: [ 1871.860361] md: unbind<sdd1>
790 Oct 21 11:05:27 dcerouter kernel: [ 1871.861059] md: export_rdev(sdd1)
791 Oct 21 11:05:27 dcerouter kernel: [ 1871.861153] md: unbind<sdg1>
 792 Oct 21 11:05:27 dcerouter kernel: [ 1871.861785] md: export_rdev(sdg1)
793 Oct 21 11:05:27 dcerouter kernel: [ 1871.861880] md: unbind<sdf1>
794 Oct 21 11:05:27 dcerouter kernel: [ 1871.862508] md: export_rdev(sdf1)
 795 Oct 21 11:05:27 dcerouter kernel: [ 1871.862599] md: unbind<sde1>
796 Oct 21 11:05:27 dcerouter kernel: [ 1871.863230] md: export_rdev(sde1)
797 Oct 21 11:05:27 dcerouter kernel: [ 1871.932655] md: bind<sde1>
 798 Oct 21 11:05:27 dcerouter kernel: [ 1871.933248] md: bind<sdf1>
799 Oct 21 11:05:27 dcerouter kernel: [ 1871.933737] md: bind<sdg1>
800 Oct 21 11:05:27 dcerouter kernel: [ 1871.934226] md: bind<sdd1>
 801 Oct 21 11:05:27 dcerouter kernel: [ 1871.934717] md: bind<sda1>
802 Oct 21 11:05:27 dcerouter kernel: [ 1871.935444] md: bind<sdb1>


**[COLOR=#000099]#  mdadm -Q /dev/sda1[/COLOR]**
 /dev/sda1: is not an md array
/dev/sda1: device 5 in 6 device undetected raid5 /dev/md0.  Use mdadm --examine for more detail.

[COLOR=#000099]mdadm -Q /dev/sdb1[/COLOR]
/dev/sdb1: is not an md array
 /dev/sdb1: device 4 in 6 device undetected raid5 /dev/md0.  Use mdadm --examine for more detail.

[COLOR=#000099]mdadm -Q /dev/sdd1[/COLOR]
/dev/sdd1: is not an md array
/dev/sdd1: device 3 in 6 device undetected raid5 /dev/md0.  Use mdadm --examine for more detail.
 
[COLOR=#000099]mdadm -Q /dev/sdg1[/COLOR]
/dev/sdg1: is not an md array
/dev/sdg1: device 2 in 6 device undetected raid5 /dev/md0.  Use mdadm --examine for more detail.


[COLOR=#000099]mdadm -Q /dev/sdf1[/COLOR]
 /dev/sdf1: is not an md array
/dev/sdf1: device 1 in 6 device undetected raid5 /dev/md0.  Use mdadm --examine for more detail.


[COLOR=#000099]mdadm -Q /dev/sde1[/COLOR]
/dev/sde1: is not an md array
 /dev/sde1: device 0 in 6 device undetected raid5 /dev/md0.  Use mdadm --examine for more detail.


[COLOR=#000099]# mdadm --examine /dev/sda1[/COLOR]
/dev/sda1:                                           
           Magic : a92b4efc                           
        Version : 00.90.00                           
           UUID : 7395e18d:4088dc27:bd9f1658:0a1d2015
  Creation Time : Sun Jun  7 11:29:40 2009           
      Raid Level : raid5                              
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
 
    Update Time : Mon Aug 17 08:16:35 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 3
  Spare Devices : 0
       Checksum : f4088e0f - correct
         Events : 650340
 
         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     5       8        1        5      active sync   /dev/sda1

   0     0       0        0        0      [COLOR=Red]**removed**[/COLOR]
    1     1       0        0        1     [COLOR=Red] faulty removed[/COLOR]
   2     2       0        0        2      [COLOR=Red]faulty removed[/COLOR]
   3     3       0        0        3      [COLOR=Red]faulty removed[/COLOR]
   4     4       8       17        4      active sync   /dev/sdb1
    5     5       8        1        5      active sync   /dev/sda1


[COLOR=#000099]# mdadm --examine /dev/sdb1[/COLOR]
/dev/sdb1:                                           
          Magic : a92b4efc                           
         Version : 00.90.00                           
           UUID : 7395e18d:4088dc27:bd9f1658:0a1d2015
  Creation Time : Sun Jun  7 11:29:40 2009           
     Raid Level : raid5                              
   Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Mon Aug 17 08:16:35 2009
           State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 3
  Spare Devices : 0
       Checksum : f4088e1d - correct
         Events : 650340

         Layout : left-symmetric
      Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       17        4      active sync   /dev/sdb1

   0     0       0        0        0      **[COLOR=Red]removed[/COLOR]**
   1     1       0        0        1      [COLOR=Red]faulty removed[/COLOR]
    2     2       0        0        2      [COLOR=Red]faulty removed[/COLOR]
   3     3       0        0        3      [COLOR=Red]faulty removed[/COLOR]
   4     4       8       17        4      active sync   /dev/sdb1
   5     5       8        1        5      active sync   /dev/sda1
 


[COLOR=#000099]# mdadm --examine /dev/sdd1           [/COLOR]
/dev/sdd1:                                                      
          Magic : a92b4efc                                      
         Version : 00.90.00                                      
           UUID : 7395e18d:4088dc27:bd9f1658:0a1d2015           
  Creation Time : Sun Jun  7 11:29:40 2009                      
     Raid Level : raid5                                         
   Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Mon Aug 17 08:15:41 2009
           State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f4088db3 - correct
         Events : 650334

         Layout : left-symmetric
      Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1

   0     0       8       65        0      active sync   /dev/sde1
    1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       97        2      active sync   /dev/sdg1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       17        4      active sync   /dev/sdb1
    5     5       8        1        5      active sync   /dev/sda1

[COLOR=#000099]# mdadm --examine /dev/sde1    [/COLOR]      
/dev/sde1:                                                     
           Magic : a92b4efc                                     
        Version : 00.90.00                                     
           UUID : 7395e18d:4088dc27:bd9f1658:0a1d2015          
  Creation Time : Sun Jun  7 11:29:40 2009                     
      Raid Level : raid5                                        
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
   Raid Devices : 6
  Total Devices : 6
 Preferred Minor : 0

    Update Time : Mon Aug 17 08:15:41 2009
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f4088dbd - correct
          Events : 650334

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       65        0      active sync   /dev/sde1

    0     0       8       65        0      active sync   /dev/sde1
   1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       97        2      active sync   /dev/sdg1
   3     3       8       49        3      active sync   /dev/sdd1
    4     4       8       17        4      active sync   /dev/sdb1
   5     5       8        1        5      active sync   /dev/sda1

[COLOR=#000099]mdadm --examine /dev/sdf1      [/COLOR]     
 /dev/sdf1:                                                      
          Magic : a92b4efc                                      
        Version : 00.90.00                                      
           UUID : 7395e18d:4088dc27:bd9f1658:0a1d2015           
   Creation Time : Sun Jun  7 11:29:40 2009                      
     Raid Level : raid5                                         
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
    Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Mon Aug 17 08:15:41 2009
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0
        Checksum : f4088dcf - correct
         Events : 650334

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       81        1      active sync   /dev/sdf1
 
   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       97        2      active sync   /dev/sdg1
   3     3       8       49        3      active sync   /dev/sdd1
    4     4       8       17        4      active sync   /dev/sdb1
   5     5       8        1        5      active sync   /dev/sda1

[COLOR=#3333ff]# mdadm --examine /dev/sdg1 [/COLOR]          
 /dev/sdg1:                                                      
          Magic : a92b4efc                                      
        Version : 00.90.00                                      
           UUID : 7395e18d:4088dc27:bd9f1658:0a1d2015           
   Creation Time : Sun Jun  7 11:29:40 2009                      
     Raid Level : raid5                                         
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
    Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Mon Aug 17 08:15:41 2009
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0
        Checksum : f4088de1 - correct
         Events : 650334

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       97        2      active sync   /dev/sdg1
 
   0     0       8       65        0      active sync   /dev/sde1
   1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       97        2      active sync   /dev/sdg1
   3     3       8       49        3      active sync   /dev/sdd1
    4     4       8       17        4      active sync   /dev/sdb1
   5     5       8        1        5      active sync   /dev/sda1


 [COLOR=#888888]
[/COLOR]

---

### Post by anupindi007 on 2009-10-26
Seeking help...

---

### Post by fjgaude on 2009-10-27
I've not run into a situation like you have... I guess I'd try a few commands to see if the whole array can be assembled. I'd rename the /etc/mdadm/mdadm.conf  file, then:

```
sudo mdadm --assemble --scan
```

A new mdadm.conf file will be auto created. Then if that didn't permit the array to come up I'd compare the UUID in the --examine commands you have shown with those in the two mdadm.conf files we have.

If they all match I'd force an assemble:

```
sudo mdadm --assemble --force /dev/md0
```

Let us know how things go, please.

---

### Post by anupindi007 on 2009-10-27
Thanks for your info,  I will check and get back with info.

---

### Post by anupindi007 on 2009-10-29
[COLOR=DarkSlateGray]**sorry for the delay in replying mesg but no luck.**.[/COLOR]

//renamed
[COLOR=DarkRed]#cd /etc/mdadm
[/COLOR] [COLOR=DarkRed]#mv mdadm.conf mdadm.conf1[/COLOR]


[COLOR=DarkRed]# mdadm --assemble --scan[/COLOR]
   [COLOR=Blue]mdadm: No arrays found in config file[/COLOR]

//recopied back to 
[COLOR=DarkRed]# mv mdadm.conf1 mdadm.conf
[/COLOR] [COLOR=DarkRed]# mdadm --assemble --scan[/COLOR]
[COLOR=Blue]    mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.[/COLOR]

---

### Post by fjgaude on 2009-10-29
How do the UUID compare in the -E command and in the mdadm.conf file?

---

### Post by joeinbend on 2009-11-02
I agree with Fj, you need to do a --force assembly. But first:

Let's see your mdadm.conf: Give us the output of "cat /etc/mdadm/mdadm.conf"

Let's see output of "sudo mdadm --detail /dev/md0"

Let's see output of "cat /proc/partitions"

---

### Post by anupindi007 on 2009-11-30
> **joeinbend said:**
> I agree with Fj, you need to do a --force assembly. But first:

Let's see your mdadm.conf: Give us the output of "cat /etc/mdadm/mdadm.conf"

Let's see output of "sudo mdadm --detail /dev/md0"

Let's see output of "cat /proc/partitions"


Sorry Guys, i was away from my system for quite some time and please find my updates:

mdadm force assemble says cannot start with 2 hard disk( which is attached to Mother board).  For RAID-5 we need minimum 3 hard disks.  But I have 4 Hard disk with [COLOR=Blue][COLOR=#000099]SanDigitalRAID[/COLOR][/COLOR]Unit, mdadm not able to use it.


I have replaced  [COLOR=Blue][COLOR=#000099]SanDigitalRAID[/COLOR][/COLOR]Unit and there after also I have same issue.  I took one of the RAID hard disk from [COLOR=Blue][COLOR=#000099]SanDigitalRAID[/COLOR][/COLOR]Unit, connected to motherboard to SATA interface and RAID was up(immediately shutdown the system because i want all hard disks to be on RAID) .

Ubuntu detected all hard disks of [COLOR=Blue][COLOR=#000099]SanDigitalRAID[/COLOR][/COLOR]Unit and but not madam able to use it.  So where should i look the problem.

Note: 
1. [COLOR=Blue][COLOR=#000099]San Digital RAID TR4M/TR4M contains 4 RAID hard disks and 2 hard disk attached to mother board all are SATA interface.

Thanks
[/COLOR][/COLOR]

---

### Post by joeinbend on 2009-11-30
I think that last post may have thrown a curveball to all of us -- is "SanDigitalRAIDUnit" a hardware RAID controller, or is that just the brand/model name of your SATA controller? If your RAID is being handled by a hardware solution, mdadm will not work properly, since it will not see the block-level hard disks, but rather the RAID built by your hardware card. Give us some more details on that.

Also, You indicate you have 4 hard disks total attached to your server, but from the sounds of it mdadm is only seeing 2 of them. Do a "cat /proc/partitions" and let's see what devices Ubuntu is actually seeing.

I may be getting ahead of myself here, but my suspicion is that Ubuntu is only seeing the two drives directly attached to your motherboard, and that your "San Digital RAID TR4M" is trying to / has already built a hardware RAID array.

---

### Post by anupindi007 on 2009-11-30
> **joeinbend said:**
> I think that last post may have thrown a curveball to all of us -- is "SanDigitalRAIDUnit" a hardware RAID controller, or is that just the brand/model name of your SATA controller? If your RAID is being handled by a hardware solution, mdadm will not work properly, since it will not see the block-level hard disks, but rather the RAID built by your hardware card. Give us some more details on that.

Also, You indicate you have 4 hard disks total attached to your server, but from the sounds of it mdadm is only seeing 2 of them. Do a "cat /proc/partitions" and let's see what devices Ubuntu is actually seeing.

I may be getting ahead of myself here, but my suspicion is that Ubuntu is only seeing the two drives directly attached to your motherboard, and that your "San Digital RAID TR4M" is trying to / has already built a hardware RAID array.


[COLOR=Blue]Thanks for your prompt reply.[/COLOR]

[COLOR=Blue]San Digital TR4M is a RAID tower connected to linux system with eSATA(Port Multiplier card) port.  This model supports 4 SATA Hard disks.[/COLOR]  [http://www.sansdigital.com/towerraid/tr4m.html](http://www.sansdigital.com/towerraid/tr4m.html)

[COLOR=Blue]I have Two RAID hard disks on board and additional 4 hard disks got from SansDigitialRAID port multiplier unit(because i am not using their RAID utility and in fact they don't have their RAID utility on linux).[/COLOR]  [COLOR=Blue]For mdadm configuration i got 6 RAID formatted disks and RAID configured using mdadm  only.

[/COLOR][COLOR=Blue]Around 3 months with 6 hard disks RAID-5 worked fine and not sure why mdadm RAID failed now.[/COLOR]

[COLOR=Blue]I dont have details of "cat /proc/partitions" time being and i will provide you the details asap.[/COLOR]

---

### Post by joeinbend on 2009-12-03
Let us know when you can display your "cat /proc/partitions" table. I just want to be sure that Ubuntu is "seeing" the /dev/sd* devices in your drive enclosure individually, and block-level. It appears from your original post...

RAID devices as follows
1. /dev/sda1 931.51GiB
2. /dev/sdb1 931.51GiB
3. /dev/sdd1 931.51GiB
4. /dev/sde1 931.51GiB
5. /dev/sdf1 931.51GiB
6. /dev/sdg1 931.51GiB

... that it is in fact seeing them as we would expect, I just want to be sure that has not changed.

I re-read the whole post here, and it appears the one recommended step that has not been performed is a --force assembly of your array. Issue the following command:

sudo mdadm --assemble --force /dev/md0

---

### Post by anupindi007 on 2009-12-09
> **joeinbend said:**
> Let us know when you can display your "cat /proc/partitions" table. I just want to be sure that Ubuntu is "seeing" the /dev/sd* devices in your drive enclosure individually, and block-level. It appears from your original post...

RAID devices as follows
1. /dev/sda1 931.51GiB
2. /dev/sdb1 931.51GiB
3. /dev/sdd1 931.51GiB
4. /dev/sde1 931.51GiB
5. /dev/sdf1 931.51GiB
6. /dev/sdg1 931.51GiB

... that it is in fact seeing them as we would expect, I just want to be sure that has not changed.

I re-read the whole post here, and it appears the one recommended step that has not been performed is a --force assembly of your array. Issue the following command:

sudo mdadm --assemble --force /dev/md0
sorry, i was not in town for couple of days, hence couldn't reply.

# cat /proc/partitions says:
major minor  #blocks  name

   8     0  156290904 sda
   8     1  150601311 sda1
   8     2          1 sda2
   8     5    5686978 sda5
   8    16  976762584 sdb
   8    17  976760001 sdb1
   8    32  976762584 sdc
   8    33  976760001 sdc1
   8    48  976762584 sdd
   8    49  976760001 sdd1
   8    64  976762584 sde
   8    65  976760001 sde1
   8    80  976762584 sdf
   8    81  976760001 sdf1
   8    96  976762584 sdg
   8    97  976760001 sdg1


Number of changes happened on system front like
We got another raid tower and added to system.  On board two raid hard disks moved to the raid tower so that we can have all raid disks on sandigital tower. Unfortunately the problem remains same.

//created raid once again
#mdadm --stop /dev/md0
#mdadm --create /dev/md0 --level=5 --raid-devices=6 /dev/sd[b-g]1
#mdadm --assemble --scan /dev/md0
#cat /proc/mdadmstat  //shows raid is assembled properly and raid is active 
//but not able to see any raid mount data in /var/media directory.

//trying to mount md0 but not able to do so
# mount -t ext3 /dev/md0 /var/media

// in the mean time mistakenly executed command from history and wiped out entire data, 
mkfs -t ext3 /dev/md0

//sorry guys i am very upset about the same and sorry for disappointing you too on this.
Thanks supporting till know on this and trying to rebuild the system from scratch.

---

### Post by joeinbend on 2009-12-09
Sorry to hear about your data loss. It looks from your post that the point of no return was running the --create command. That would have built a new RAID with the disks you specify, rather than attempting to reassemble the offline RAID. The final nail in the coffin was writing a filesystem to that newly created RAID.

---

### Post by laluz on 2009-12-18
Check this thread of mine. It may help you. [http://ubuntuforums.org/showthread.php?t=1281922](http://ubuntuforums.org/showthread.php?t=1281922)

---


---
title: "[Solved] Mdadm problem, need advice on sleeping the assemble or not running at boot?"
date: 2013-06-14
forum: Server Platforms
---

### Post by mcordell on 2013-06-14
Hello All,

I'm having a problem with my mdadm setup. I have a raid-6 running and it currently has 6 drives. My Mobo has 6 sata ports, one of which is used up for the boot drive (not involved in the array). The sixth array drive is on a PCI sata/raid card. I have a recurrent problem where my raid will drop one of the disks at boot. It will still assemble (dirty) because I had that configured when I used dpkg-reconfigure mdadm. The server is headless, so dropping into busybox wasn't an option for me.  I can re-add the missing drive, but this causes a rebuild because the other 5 drives are in one state (5-1) and the lone drive is in another state (6 clean). 

Shown here:

mdadm -D /dev/md0
```

        Version : 1.2
  Creation Time : Mon Jan  9 13:41:49 2012
     Raid Level : raid6
     Array Size : 7814049280 (7452.06 GiB 8001.59 GB)
  Used Dev Size : 1953512320 (1863.01 GiB 2000.40 GB)
   Raid Devices : 6
  Total Devices : 5
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Fri Jun 14 00:34:45 2013
          State : active, degraded
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 128K


           Name : GlaDoS:0  (local to host GlaDoS)
           UUID : d7b5c7fc:144c0df7:09692912:dc1973a0
         Events : 2276403


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       4       8       65        3      active sync   /dev/sde1
       6       8       81        4      active sync   /dev/sdf1


```

Inspect the lone drive:
mdadm --examine /dev/sdh1
```

/dev/sdh1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : d7b5c7fc:144c0df7:09692912:dc1973a0
           Name : GlaDoS:0  (local to host GlaDoS)
  Creation Time : Mon Jan  9 13:41:49 2012
     Raid Level : raid6
   Raid Devices : 6


 Avail Dev Size : 3907025072 (1863.01 GiB 2000.40 GB)
     Array Size : 15628098560 (7452.06 GiB 8001.59 GB)
  Used Dev Size : 3907024640 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 1e6cb303:e967c291:12302f42:9d605699


Internal Bitmap : 2 sectors from superblock
    Update Time : Thu Jun 13 23:26:03 2013
       Checksum : 4aa39991 - correct
         Events : 2276365


         Layout : left-symmetric
     Chunk Size : 128K


   Device Role : Active device 5
   Array State : AAAAAA ('A' == active, '.' == missing)


```




[B]My theory is that the sata card drive doesn't come up quick enough for the assemble. dmesg log seems to support this idea because mdadm starts its assemble and then several lines down the log the lone drive is mentioned and recognized.


So, how can I solve this problem?
[/B]
I figure make mdadm wait longer before assembling or just assemble it by hand after boot and I can ssh in. I don't really care which, I just don't want to reassemble after every boot.


_Other things that might be relevant:_

1. this array has grown slowly over time started as a 3 disk RAID 5 and slowly expanded from there. Not sure if that is relevant
2. MDadm version
```

# mdadm -V
mdadm - v3.1.4 - 31st August 2010

```
3. Ubuntu version
```

#uname -a
Linux GlaDoS 3.0.0-32-generic #51-Ubuntu SMP Thu Mar 21 15:50:59 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

# lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric



```

3. cat /proc/mdstat
```

# cat proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdb1[0] sdc1[1] sdd1[2] sdf1[6] sde1[4]
      7814049280 blocks super 1.2 level 6, 128k chunk, algorithm 2 [6/5] [UUUUU_]
      bitmap: 2/15 pages [8KB], 65536KB chunk

```

4. cat /etc/mdadm/mdadm.conf
```

# cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR michaeldcordell@gmail.com


# definitions of existing MD arrays
ARRAY /dev/md0 metadata=1.2 name=GlaDoS:0 UUID=d7b5c7fc:144c0df7:09692912:dc1973a0


# This file was auto-generated on Sat, 07 Jan 2012 13:38:24 -0800
# by mkconf $Id$



```
4. Yes I know the drive letter is sdh and not sdg. sdg is a blank drive not in the array that I was eventually going to use as a hot swap

5. blkid
```

# blkid
/dev/sdc1: UUID="d7b5c7fc-144c-0df7-0969-2912dc1973a0" UUID_SUB="53e76a77-0c6c-8b1b-05f9-e9542bcb07ab" LABEL="GlaDoS:0" TYPE="linux_raid_member"
/dev/sda1: UUID="e95c2ed5-845c-4c67-b8d0-f9cd3be77acd" TYPE="ext4"
/dev/sda5: UUID="712c7d09-1b89-41e2-b936-dfa9653155b8" TYPE="swap"
/dev/sdb1: UUID="d7b5c7fc-144c-0df7-0969-2912dc1973a0" UUID_SUB="692dd59f-ded5-c024-c24f-2ee15db788fd" LABEL="GlaDoS:0" TYPE="linux_raid_member"
/dev/sde1: UUID="d7b5c7fc-144c-0df7-0969-2912dc1973a0" UUID_SUB="0352a0f4-f1d7-4c42-56ce-008f18107002" LABEL="GlaDoS:0" TYPE="linux_raid_member"
/dev/sdf1: UUID="d7b5c7fc-144c-0df7-0969-2912dc1973a0" UUID_SUB="548b8f01-b953-7410-0df4-4252b62e49f4" LABEL="GlaDoS:0" TYPE="linux_raid_member"
/dev/sdd1: UUID="d7b5c7fc-144c-0df7-0969-2912dc1973a0" UUID_SUB="ebbf171f-9d07-46ea-f530-e941669f8ffe" LABEL="GlaDoS:0" TYPE="linux_raid_member"
/dev/md0: LABEL="filestore" UUID="e1889eee-4a69-4a90-b47e-89cc975881a5" TYPE="xfs"
/dev/sdh1: UUID="d7b5c7fc-144c-0df7-0969-2912dc1973a0" UUID_SUB="1e6cb303-e967-c291-1230-2f429d605699" LABEL="GlaDoS:0" TYPE="linux_raid_member"

```

6. I can't stop the array, with the raid filesytem unmounted. Even with:
```

mdadm -S --force /dev/md0

```
I get:
mdadm: failed to stop array /dev/md0: Device or resource busy
Perhaps a running process, mounted filesystem or active volume group?

---

### Post by SaturnusDJ on 2013-06-14
In theory, all you need to do to stop auto assemble, is remove the definitions from /etc/mdadm/mdadm.conf. But...Ubuntu/mdadm is configured in a way that mdadm will always auto assemble.

To prevent this:
Edit /lib/udev/rules.d/64-md-raid.rules.
Comment out the line saying:
```
ACTION=="add", RUN+="/sbin/mdadm --incremental $tempnode"
```

---

### Post by rubylaser on 2013-06-14
> **SaturnusDJ said:**
> In theory, all you need to do to stop auto assemble, is remove the definitions from /etc/mdadm/mdadm.conf. But...Ubuntu/mdadm is configured in a way that mdadm will always auto assemble.

To prevent this:
Edit /lib/udev/rules.d/64-md-raid.rules.
Comment out the line saying:
```
ACTION=="add", RUN+="/sbin/mdadm --incremental $tempnode"
```

+1 this will work.  Then, you could assemble the array later by adding an mdadm --assemble --scan line to /etc/rc.local.  This will run after all other startup processes have completed.

---

### Post by mcordell on 2013-06-14
> **SaturnusDJ said:**
> In theory, all you need to do to stop auto assemble, is remove the definitions from /etc/mdadm/mdadm.conf. But...Ubuntu/mdadm is configured in a way that mdadm will always auto assemble.

To prevent this:
Edit /lib/udev/rules.d/64-md-raid.rules.
Comment out the line saying:
```
ACTION=="add", RUN+="/sbin/mdadm --incremental $tempnode"
```



Thanks to both of you! This indeed works and had the intended effect, a few notes for anyone finding this by google:

1. On my version I didn't have /lib/udev/rules/64-md-raid.rules, I had /lib/udev/rules/85-md-raid.rules (I assume because I was on 11.10). Commenting out the same section worked.
2. I deleted(moved) all of mdadm config files out out of /etc/mdadm/ (don't know if this was necessary)
3. I ran:
```

update-initramfs -u

```
[B]This seemed to be key to the changes being accepted and not having mdadm run on start.
[/B]4. System boots now straight to prompt without falling into busybox hell
5. _Important_: During this little venture I had to drop in a video card and hook up a monitor in order to get through the busybox and such. I decided now was as good a time as any to upgrade to 12.04.2 LTS (been putting it off because I didn't want to do it over SSH). As a known benefit I would get an upgraded mdadm version:
```

# mdadm --version
mdadm - v3.2.5 - 18th May 2012

```


5. I hand assembled the 5 good drives
```

mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1

```

6. Re-added the one dirty/lone drive
```

mdadm /dev/md0 --re-add /dev/sdh1

```
drive is picked up into the array and everything is clean and great.
*If you are getting a complete rebuild you might try upgrading your distro or just mdadm (as I think that the newer version might be better at re-adding, not 100% on this)*. I had the newer mdadm version and I didn't have to completely rebuild.

---


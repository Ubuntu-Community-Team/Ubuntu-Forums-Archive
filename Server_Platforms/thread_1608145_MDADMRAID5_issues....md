---
title: "MDADM/RAID5 issues..."
date: 2010-10-28
forum: Server Platforms
---

### Post by KirkPotlit on 2010-10-28
I've done a fair amount of searching and this issue seems to be pretty common, but I have yet to find a solid answer.  Hoping that there is one...
 
Here's my problem.  I have 6 SATA drives on my machine arranged in this order on the SATA connectors...
1.  250G WD
2.  1TB Samsung
3.  1TB Samsung
4.  1TB Samsung
5.  1TB Hitachi
6.  LG CD/DVD Burner
 
My intention is to boot off the 250G WD drive and setup the 1TB drives in a RAID5 array using MDADM.  In fact, I have this working and it's been operational for a couple weeks now while I've been fiddling with other software on the machine.
 
The problem I'm seeing is, when I reboot the machine, the order of the devices sometimes changes, sometimes not.
 
It seems the WD is sometimes /dev/sda and sometimes /dev/sdb, I honestly have not paid too much attention to the others, but when the above happens, it screws up the RAID5 array.
 
my /etc/mdadm/mdadm.conf looks like:
```
DEVICE  partitions
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR root
ARRAY /dev/md0 level=raid5 num-devices=4 devices=/dev/sda,/dev/sdc,/dev/sdd,/dev/sde

```
Currently, the WD drive is /dev/sdb, last night it was /dev/sda
 
I'm running Ubuntu Server 10.04 AMD x64.
 
I've read solution that talk about using UUID, but that appears to be for /dev/md0, not the individual disks.  Others point to editing some UDEV settings.  Some indicate that's just the way the devices are detected at boot time.
 
Many of the posts are older, circa 2005-2006, and none I've found seem to post a definitive answer.  Is there one?
 
Hopefully I provided enough info, if there's anything else, let me know.  I'm fairly green to Ubuntu and linux in general, but I can struggle along with the best of them...
 
Thanks...

---

### Post by jacekk015 on 2010-10-29
mdadm --detail --scan >> /etc/mdadm/mdadm.conf

Gives you RAID with UUIDs. Remove any other old/unwanted data.

[http://ubuntuforums.org/showthread.php?t=444274](http://ubuntuforums.org/showthread.php?t=444274)
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by KirkPotlit on 2010-10-29
Yeah, I'm pretty sure I looked over those threads and maybe I'm just thick skulled...

It looks like in the first one, he thought he solved the issue by building the array in the mdadm.conf file by using UUID= xxxxx.  But then followed up with, dang, it didn't work.

I'm not seeing anything in the second one...  I think what I'm looking for is something like specifying the following in my fstab:
```
# /dev/sda1

UUID=5e1d155c-2c26-4579-8ae2-39acc139833c     /dev/sda          ext3    defaults,errors=remount-ro     0       1


```but I'm not sure what to use after the /dev/sda as far a filesystem, etc for a RAID member.  OR, even if that assignment is even possible.  It doens't seem like it should work, I thought the fstab was more for mount locations and not device assignment.

Right now, i have the following in my mdadm.conf file:
```
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=a9a1b792:71d0fefd:2161fa22:3af496da
```I have rebboted once, and currently, my WD drive is /dev/sda which means my array shouldn't be working, but it looks like it's OK.  Not sure if future reboots will yield the same result.

mdadm.conf
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
# This file was auto-generated on Fri, 08 Oct 2010 23:35:12 -0400
# by mkconf $Id$
#ARRAY /dev/md0 level=raid5 num-devices=4 devices=/dev/sda,/dev/sdc,/dev/sdd,/dev/sde
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=a9a1b792:71d0fefd:2161fa22:3af496da

```blkid:
```
/dev/sda1: UUID="c191cc77-60d3-4e3f-818b-2c77470d017b" TYPE="ext4" 
/dev/sda5: UUID="64b8a3a5-41ef-4f2d-b092-165e72b66df7" TYPE="swap" 
/dev/sdb: UUID="a9a1b792-71d0-fefd-2161-fa223af496da" TYPE="linux_raid_member" 
/dev/sdc: UUID="a9a1b792-71d0-fefd-2161-fa223af496da" TYPE="linux_raid_member" 
/dev/sdd: UUID="a9a1b792-71d0-fefd-2161-fa223af496da" TYPE="linux_raid_member" 
/dev/md0: UUID="5cf0588f-4613-4336-be3f-45bc48031cd0" TYPE="ext4" 
/dev/sde: UUID="a9a1b792-71d0-fefd-2161-fa223af496da" TYPE="linux_raid_member"

```mdadm --detail /dev/md0
```
/dev/md0:
        Version : 00.90
  Creation Time : Fri Oct  8 23:41:22 2010
     Raid Level : raid5
     Array Size : 2930287104 (2794.54 GiB 3000.61 GB)
  Used Dev Size : 976762368 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Oct 29 18:27:08 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 256K

           UUID : a9a1b792:71d0fefd:2161fa22:3af496da (local to host sun)
         Events : 0.15790

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       64        1      active sync   /dev/sde
       2       8       48        2      active sync   /dev/sdd
       3       8       32        3      active sync   /dev/sdc

```EDIT:  Hmmm...  I'm noticing the UUID for all the raid devices is the same, I guess I assumed they would each have their own, and didn't even notice because I've been down this road so often I never really paid much attention to the obvious...  .  So is this the superblock info that I'm reading about?  

Are we witnessing that AHA! moment that everyone has every so often?

Thanks for the assitance...

If this plays out as I hope it will, I'll be sure to update the status to [SOLVED]...  Maybe by then there will be a "I should have had a V-8" smiley?

---


---
title: "raid 5 with 3TB drives"
date: 2011-06-15
forum: Server Platforms
---

### Post by PeterNSteinmetz on 2011-06-15
I am trying to use 3 3TB Western Digital drives in a raid 5 software array. The trouble seems to be that the array is created with only 1.5 TB of capacity, rather then the expected 6 TB. 

Here are the commands and output:

$ sudo dmraid -f isw -C BackupFull6 --type 5 --disk /dev/sde,/dev/sdf,/dev/sdg --size=5589G


     Create a RAID set with ISW metadata format     

RAID name:      BackupFull6
RAID type:      RAID5
RAID size:      5589G (11720982528 blocks)
RAID strip:     64k (128 blocks)
DISKS:     /dev/sde, /dev/sdf, /dev/sdg, 


About to create a RAID set with the above settings. Continue ? [y/n] :y

$ sudo dmraid -s
*** Group superset isw_cdjhcaegij
--> Subset
name   : isw_cdjhcaegij_BackupFull6
size   : 3131048448
stride : 128
type   : raid5_la
status : ok
subsets: 0
devs   : 3
spares : 0

So I cannot understand why the size of the created array is only 3131048448 or about 1.5 TB.  The first command seemed to imply it was going to create an array with 5589GB.

System is:
Description:    Ubuntu 10.04.2 LTS
Release:        10.04
Codename:       lucid

Am I doing something wrong? Is this a limit of isw somehow? Or if this is a bug, is there a workaround? 

thanks,
Peter

---

### Post by tgalati4 on 2011-06-16
Can't help you with your immediate problem, but be mindful that using RAID5 with large disks (3 TB is pretty big) can leave you vulnerable to complete RAID failure.

Here is the scenario:  One disk fails and your RAID5 is operating in degraded manner while it waits for you to replace the faulty drive.  You replace the drive and it takes 3 days to rebuild the RAID5.  Your data is at risk during this time.  Meanwhile your power supply stutters during this 3-day recovery and your entire RAID is trashed and unrecoverable--data lost.  Incidentally, the original drive failure was also caused by this faulty power supply, but the RAID doesn't know any difference--if it can't read from a drive, then it's marked as bad--such as when the 12VDC rail fails and the disk spins down, but the controller is still trying to read data.

Substitute power supply for RAM or RAID controller.  Any non-disk failures can propagate to RAID warnings, then your dutiful disk maintenance results in RAID collapse because of continued hardware problems.

If you left the size parameter off, does it create a different size RAID5?

---

### Post by ian dobson on 2011-06-16
Hi,

Why are you using dmraid and not mdadm? dmraid is for fake raid thats compatible with windows. mdadm is the native software raid system for linux.

I'd imagine your problem is that the drives are larger than 2Tb and that can cause some programs to miss calculate the number of blocks/size of the drive.

What does fdisk -l /dev/sd(drive letter) show?

Regards
Ian Dobson

---

### Post by YesWeCan on 2011-06-16
Note that as you are on 10.04 mdadm will default to using metadata format v0.90 - which won't work properly with drives larger than 2TB. The lastest mdadm uses format v1.2.

I agree with tgalati4 that RAID 5 is not very safe at all. So do regular backups or use RAID 6 or for the safest use a RAID 1 variant.

---

### Post by psusi on 2011-06-16
> **tgalati4 said:**
> Can't help you with your immediate problem, but be mindful that using RAID5 with large disks (3 TB is pretty big) can leave you vulnerable to complete RAID failure.

Here is the scenario:  One disk fails and your RAID5 is operating in degraded manner while it waits for you to replace the faulty drive.  You replace the drive and it takes 3 days to rebuild the RAID5.  Your data is at risk during this time.  Meanwhile your power supply stutters during this 3-day recovery and your entire RAID is trashed and unrecoverable--data lost.  Incidentally, the original drive failure was also caused by this faulty power supply, but the RAID doesn't know any difference--if it can't read from a drive, then it's marked as bad--such as when the 12VDC rail fails and the disk spins down, but the controller is still trying to read data.

It would take something like 10 hours, not 3 days, and if power is lost during that time, it just resumes when the power comes back on.

Once again, the purpose of raid is to maintain uptime, not protect data; you still need backups.


For the OP: you need to use Linux software raid ( mdadm ) instead of the fakeraid.

---

### Post by ian dobson on 2011-06-16
> **psusi said:**
> It would take something like 10 hours, not 3 days, and if power is lost during that time, it just resumes when the power comes back on.

Once again, the purpose of raid is to maintain uptime, not protect data; you still need backups.


For the OP: you need to use Linux software raid ( mdadm ) instead of the fakeraid.

My 4x2Tb raid 5 array takes about 6-7hours to resync/check so with 4x3tb drives 10hours sounds about right.

And yes raid is not a replacement for good backups.

Regards
Ian Dobson

---

### Post by tgalati4 on 2011-06-17
The 3-day rebuild is when the process is niced so that it doesn't affect database throughput on a production machine during work hours.

---

### Post by PeterNSteinmetz on 2011-06-18
Thanks all for the ideas and comments. Regarding the rebuild issue, this is actually for a set of 3 drives I periodically swap out as backup, so not really a major concern.

fdisk -l /dev/sdc shows:

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      194903  1565556607+  ee  GPT
Partition 1 does not start on physical sector boundary.

Similar for the other two drives, but without a partition table.

I upgraded to natty on this server, erased the raid metadata with dmraid -rE and attempted to reinitalize with 
sudo dmraid -f isw -C BackupFull6 --type 5 --disk /dev/sdc,/dev/sdd,/dev/sde --size=5589G

same result from dmraid -s

*** Group superset isw_cdjhcaegij
--> Active Subset
name   : isw_cdjhcaegij_BackupFull6
size   : 3131048448
stride : 128
type   : raid5_la
status : ok
subsets: 0
devs   : 3
spares : 0

so no luck there.

I understand this may be an issue with dmraid, software raid, only supporting up to 2 TB drives, as is 32 bit addressing. 

Does this seem correct and should mdadm fix it?

---

### Post by psusi on 2011-06-19
Yes, mdadm will work, dmraid will not since it does not handle GPT.

---


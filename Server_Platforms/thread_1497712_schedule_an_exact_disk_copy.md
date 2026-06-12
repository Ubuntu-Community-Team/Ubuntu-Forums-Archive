---
title: "schedule an exact disk copy"
date: 2010-05-30
forum: Server Platforms
---

### Post by nikitchm on 2010-05-30
Hi guys,

Could you recommend the best way to do a scheduled backup of a server (PowerPC, Ubuntu 9.10), when an exact copy of the linux partition would be made on a disk of the same size? It seems there are several solution, but I have problems choosing the best.

Thank you,
M

---

### Post by ian dobson on 2010-05-31
Hi,

I would use cron to start a script at a specific time. This script unmounts the drive to be backed up and then copies the drive to another one using dd then mounts the drive again.

Or I would be to put both drives into a RAID1 array so that all writes to one drive get mirrored to the other online. Note RAID is not a backup, if you delete something by mistake it'll be deleted on both drives.

Regards
Ian Dobson

---

### Post by nikitchm on 2010-05-31
Hey Ian,

Thank you for the response. The solution with cron wouldn't suit me perfectly, as I'd like it to be completely automatic and as far as I understand the running Linux cannot unmount the disk it runs on to copy it and mount it back after that. Please, correct me, if I'm wrong.

But the RAID-1 solution sounds actually exactly what I need. But I have two questions about it. First, if I use 2 HHD's and the software solution for the RAID, how slower is that compare to the hardware implementation? I don't need it to be especially fast, but it's a server after all.. And the second, is it possible to have the whole system running on some hardware implementation of RAID-1? At the moment, as I wrote earlier, I have PowerPC with Ubuntu 9.10 installed on one HDD.

Thank you.

---

### Post by garfonzo on 2010-05-31
> **nikitchm said:**
> Hey Ian,

Thank you for the response. The solution with cron wouldn't suit me perfectly, as I'd like it to be completely automatic and as far as I understand the running Linux cannot unmount the disk it runs on to copy it and mount it back after that. Please, correct me, if I'm wrong.


I have the exact situation with my server. I have three data disks (two 320 GB and one 500GB). Every wednesday, I have a cron job run that mirrors all three disk onto three other disks of the exact same size. What I did was create a shell script which runs rsync to copy over *only new/changed documents* to the backup disks and the cron job executes the shell script. As a result, the backup is really fast as only a small amount of data transfer is required. The backup disks are perfect mirrors of the data disks.

The computers in my home can only see and access the data disks, but the computer I use can see all 6. The backup disks are exactly the same, in all regards, to the data disks so that if a data disk fails I can put the backup disk in place with zero down time.

> **nikitchm said:**
> 
But the RAID-1 solution sounds actually exactly what I need. But I have two questions about it. First, if I use 2 HHD's and the software solution for the RAID, how slower is that compare to the hardware implementation? I don't need it to be especially fast, but it's a server after all.. And the second, is it possible to have the whole system running on some hardware implementation of RAID-1? At the moment, as I wrote earlier, I have PowerPC with Ubuntu 9.10 installed on one HDD.

Thank you.

In my long search for the ideal, mirroring style backup, I cam accross a number of people who said I should shy away from RAID as a form of mirroring. Especially software RAIDs. I'm not sure why, (I never tried it as enough people suggested against it that I decided to not try) but I would suggest something other than RAID. 

Just my two bits. 

Cheers.

:-)

---

### Post by ian dobson on 2010-05-31
Hi,

I can't see why you should shy away from software RAID. I've been running software RAID (mdadm) on my backend server (currently 6 x 2Tb wd drives) for about 3 years and have never had a problem. Drives have died in the array ( 1Tb seagate) but the array kept on running an I didn't lose any data.

Mirroring could be abit slower when writing to an array as it must write to 2 disks (that could well be hidden my cache) and reading could be quicker at reading as several disks can be used (each disk only reading part of the required data).

Regards
Ian Dobson

---

### Post by disabledaccount on 2010-06-01
> **ian dobson said:**
> Hi,

I can't see why you should shy away from software RAID. I've been running software RAID (mdadm) on my backend server (currently 6 x 2Tb wd drives) for about 3 years and have never had a problem. Drives have died in the array ( 1Tb seagate) but the array kept on running an I didn't lose any data.

Mirroring could be abit slower when writing to an array as it must write to 2 disks (that could well be hidden my cache) and reading could be quicker at reading as several disks can be used (each disk only reading part of the required data).

Regards
Ian DobsonYou are absolutely right - rsync is good solution, but without extra-free performance boost on reading. What I can say: md is also much better than most of commercial software raid solutions, sold as "Raid controller" cards or bundled as BIOS modules. It has plenty of administrative options, online monitoring with email notifiction and more...

A word about writing performance: placing write-intent bitmap on separate array and proper usage of --write-mostly flag can do miracles (lets say - this gets md closer to ZFS or Lustre FS :) )

---

### Post by The Real Dave on 2010-06-01
Far as I can tell, you want a "bulletproof" backup system. So for that, I'd get a script to mount the drive, rsync new/changed data as has been suggested, and umount it when it's done. The script can be done fine, and I'm sure there's people here who can sort it out for you (mine are generally basic, and not so great). You'll need to run the script as root for the mounting and umounting, so instead of using 

```
crontab -e
```

your best off using the root crontab

```
sudo nano /etc/crontab 
```

Same cron, but with root powers :) Don't forget you need to specify the user "root". You'll understand when you have a look.

You'll also need to make sure that the drive your going to be mounting and umounting will always have the same drive name, otherwise your script might try copying the data to an incorrect device. I'm sure there's  a method of assigning a particular name to drive (making sure it's always /dev/sdb for example).

Other than that, your good to go.

Raid is a different solution, a kind of rolling security. Software RAID is perfect IMO, and usually a lot less hassle than a hardware card, for me at least. Mdadm is a fantastic tool, and [here's it's Ubuntu Docs page.]("https://help.ubuntu.com/community/Installation/SoftwareRAID") The type of RAID you'll need to use varies on how many drives you want in there and what you want, probably RAID1 for your case.


But like I said, if you want a separate "bulletproof" mirror, the script and cron is your way to go. Along the same lines, my desktops all backup to my server twice a day through RSync and Cron ;)

EDIT: Here's [my blog post explaining my RSync script]("http://linuxexpresso.wordpress.com/2009/12/29/rsync-backups/") and daily backups. The script also has the nice feature of pinging the server before starting RSync to make sure it's up and available. Could be useful for some, or if you want to spread the automatic backups further than your server.

---


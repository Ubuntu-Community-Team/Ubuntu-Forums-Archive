---
title: "New Ubuntu User Looking for Drive Config Advice"
date: 2010-02-04
forum: Server Platforms
---

### Post by CountryGuy on 2010-02-04
Hello all!  I'm planning to take a custom-built machine presently running Windows Home Server and convert it to a Ubuntu server to support the same backup functionality, but also allow me to support other server functions as well (WHS is great for backups and as a file server, but that's about it).  The machine has two 1TB 7200 RPM drives.  As the primary use for the machine is backups of files stored on the server as well as on the local PCs, I'd like to configure the box to support redundancy across both drives - So if one fails, I still have my data.  What would be the recommended configuration of the drives to support this?  I plan on using Bacula for the backups (clients and server).  

I'll assume the disk format won't be NTFS  :)  Quick question then:  If one of the drives fail and its the boot drive, how easy is it to recover the data from the other drive?  Just want to make sure there isn't some form of security that would prevent me from reading the data.  
 
I'm new to Linux with only a bit of Unix experience, but I figure I have to start somewhere (and I have a bit of technical expertise, just with the Windows platform) :)  This will also let me start playing with the LAMP stack.  As for my files, I have them all backed up on an external drive as well as my primary PC's disk, so I'm covered while I learn this thing.  
 
Thanks in advance, and if you have any other tips or sites to help get a Ubuntu server up quickly I'd appreciate it (although the Server guide here was a really good read, so hopefully I'm set).

---

### Post by Demented ZA on 2010-02-04
Are you planning on dual booting windows and Linux?

I wouldn't bother. I would run clean Ubuntu. (My 2 cents)

As for configuration of the disk, I would suggest software raid 1 (mirroring).
i.e: Disk 0 Would contain an exact copy of Disk 1. If one fails, you have an exact copy on the other. Only problem is that with 2 x 1TB, you'll only be able to use 1TB in total as the other drive will contain a mirror image.

You can read up more [here]("https://help.ubuntu.com/community/Installation/SoftwareRAID").

Hope that helps :-)

---

### Post by CountryGuy on 2010-02-05
Thanks for the reply!  Nope, no plans to dual-boot Windows and Linux;  This server is dedicated to being... Well... A server :)  As I mentioned, it currently runs Windows Home Server which functions fine as a file server and backup tool, but has its own issues I want to address with Linux:  

1) Can't really add other tools on to it other than Add-Ins (like network or ops management) 
2) I want to play with Linux to keep my Unix skills up to date (and to learn Linux itself)  

My plan is to use Ubuntu to manage backups with Bacula, file server functionality, check network traffic, and help manage the other PCs on the network.  

I don't think I want to set it up as a RAID 1, primarily because I do want this to function as a backup system;  While if a disk dies I can always recover the other one, wouldn't it be better to have Bacula store backups of the server (and the PCs) to the second TB drive, rather than setting up RAID?  

Two other questions this thread brought up:  

Would anyone have recommendations on software to handle the network traffic monitoring and PC management?  By PC Management, looking to be able to review system status and software, and deploy software to PCs on the network.  

As far as playing with Linux, I'm also thinking of putting VMWare ESXi on the bare metal box, then creating Linux in a VM.  This would give me some fault tolerance if I screw something up while I learn (and backups would be on the second drive, so recovery wouldn't lose anything).  Any thoughts on that?  

Thanks again for the help!

---

### Post by BobVila on 2010-02-05
> **CountryGuy said:**
> 

I don't think I want to set it up as a RAID 1, primarily because I do want this to function as a backup system;  While if a disk dies I can always recover the other one, wouldn't it be better to have Bacula store backups of the server (and the PCs) to the second TB drive, rather than setting up RAID?  

Two other questions this thread brought up:  

Would anyone have recommendations on software to handle the network traffic monitoring and PC management?  By PC Management, looking to be able to review system status and software, and deploy software to PCs on the network.  

As far as playing with Linux, I'm also thinking of putting VMWare ESXi on the bare metal box, then creating Linux in a VM.  This would give me some fault tolerance if I screw something up while I learn (and backups would be on the second drive, so recovery wouldn't lose anything).  Any thoughts on that?  

Thanks again for the help!

On not wanting to RAID the drives, a THOUSAND TIMES NO!!! Sure, if the OS drive takes a dump, you can always reinstall the system on a new drive and restore from backups, but what if the backup drive dies? Drives are cheap enough these days...

esxi is fun to play with for sure. If you do go that route, I'd consider backing up the server VM itself for some experience doing that. It comes in handy. While you're learning, take snapshots early and often  ;)

Take a little more time thinking about the backup solutions if you go with esxi, though. Between snapshotting, backing up vm states, and running bacula on the linux install, you'll probably be duplicating a hefty amount of data unnecessarily. 

Just my two cents.

---

### Post by CountryGuy on 2010-02-05
That's a good point on the RAID setup;  I guess what I'm concerned about is if a file is deleted or something happens within the OS that gets replicated across both drives.  I'd like to be able to restore from backup.  On the WHS box, I'm at about 36% utilization (including backups and drive)... So with RAID 1 and backups I'll probably be at around 70% utilization on the two drives.  Might have to think about tossing in another TB drive and going RAID 4...

---

### Post by KiLaHuRtZ on 2010-02-06
Could use rsync to replicate in the place of a RAID.  I personally hate mdadm, software raids, fakeraids, etc.  While cheap, you get what you pay for.  If you want a serious RAID and are looking to drop at least $400, get a 3ware RAID controller.  If not, use rysnc for your data.  Basically, make two identical partitions on each drive, have your backup software dump to one partition, then at a time interval you specify (perhaps daily or weekly) in cron, you can run a simple rsync script to sync the secondary drive to the primary.

The script...

```
#!/bin/bash

SHELL=/bin/bash
PATH=/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin

bkpSrcDev=/path/to/primary/drive
bkpDstDev=/path/to/secondary/drive

rsync -avx --delete --delete-after --delete-excluded --exclude=lost+found $bkpSrcDev/ $bkpDstDev/

exit 0;

#eof
```

Make the script executable...

```
sudo chmod 744 /path/to/script
```

Add this line to '/etc/crontab'...

For daily at midnight...

```
00 0 * * * root /path/to/script > /dev/null 2>&1
```

- Or -

For weekly on Sundays at midnight...

```
00 0 * * 0 root /path/to/script > /dev/null 2>&1
```

---


---
title: "How Probable is Hard Drive Failure?"
date: 2013-01-21
forum: Server Platforms
---

### Post by Zythyr on 2013-01-21
I want to build a personal home server. I am still planning which way I want to go (Windows, Linux, or NAS). However, during my planning, I keep coming to the notion of RAID an or data protection in case of hard drive failure. 

I know for sure I won't be using a hardware RAID. I'll be going with the software RAID route if I do use RAID. 

[B]My main question is, how probable is it that a hard drive will fail? Do server hard drives (regular 3.5inch hdd compared to 2.5inch laptop hdd) fail regularly?

Do I really need to consider using a RAID during my early stages of building a server? If I build my server without the use of RAID, can I convert it to a RAID in the future when I upgrade my hardware to have more hard drive slots (since at the moment I only have 2 hard drive slots available on my old desktop and only 2x 3TB hard drive)?
[/B]

---

### Post by Cheesemill on 2013-01-21
I would say that the probability of a drive failing is 100%.

All hard drives fail, it's not a matter of if just a matter of when.
I've got some 40GB drives kicking about that are still working but I've also had drives fail in the first week.

Also bear in mind that RAID will *only* protect you in the case of hard drive failure, it doesn't protect against user error, hardware failure, software bugs etc...
You should always have a full backup strategy in place *as well as* your RAID setup.

---

### Post by |{urse on 2013-01-21
A safe rule of thumb is that the drive will fail as soon as you really need it. If you go the RAID route, do it hardware with a mirror (RAID 6 or my favorite RAID 1+0). Mdadm is useful but horrendous if anything goes wrong with the OS. Best to keep your raid on a separate chip if your data is mission critical.

---

### Post by Cheesemill on 2013-01-21
> **|{urse said:**
> Mdadm is useful but horrendous if anything goes wrong with the OS. Best to keep your raid on a separate chip if your data is mission critical.

Only if you can afford to keep spare RAID cards lying around.

I tend to prefer mdadm for the reason that the drives can be moved to any machine running Linux and the array can be brought back up.

I've been in the situation more than once where a hardware RAID card has died and I've been unable to recover the array as the card was no longer in production or unavailable second-hand.

---

### Post by papibe on 2013-01-21
Hi Zythyr.

Yes, drives fail.

If your data, or the service it provides it is important, you'd need either some sort of duplication (RAID, zfs, etc), or comprehensive backup procedures.

Having said that, **they don't die like flies**. This is my experience (coincides with  I've read): drives have a considerable chance to fail in their first weeks of operation. Once you get to a month or so, the chances remain lower and flat for at least a couple of years. Starting the forth year, the probability of failure becomes significantly. 

Just my thoughts.
Regards.

---

### Post by spynappels on 2013-01-21
For home use, mostly as a file server, I'd have a small disk or even a USB stick for the OS, and a mdadm RAID5 array for the data.

I'd have a RAID5 array of at least 3 same size disks from different batches if possible, so that you have a good compromise between space (N-1 x capacity) while still maintaining redundancy. This way, if one disk dies, you can still get to your data, although access will be slower when the array is degraded.

In a production server in the workplace, I'd also have a hot-spare in place, but this is probably overkill for a home server, unless money is no object.

As Cheesemill said, use RAID ***_and_*** a good backup strategy, it's not an either/or scenario.

Lastly, a virtual environment is the perfect place to learn about mdadm and what to do when a disk dies. Try creating a VM with 6 x 2GB disks and create an array with or without hotspares and see what happens when you remove one.

---

### Post by |{urse on 2013-01-21
> **Cheesemill said:**
> Only if you can afford to keep spare RAID cards lying around.


Doesn't everyone? \\:D/ :lol:

---

### Post by Zythyr on 2013-02-03
> **|{urse said:**
> A safe rule of thumb is that the drive will fail as soon as you really need it. If you go the RAID route, do it hardware with a mirror (RAID 6 or my favorite RAID 1+0). Mdadm is useful but horrendous if anything goes wrong with the OS. Best to keep your raid on a separate chip if your data is mission critical.

> **papibe said:**
> Hi Zythyr.

Yes, drives fail.

If your data, or the service it provides it is important, you'd need either some sort of duplication (RAID, zfs, etc), or comprehensive backup procedures.

Having said that, **they don't die like flies**. This is my experience (coincides with  I've read): drives have a considerable chance to fail in their first weeks of operation. Once you get to a month or so, the chances remain lower and flat for at least a couple of years. Starting the forth year, the probability of failure becomes significantly. 

Just my thoughts.
Regards.

So after doing more research on RAID and possible backup strategies... I still have few questions. 

I prefer to go the software RAID route (mdadm) using RAID 5. However the issue is, I only have 2x 3TB hdd and 1x 500GB hard drive. Also, I can only fit 2x in my currently desktop enclosure. I can possibly make it fit 3 hdds if I remove the optical drive. 

1) If I do RAID 1 right now, can I switch/convert to RAID 5 in the future when I purchase more hard drives and upgrade my desktop enclosure to fit more hard drives? 

2) I want to do RAID 5, but I don't have 3x 3TB. I only have 2x 3TB.  Can I create a RAID 5 with only 2 hdds and pop in the 3rd HD in future? 

3) So I read about ZFS when I was looking into FreeNAS. Its my understanding ZFS is a file system (not a data redundancy method). If I go to FreeNAS route, how do I ensure data redundancy? Is there a RAID for FreeNAS? 

4) Since I have 1x 500GB hdd, I want to partition this hdd to install both Windows (personal use) and Linux (or FreeNAS) for a server. (I want to install Windows for personal use because my desktop is a lot faster than my other devices, so I might use Windows for task that require this performance.) Will this be a problem/ 

5) As @papibe, my RAID 5 can lose all the data if my OS is corrupted (which will be installed on my 500GB hard drive)  of if this 500GB hard drive fails. Is there a way I can backup the server OS (Linux/FreeNAS) onto another location (ex: external hdd) in case the OS does get corrupted?

6) @spynappels mentioned using a USB stick to install the OS on. Is this method feasible since USB (flash memory) only have limited number of read/writes and over time they can start to fail? 

7) I have heard people mention when installing the OS, to keep the /var/log or some other directories in a separate partition of the hard drive to prevent "run away logs". What does this mean? How do I do this? Also, when I install a software onto a linux, which directory does it get saved to? The reason I ask is, if I use a USB drive to run the OS, the USB drive will have limited space (~8GB-16GB). Won't this be an issue in the future if I want to install more software onto the Linux server? Won't I run out of space?

---

### Post by tgalati4 on 2013-02-03
3 and 6 go together.  Freenas and nas4free have a USB (readonly) boot to RAM option, so the OS runs in RAM and keeps it's log files in RAM.  So if you have *green* drives, your drives will spin down when not serving data and the OS has no disk to write to--and no disk to fail.

BUT, if there is a problem, there are no log files kept (since they vanish in RAM).  Some work arounds--send syslog messages to another linux server which is running a web server for instance.  I do this and it works well.  Set up text messaging/email for critical problems--this sends warnings out as they happen.  Not has good as log files, but you will know when your NAS is not happy.

The downside of a running in RAM, you will inevitably want to run more and more services and those services need a hard disk installation to store the database and configuration files.  There are ways of "respinning" your configuration to a new, bootable USB, but at some point, it is just easier to do a hard disk install and just keep adding services as you need them.

Yes, you can set up RAIDs on ZFS, but because ZFS has file corruption detection, it's not really necessary, but it depends on what your data availablity requirements are.  Remember ZFS and RAID are not a backup strategy.  You would still benefit a 3-2-1 strategy:  3 copies of critical data, 2 physical devices, 1 offsite.  How you accomplish that is up to you.

On 7) I have had a server running for 6 years continuously (with only a handful of reboots).  Uptime has been over 99%.  My logs are not huge.  440 items and 16MB.  The standard logrotate cronjobs do a decent job of compressing log files.  Now, if you have a runaway process or hardware failure then that could fill up a log file, but that has not been my experience.  So a separate hard drive or partition for log files for a home server is overkill.

4)  Windows is always a problem, because if you get a virus, it can destroy your partition tables, which makes getting access to your data problematic.

---

### Post by spynappels on 2013-02-03
Just to add that running from a USB is fine also in non read only mode for a system which will remain largely static (doing only a single or a few jobs, so not many OS changes) and logs are written to a partition on the RAID array. I've had several servers run like this for 3 years+ with no problems.

I have seen logs going mad and filling a disk, so even for a home server, I'd still create a small (~10GB) partition for /var/log/ .

I would echo tgalati4's 3-2-1 backup strategy as a must for important data.

---

### Post by markbl on 2013-02-03
> **Cheesemill said:**
> 
All hard drives fail, it's not a matter of if just a matter of when.
I've got some 40GB drives kicking about that are still working but I've also had drives fail in the first week.
Agree with this. Baring defects though, it is my experience that what vastly accelerates hard drives failing is a hot environment.

---

### Post by papibe on 2013-02-04
> **Zythyr said:**
> 5) As @papibe, my RAID 5 can lose all the data if my OS is corrupted (which will be installed on my 500GB hard drive)  of if this 500GB hard drive fails. Is there a way I can backup the server OS (Linux/FreeNAS) onto another location (ex: external hdd) in case the OS does get corrupted?
As others have already suggested it, I also would install the OS on another media different from the RAID.

Regards.

---

### Post by Hawkway on 2013-02-04
I recently added a home server to my network and considered having a RAID setup for my HDDS. However, as I started to think more about it, while availability of the data is important, what I really wanted to ensure was that I had a reliable backup of data. In my case, I installed two identical 2 TB hard drives and use Rsync to keep them identical with the files I want to backup. I use rsync incrememtal backups with the link-dest option so that I can have multiple versions of the same files. This worked well for me siince I'm the primary user of the server and if I have a problem with a drive, I can always go to the other backup drive easily.
 
I realize RAID is powerful and if you need it, it's great but just wanted to toss another idea out there.

---

### Post by Zythyr on 2013-03-03
1) Is the RAID partition/data safe and recoverable if the hard drive/USB that the OS is installed on fails? What I mean is, lets say for example HDD A has the OS installed, HDD B and HDD C are in RAID configuration with the /home attached to it. If HDD A fails, can I just get another HDD and install the OS again, install mdadm, and re-mount my RAID partition (B/C) onto the OS? 

2) How do I mount certain directories to a partition? For example, how do I mount a the /var/log to a certain partition? 

3) I plan on mounting my /home directory to my RAID partition since data in the /home is the only data that is most important to me... However, which other directories are important to be mounted onto the RAID partition in case the HDD with my OS fails and I need to reinstall the OS. I am not sure which directory software and their configurations get installed to, but is it necessary to backup that directory also? 

4) Overall, what is the best route to install the OS? Should I install it on a hard drive or USB drive? Is there a guide on how to install Ubuntu on a USB drive? If I install to a USB drive, I will be able to reboot my server right? 

5) Is it possible to convert RAID1 to RAID5 without losing any data on the hard drive? 

6) Because currently my desktop enclosure don't have enough HDD slots, I was wondering is it possible to have a RAID5 configuring with only 2x HDD and the 3rd one being "missing"? I an install the 3rd HDD in the future when I upgrade my desktop enclosure...

---

### Post by tgalati4 on 2013-03-03
1.  Yes, it will take some time but that is a valid recovery method.  You may need to use blkid to get the UUID's of the RAID disks and put the UUID's in some config files.

2.  You can create a symbolic link from /var/log to /mnt/newdrive/var/log--see man ln

3.  You should make a backup of /etc once a month or so.  Your configuration won't change much once your system is up and running.  Whether you copy /etc to a USB flash drive or make a backup onto RAID is up to you.  Remember RAID is not a backup strategy,  It is a method to increase data availability or speed or both.  Many home users think RAID is for backup when it's really designed for rapid data availability (as in a business with several users).  Many home users are not prepared to perform RAID recovery when things go wrong.

4.  Hard Disk or SSD install is easiest, because it's less reliable to install updates to a USB disk.

5.  It's possible but there is always a risk of data loss in a major RAID configuration.  Just as there is risk of data loss when resizing partitions.  You would need to back up your RAID1 data, make the new RAID5 array then repopulate the data.

6.  Bad idea.

---

### Post by joeyea3231 on 2013-03-04
I'm not sure of you hardware specs for this server but if it's 64 bit and has a fair amount of RAM, I would take a hard look at ZFS.  Regarding OS failure, ZFS allows you to not only import the pool once you reinstall the OS, but doesn't even require that it be on the same hardware, hard drives connected to the same SATA/SAS ports, or even that it's the same OS.  As long as the OS you install supports it's pool version it should import it with no issues.  That is one big caveat to keep in mind though since a more recent ZFS update in the Linux world has surpassed the pool and filesystem versions the other "big implementation" OSes support (FreeBSD, Solaris).  If you don't plan on switching OSes this isn't an issue.  This is actually something I did 2 months ago moving a 5 disk RAID-Z array from FreeBSD to Ubuntu Server.  Since the pool configuration is stored in metadata on the disks themselves you don't have any config files to restore and you recover doc would look like this:
     1.  Reinstall OS
     2.  Install ZFS Native
     3.  Run zpool import
     4.  On the list it displays, verify the pool you want to import and run zpool import -f [pool/ID]

At that point the pool will be imported and all the filesystems residing on it remounted.
     ZFS also helps in the provisioning speed of those 3TB disks.  If you set them up with mdadm you would still need to format them with whatever filesystem you plan on using and 3TB can take a substancial amount of time.  ZFS on the other hand will have it ready for you in under a minute.  Depending on the file system you would choose with a more traditional RAID setup, the feature set may also be much larger with ZFS with things like compression, quotas, and snapshots.  Like many others have stated, RAID is not a replacement for full backups as it doesn't prevent end user issues like deleting important files.  Snapshots are a great area to backup from and alleviate some of the overhead if there is an available snapshot when you need to restore.  Just note that snapshots alone are not a full backup solution either, but definitely something worth looking in to when developing your backup solution.

     On your questions 5 and 6 I would first ask if you plan on filling up 3TB (and in the case of the RAID 5 6TB) right away and how much time do you need to buy that 3rd drive?  Just based on what you've asked I would suggest RAID 1 as that's actually giving you working redundancy (and a performance bump for reads).  I'm sure you can fake out mdadm and create a 3 disk RAID 5 group and then pull that 3rd psuedo disk, but at that point you are starting with a degraded group with no fault tolerance at all and are no better off then if you had used RAID 0 until you buy that 3rd drive and resilver/rebalance the group.  If that 3TB drive is a month out I would have to say hold off for a month and build it the right way from the beginning.  If it's more like 6 months to a year then go RAID 1 and 6 months from now really think about incurring the cost overhead of a 4th drive and go RAID 10.

---

### Post by LHammonds on 2013-03-04
I don't think anyone has mentioned the difference between server-grade equipment and home-grade equipment.  Server-grade equipment is designed to be online all the time and tend to enjoy longer life in 100% online, all-the-time usage.  Taking home equipment and leaving it on all the time acting like a server will run the risk of the equipment failing even sooner.  Other factors to consider is how "clean" your power is going into your equipment.  Do you have it plugged directly into a wall (surge suppressor not much better)?  Or do you have your equipment plugged into a good quality UPS?  Does your area experience lots of brown-outs or lightning storms?

But regardless, you always need to plan on the equipment failing and how much you are willing to spend to lower the risk of "when" it does.

When speaking of RAID, do not think of it as any sort of "backup" at all.  Only a means to keep your system running if a drive fails.  You should always have a backup process in place.  Having all your partitions backed up on a regular basis for full disaster recovery is good but it takes time to run such backups.  It would also be good to couple it with smaller data/delta backups that happen more frequently.  Where your backups reside is also a VERY important consideration.  If the backup is on the same machine, a lightning strike or PSU failure could destroy it all in one shot.  Having it write to a drive on the same machine is handy and easy to schedule on a regular basis but you might want to consider having it written to an external drive or another computer on the network.  To further reduce risk of data loss, consider having the data written to an external disk and then alternate that disk with another at an offsite location on a regular basis.

Once you have a process figured out, the next item to determine is how many backups are you going to retain (how far back you can restore).

Getting the process automated as much as possible can save your neck when disaster strikes.  Relying on manual human interaction is another risk since it might not happen.  ;-)

LHammonds

---

### Post by Zythyr on 2013-03-12
**Firstly I want to thank all of you for taking your time to answer my questions. I really appreciate everyone's help. Once again, thanks a lot! **


> **tgalati4 said:**
> 1.  Yes, it will take some time but that is a valid recovery method.  You may need to use blkid to get the UUID's of the RAID disks and put the UUID's in some config files.

3.  You should make a backup of /etc once a month or so.  Your configuration won't change much once your system is up and running.  Whether you copy /etc to a USB flash drive or make a backup onto RAID is up to you.  Remember RAID is not a backup strategy,  It is a method to increase data availability or speed or both.  Many home users think RAID is for backup when it's really designed for rapid data availability (as in a business with several users).  Many home users are not prepared to perform RAID recovery when things go wrong.


1. I looked at this guide, and it seems rebuilding/recovering the RAID partition is a lot more simpler: [http://askubuntu.com/questions/11293/rebuild-mdadm-raid5-after-os-hard-drive-died](http://askubuntu.com/questions/11293/rebuild-mdadm-raid5-after-os-hard-drive-died), Are you sure recovering/rebuilding the RAID partition after a fresh OS install is difficult? 

2. So /etc store all the configurations? Which directory stores all the software/apps I install? 

> **joeyea3231 said:**
> I'm not sure of you hardware specs for this server but if it's 64 bit and has a fair amount of RAM, I would take a hard look at ZFS.  Regarding OS failure, ZFS allows you to not only import the pool once you reinstall the OS, but doesn't even require that it be on the same hardware, hard drives connected to the same SATA/SAS ports, or even that it's the same OS.  As long as the OS you install supports it's pool version it should import it with no issues.  That is one big caveat to keep in mind though since a more recent ZFS update in the Linux world has surpassed the pool and filesystem versions the other "big implementation" OSes support (FreeBSD, Solaris).  If you don't plan on switching OSes this isn't an issue.  This is actually something I did 2 months ago moving a 5 disk RAID-Z array from FreeBSD to Ubuntu Server.  Since the pool configuration is stored in metadata on the disks themselves you don't have any config files to restore and you recover doc would look like this:
     1.  Reinstall OS
     2.  Install ZFS Native
     3.  Run zpool import
     4.  On the list it displays, verify the pool you want to import and run zpool import -f [pool/ID]

At that point the pool will be imported and all the filesystems residing on it remounted.
     ZFS also helps in the provisioning speed of those 3TB disks.  If you set them up with mdadm you would still need to format them with whatever filesystem you plan on using and 3TB can take a substancial amount of time.  ZFS on the other hand will have it ready for you in under a minute.  Depending on the file system you would choose with a more traditional RAID setup, the feature set may also be much larger with ZFS with things like compression, quotas, and snapshots.  Like many others have stated, RAID is not a replacement for full backups as it doesn't prevent end user issues like deleting important files.  Snapshots are a great area to backup from and alleviate some of the overhead if there is an available snapshot when you need to restore.  Just note that snapshots alone are not a full backup solution either, but definitely something worth looking in to when developing your backup solution.


I was really wanted ZFS, but I thought ZFS was only for FreeNAS/FreeBSD. My understanding was/is that ZFS is not yet fully developed or stable for Ubuntu/Linux. Is it a good idea to use ZFS in Linux since it can have a lot of bugs unlike FreeBSD where ZFS is native? How would I go about installing or implementing ZFS in Ubuntu? Is there a guide? 

> **LHammonds said:**
> I don't think anyone has mentioned the difference between server-grade equipment and home-grade equipment.  Server-grade equipment is designed to be online all the time and tend to enjoy longer life in 100% online, all-the-time usage.  Taking home equipment and leaving it on all the time acting like a server will run the risk of the equipment failing even sooner.  Other factors to consider is how "clean" your power is going into your equipment.  Do you have it plugged directly into a wall (surge suppressor not much better)?  Or do you have your equipment plugged into a good quality UPS?  Does your area experience lots of brown-outs or lightning storms?

But regardless, you always need to plan on the equipment failing and how much you are willing to spend to lower the risk of "when" it does.

When speaking of RAID, do not think of it as any sort of "backup" at all.  Only a means to keep your system running if a drive fails.  You should always have a backup process in place.  Having all your partitions backed up on a regular basis for full disaster recovery is good but it takes time to run such backups.  It would also be good to couple it with smaller data/delta backups that happen more frequently.  Where your backups reside is also a VERY important consideration.  If the backup is on the same machine, a lightning strike or PSU failure could destroy it all in one shot.  Having it write to a drive on the same machine is handy and easy to schedule on a regular basis but you might want to consider having it written to an external drive or another computer on the network.  To further reduce risk of data loss, consider having the data written to an external disk and then alternate that disk with another at an offsite location on a regular basis.


Yes, that is a very good point you mentioned. My server/RAID configuration is not going going to be my only backup. I also have multiple external drives to ensure I have multiple copies of my important data. However, doesn't a RAID configuration have data redundancy? Multiple hard drives in the RAID configuration have the same data, thus failure of one hard drive will still allow recovery of the data?

---

### Post by bab1 on 2013-03-13
> **Zythyr said:**
> [B]...
I was really wanted ZFS, but I thought ZFS was only for FreeNAS/FreeBSD. My understanding was/is that ZFS is not yet fully developed or stable for Ubuntu/Linux. Is it a good idea to use ZFS in Linux since it can have a lot of bugs unlike FreeBSD where ZFS is native? How would I go about installing or implementing ZFS in Ubuntu? Is there a guide? 
ZFS isn't anymore *native *to BSD that it is to Linux.  ZFS was developed by SUN and is native to Solaris UNIX.  Your best bet is to get Ubuntu forum user @rubylaser to help you.  He uses ZFS on Both Linux and Solaris. 

 See [**_[COLOR="#FF0000"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2104672&highlight=rubylaser") for an interesting discussion with @rubylaser.> 

Yes, that is a very good point you mentioned. My server/RAID configuration is not going going to be my only backup. I also have multiple external drives to ensure I have multiple copies of my important data. However, doesn't a RAID configuration have data redundancy? Multiple hard drives in the RAID configuration have the same data, thus failure of one hard drive will still allow recovery of the data?
A RAID implementation should **never be used in place of a backup strategy**.  The data is striped across all the disks in RAID 5.  A mirrored RAID is no better that using a single disk and a backup in the long run.  In my opinion, with large disks (1TB >) RAID fails for many when being rebuild after a disk failure.

See [**_[COLOR="#FF0000"]here[/COLOR]_**]("http://storagemojo.com/2012/07/23/the-post-raid-era-has-begun/") for more about why NOT to rely on RAID.

---

### Post by rubylaser on 2013-03-13
I would love to know what type of stuff you want to store on the array.  I use ZFS, mdadm, and SnapRAID and they all work very well.  I have used both ZFS and mdadm for home storage (and enterprise) for years, but I've come to think that SnapRAID for most home users is the easiest solution.  If you don't need the blazing throughput of ZFS or mdadm, SnapRAID + AUFS is a great solution. I have some setup directions for both mdadm and SnapRAID in my signature.  The good news is any of these solutions will work great :)

---

### Post by Vegan on 2013-03-13
[http://www.windows-it.tk/wp/disk-reliability.php]("http://www.windows-it.tk/wp/disk-reliability.php")

---

### Post by LHammonds on 2013-03-15
> **Zythyr said:**
> 
My server/RAID configuration is not going going to be my only backup.

You are still thinking incorrectly here.  RAID is not a "backup," it is redundancy mainly to reduce risk of downtime.  In a 3-drive RAID, you can lose 1 drive and still hobble along and let a new drive get rebuilt.  However, if you lose 2 or 3 of the 3 drives, you are just as dead in the water if you didn't use RAID.  With hardware RAID, you also have to be concerned about the RAID card.  You should always have 2 of these cards.  The spare would be used if the production RAID card failed so you can get back up-and-running quickly without worrying about finding someplace you can buy one and wait for shipping.  When a drive fails in a RAID system, the entire system slows down while that drive is offline because it has to dynamically determine what this missing data is whenever it is accessed.  The system goes even slower when you put in a new drive and it begins the rebuild process.

Again, RAID is only to reduce risk of downtime.  That should be all it is considered.   It should never be considered "a" backup solution because if your PSU blows and shorts everything out in your computer (including the drives), can you "restore" from that "backup"?  Nope.

> **Zythyr said:**
> 
I also have multiple external drives to ensure I have multiple copies of my important data.

That is very good.  Make sure to always keep one of them offsite and safe from a single flood/tornado/earth quake/evil bunny attack.

> **Zythyr said:**
> 
However, doesn't a RAID configuration have data redundancy? Multiple hard drives in the RAID configuration have the same data, thus failure of one hard drive will still allow recovery of the data?

Not quite redundant depending on how you configure it.  Striping (RAID 0) spreads the data out over multiple drives and thus ensuring fast read access but lose one drive and the whole thing topples down.  Mirroring (RAID 1) has a copy of all data one 2 drives so if one goes down, the other is used instead and is fully redundant.  Raid 5 uses a parity bit on all the drives so if one dies, it can mathematically calculate the missing data based on the 2 drives beside it (which is why you MUST have at least 3 drives for RAID 5).  Here is a good and quick explanation of [how RAID 5 works]("http://blog.open-e.com/how-does-raid-5-work/").  RAID 10 is a combination of mirroring and striping which performs better than RAID 5 for large drives.  Here is another [good summary for common RAID levels]("http://www.thegeekstuff.com/2010/08/raid-levels-tutorial/").

Again, redundant does not equal backup.  No matter how you have your drives configured in your machine, if the PSU blows up or you take a lightning strike or brown out that destroys your hardware, RAID CANNOT restore from it to a new system.

LHammonds

---


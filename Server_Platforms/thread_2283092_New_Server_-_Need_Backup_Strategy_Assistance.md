---
title: "New Server - Need Backup Strategy Assistance"
date: 2015-06-19
forum: Server Platforms
---

### Post by Marc-NJ on 2015-06-19
I previously had an Ubuntu 12.04 LTS server that I was running off of a single 2 TB hard drive.  I had also installed CrashPlan on it and was backing up some data from it to the cloud (including the entire home directory and sub-dirs and some other random locations).  Unfortunately, I was stupid and started using the server for more and more important things and at some point the HD started going bad and getting corrupted.  I haven't turned it on since, and at some point will need to figure out how to retrieve what I can off of it (or my cloud backups).


But since then I've acquired a more powerful machine, installed 2 x 4 TB drives and 1 x 6 TB drive in it, and installed Ubuntu 14.04.2 LTS on it using mdadm software RAID1 across the 2 x 4 TB drives (it had fakeRAID, but based on my research and previous postings, it seems that mdadm software RAID is a better way to go so I disabled the fakeRAID).  However, before I start using this new server, I want to make certain that my backup strategy is sound and functioning correctly.  I know that RAID1 is NOT a backup solution, which was the reason I also got the 6 TB drive.  But at this point, I'm not sure how best to proceed with using that drive.  
	- I want to definitely installed CrashPlan again so I can back up to the cloud as well as the 6 TB drive
	- I'd potentially like to use CrashPlan to also back up locally to the 6 TB drive (if appropriate)
	- I'd also like to figure out a way to do a full bare metal backup (or as close to it as possible; hopefully without having to shut down the server when doing it) every so often (on a schedule if possible)


My problems are:
	- I don't know what exactly to specify that CrashPlan backup (both to the cloud and to the 6 TB drive locally) so that I can be sure I'm backing up everything important  (I'm not new to Ubuntu, but am self-taught and so have gaps in my knowledge that prevent me from fully understanding how everything is structured and what's important and what's not)
	- I don't know what software to use to do the "bare metal backups" (or as close to it as possible) -> should I just be using something like rsync, or are there presumably better software packages or solutions out there?
	- Are there other options or alternatives I should look at or am missing out on?


Any help on this is greatly appreciated!  Thanks!

---

### Post by mastablasta on 2015-06-19
depends what you want to backup. I use server for backup as well as a few other things. 

if you are backing up the system then either rsync or maybe easier and better is rdiff-backup. I plan to use it to do the system backup. it has versioning and all.
for backup form computers to server I plan to use Areca (on windows) and maybe Luckybackup on Linux pc's (for some reason it doesn't do the backup on windows), though I am still thinking if I should maybe instead pull the backups to server using urbackup.

doing system images is not really possible while system is running. 

so you will have about 7.2 TB in your RAID array and you want it all backed up to 1x 6 TB drive? and you plan to use crash plan to back it all up in the cloud as well?

edit: also crahsplan looks like a desktop app, do they also have command line or are you maybe running desktop on your server?

---

### Post by Marc-NJ on 2015-06-19
> **mastablasta said:**
> if you are backing up the system then either rsync or maybe easier and better is rdiff-backup. I plan to use it to do the system backup. it has versioning and all.

Could you point me to any documentation or information on how to implement?  Also, what I really need to know is specifically what files/folders/structure within Ubuntu Server to backup (both via CrashPlan to the cloud and the 6 TB drive, and via whatever other method I implement to the 6 TB drive that hopefully would allow me to do a full recovery if necessary)

> **mastablasta said:**
> for backup form computers to server I plan to use Areca (on windows) and maybe Luckybackup on Linux pc's (for some reason it doesn't do the backup on windows), though I am still thinking if I should maybe instead pull the backups to server using urbackup.

I think you're stating here what would be necessary to backup PC workstations to the Ubuntu server, right?  That is one thing I'm actually not doing, since I have other backup methods for my PC workstations - but thanks for the info!

> **mastablasta said:**
> doing system images is not really possible while system is running. 

So does that mean there's no way to get a full backup that could be used to do a full recovery in the event the system somehow suffered a catastrophic failure (i.e. both RAID1 drives died, etc.)?  If I'm willing to take the system down once a month or so, what would you recommend - just a Clonezilla backup, or something else?  I'd prefer to automate it, but I guess if that's not possible I still want to have something for a full recovery if necessary.

> **mastablasta said:**
> so you will have about 7.2 TB in your RAID array and you want it all backed up to 1x 6 TB drive? and you plan to use crash plan to back it all up in the cloud as well?

I don't think I'll have 7.2 TB of data to backup actually - I might have that amount (although probably much less since I'm not planning to fill the drives to capacity anytime soon) technically, but because RAID1 is doing mirroring, I'd only need to backup half of the data actually residing on both drives since it's basically a duplicate.  And presumably since the Ubuntu Server system only sees one file system anything I run on it will be smart enough not to back up the duplicate data on the second drive, right?

And I want to use CrashPlan, but not necessarily to back up every file and folder on the Ubuntu Server.  That's why I was asking before for a "strategy" and understanding on what is important to back up.  I know with Windows PC's, for instance, backing up the "Windows" dir or the "Program Files" dir is usually not appropriate, since you can just reinstall Windows and the applications.  Obviously, you might lose some configuration doing that, but backing up the "Users" directory and sub-dirs is the most important.  So I'm obviously going to back up the "home" dir and all sub-dirs, but I'm sure there's other stuff spread throughout the file system that might also be useful to backup (i.e. website info and config, mysql databases, etc.) and since I don't know enough to be sure I'll get everything, and don't just want to select everything, I figured someone on here might point me to a good strategy.

> **mastablasta said:**
> edit: also crahsplan looks like a desktop app, do they also have command line or are you maybe running desktop on your server?

Actually, CrashPlan can run on Linux machines that are headless as a service, which is how I'll install it on this new server (and how I've used it on other Linux machines in the past with no issues).


Thanks!

---

### Post by mastablasta on 2015-06-22
well look like this article is popular: [http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)

also they have good examples: [http://www.nongnu.org/rdiff-backup/examples.html](http://www.nongnu.org/rdiff-backup/examples.html)

looks preety easy to use. 

yeah i dont' know what i though that you have 2x 8TB :-O sure enough you can back it all up to the 6 TB drive.


/etc has configurations
/var has variable data as well as any webstuff.
/home has user files

the applications I see people usually just create a list and put them in a script to reinstall later with ease. but you could back them up as well.


I will also have a look at crashplan now if it can really run as service in command line only. might a good option to backup the os to.

---

### Post by TheFu on 2015-06-22
> **mastablasta said:**
> 
the applications I see people usually just create a list and put them in a script to reinstall later with ease. but you could back them up as well.

Pre-Backup:
```
dpkg --get-selections > /root/backup-list-o-pkgs
```

Restore:
```
dpkg --set-selections </root/backup-list-o-pkgs
```
Then use dselect and install them.

These 2 little commands save about 4G-8G off every backup which is useful as more and more systems are involved.  Not so useful for just 1 system ... except the backup time saved nightly.

Of course, for a server it is probably best to use an LVM snapshot so uptimes aren't impacted by backups.

---


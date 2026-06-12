---
title: "Suggestions for Bare Metal Backup"
date: 2016-06-26
forum: Server Platforms
---

### Post by martinwebster on 2016-06-26
I recently switched from ClearOS, with a brief evaluation of FreeNAS, before settling on Ubuntu Server 16.04 for my home NAS / media server. In brief, I have the OS running on a single SSD (LVM) with data utilising ZFS: a single pool with two mirrors, i.e. 4 disks. I'm using CrashPlan (gui via xauth and XQuartz) to backup to the cloud and Plex to serve media. I'm also running NFS for Mopidy (HiFi audio), Netatalk (Time Machine and Apple shares) and Samba for Windows devices. There's also a UPS managed with apcupsd.

This is running on an HP Proliant N40L microserver with 16GB ECC RAM and a non-stock Intel NIC.

Before building the production server I used a VM to play with the configuration and document my run book. It took about a day to build the server. Now it's running flawlessly.

So to my question ... I want a relatively straightforward solution to backup the OS so I can rebuild this from scratch without the hours of config changes. Any suggestions? The solution must be headless. Would an LVM snapshot do the trick?

---

### Post by TheFu on 2016-06-26
Don't know what you should do, but here's what I do. Backup the OS and data separately.  Things that change all the time get versioned backups using **rdiff-backup**. Different systems have 30, 60, 120 days of versions - depends on the attack surface how many. Takes about 30-45 min to get everything back (for each) .... except the data.  Data that doesn't change often (if ever), gets an **rsync** to backup storage. Takes between 2-15 minutes to backup the systems - just depends on the total number of files involved. Media files get manually synched to storage a few times a week ... reminds me need to kick one off now.

I decided years ago that backing up the 4G of the OS from every systems was a waste of time AND storage, so I only backup the settings and installed packages. On my email front-end box, 120 days of backups is less than 100MB (yes, MB). On that machine, it isn't about the data, but the settings. That means during a restore, I have to put a base OS back (server with ssh-server only), then put all the settings back, then re-install all the packages, then install all the data.  The trick initially is to be certain to get all the information and settings needed. Most is covered by grabbing /etc/, but don't forget crontabs that are in /var/spool/ too.  I also capture RAID and lvm setups - mainly as a guide for later, but not strictly required. That restore is less than 45 min to a working system that is the same as the last backup point. I do daily backups.

BTW, the only way to do true bare metal backup is to boot of alternate media and bit-for-bit copy everything to identical storage. For me, that is just too much of an inconvenience. Back in the early 2000s, I did it this way and found I only made backups every quarter, at best, but usually less often. Tools for this are: dd, ddrescue, partimage, clonezilla.

LVM snapshots aren't a backup tool alone. They are a way to freeze any files so that other tools can be used to perform the backup of the frozen area. For a DBMS, the file system still needs to be quiesced for the DB before performing the snapshot. For small DBs, I'd just dump the DB to a gz file and use that to restore.

Of course, you could use ZFS to zsend to another box, but without another machine running ZFS, that isn't an option.  Do you have a backup server to stream this data at? Does it run ZFS?

What's your recovery plan? How long will that take? Have you tested it? What is the cost?  In professional IT, we use RTO and RPO analysis to determine what the backup and recovery plan need.  If you want everything working the same day as the failure happens, off-site backup storage really isn't useful.  Next day delivery of HDDs will cost - probably $300+ per disk.  If you download the data, that becomes a month-long effort, perhaps longer.

On my network, there are about 20 systems to backup. Most are VMs, but I treat them just like physical servers. Don't currently have any ZFS, but your use of it is what I plan with the next disk upgrades.  I backup the backup server using the same techniques, just not the storage holding all the backups.

Don't have any 16.04 servers here yet, maybe in the fall. Too new to assume that all my normal programs are available on that release. Some of them take 6-12 months for a stable program release to catch up.

Make sense?  I look forward to what others do here.  There is always a trade-off between simplicity, completeness, time and storage.

---

### Post by martinwebster on 2016-06-26
Thanks for your reply, TheFu. This is a home installation, but also a hub for students living away from home. Nonetheless, our data are important and is backed up regularly; multiple local copies plus cloud. Unless we work offline, which is rare, RPO is measured in minutes. RTO is moot. I'm not running a business and the total loss of all "local" data copies is highly unlikely and I have a good deal of redundancy built into my solution. Worse case scenario, I would recover from the cloud and that could take a week or so albeit I would cherry pick important data first.

So, I'm looking for a solution to restore my home server (sans data) quickly. Yes, I need /etc plus my custom scripts, crontab etc. Ideally, I'd like a solution that creates a clone of my system drive without the need to bring the system down: dumping an ISO in the data store. Some years ago I achieved this with BackupEdge (RecoverEdge.) Unfortunately, my licensed copy stopped supporting newer kernels many years ago and personal licenses are no longer available.

An LVM snapshot was simply an idea; I haven't explored this yet. I was wondering if Mondo Rescue is a reliable solution, but the site has been down all day, so I'm not sure if it is a live project or supported on Ubuntu 16.04. I'm also disinclined to use software that's not in the standard repos.

Looking forward to other suggestions and scenarios.

---

### Post by kenz71 on 2016-08-21
Understanding this post is in a hibernate status, maybe I'll bring it back...

Having as much as possible running on a VM somewhat takes care of the bare metal backup concept. That is all the settings would be saved in the .vdi, .vmdk or whatever extension applies to your VM platform. Right?

Then the VM guest files can be thought of as data, so having scheduled reboots to commit any unchanged data then copy those files off to your backup wherever that might be.

Or am I missing something in here?

---

### Post by martinwebster on 2016-08-21
> **kenz71 said:**
> Understanding this post is in a hibernate status, maybe I'll bring it back...

...

Or am I missing something in here?

I think so. I'm not using a VM for production use. I still don't have a satisfactory solution; when I last had a look Mondo was broken on 16.04 and I've not had time to checkout LVM snapshots.

---

### Post by TheFu on 2016-08-21
LVM snapshots are just the first step to stop the data to be backed up from changing. It is NOT a backup method. We still need to actually backup the snapshot area.

VMs that are file-based (lower performance), can be turned off, then those files copied. I suppose that is a backup method. Never done it that way - since all the wasted space would be included. Why copy 50G of storage when only 15G is actually used?

I use VMs extensively. Basically since 2008, all production systems have been running inside VMs - even my daily desktop is a VM.  There are many reasons for this.  VMs abstract the physical hardware away from the OS. That isn't too important with Linux, but for proprietary OSes, it is very helpful.  Getting a performance upgrade by swapping in faster HW without having to reinstall has been very nice.  My Linux VM backups are exactly the same as my physical Linux backups. Restoration steps are the same.  Backups take about 1-5 minutes for each system.  Restores take between 30-45 min for each system.  Only the media restore could take longer, but that data isn't versioned, it is just manually mirrored a few times weekly.  System settings, lists of installed packages, DBs, and HOME files are backed up daily, versioned, automatic.

Don't forget that versioning is absolutely critical for backups.  Having 1 copy is useful about 80% of the time, but there are times when having 60 versions (without wasting the storage space for 60 versions) is absolutely critical.  rdiff-backup does this stuff for me, but on paper, duplicity is the best backup tool. Sadly, I couldn't get it working the way I liked and really sadly, it follows the same backup methods from 1970 with weekly fulls and daily incrementals. I really want the last backup to be a mirror that is trivially restored and providing a user file recovery is just a file copy - no tool needed. In a home environment, this last item is a special requirement and very nice to have.

For true bare metal backup - use ddrescue, but boot off alternate media. I suppose switching to single user mode would be possible, but under systemd ... things have changed, I suspect.

---

### Post by toby-humphrey on 2016-10-20
Hi Martin,

I came across this thread because I would like to acheive the same thing.

I have a headless 16.04 server installed to an SSD and serving a ZFS disk pack. The ZFS data is synced to a personal offsite backup location, but I would also like to have an image of the SSD so if something goes wrong with it I can reimage a new SSD, plug it in and the server will be back up and running again in no time.

Now there are 2 decent solutions:

1. Shutdown the server, boot from a live disk and image, shutdown, remove disk and reboot.

This is tough on a headless, but my plan is to set up a live disk that will automatically start ssh so I can log in from another computer, run the imaging and shutdown. This does however require that your BIOS is already set to boot from the USB first, instead of the OS drive already installed...so this MAY require some time with a display attached to get the BIOS set up.

2. Boot from a network OS on a separate DRBL server.

I don't want to go down this route - another server to maintain...


I'll let you know how it goes for me!

Toby

---

### Post by cariboo on 2016-10-21
@toby-humphrey, the last time the op of this thread logged in to the Forum, was the last time he posted, so you may be waiting for a long time for an answer. I'd suggest you create a new thread of your own.

---

### Post by martinwebster on 2016-10-21
Hello Toby,

We have a similar configuration and I'm also running headless and don't want to shut the box down to perform imaging.

Here's what I currently do with the OS:

1. Include important system files in the cloud backup solution, e.g. /etc.
2. Rsync the system drive to my ZFS store

```

sudo rsync -aAX --info=progress2 --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found","/store"} / /store/backups/
```

(Archive, preserve acls, preserve extended attributes)

I have documented the steps needed to build the server, so worst case scenario I'll need to set aside a day to rebuild.

---

### Post by TheFu on 2016-10-23
Rebuilding a server should be 30-45 min, tops.  Then whatever time it takes to put the data back, usually 5 min, but large data could require longer. If the restore method takes longer than that, there are better methods.  I've described the steps multiple times in these forums.

---


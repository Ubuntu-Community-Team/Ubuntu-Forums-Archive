---
title: "Full server backup"
date: 2013-08-22
forum: Server Platforms
---

### Post by Dan_Joyce on 2013-08-22
I need to back up a client server running Ubuntu Server 12.04 ( I  think...) to an external drive. They had someone in the past set up a command for them that tars the entire drive to a backup file then they move that file to a backup drive. I'm asking for help on a few items:
[LIST=1]
[*]Please review the backup steps they take now and tell me if they are sufficient to accomplish a bare metal restore assuming the server hard drive fails or we move it to another machine altogether. I'm trying to test that now, but at 100GB, the backup file takes some time to move around and attempt a restore.  (more below)
[*]I'm going to attempt restoring this to a virtual machine in VirtualBox. That should work, right?
[*]What is the best long-term backup strategy for this. My priorities are minimal down-time, but a few hours is alright. My feeling is I should be able to get incremental backups set up using three or four external drives they'd cycle off-site weekly. A RAID1 mirror is on my list too. So, what's the best way to set up incremental backups on Ubuntu Server? Note: I have a test server here and tried Backula, but couldn't figure it out, even after reading a bunch of tutorials. Does this or another application work to do as I wanted, especially considering multiple drives and incremental backups? If not, what scheme do you all recommend?
[/LIST]

More info on 1.: 
Here are the steps they currently take to make a backup:
[LIST=1]
[*]Plug in backup drive, navigate to Webmin, mount the external drive under /mnt
[*]through Putty (remote from another machine):
```
cd /mnt
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```
[*]when complete they copy the backup.tgz file to a folder named by date
[*]unmount drive and walk off-site with it.
[/LIST]
so, does this look good enough for now? They've never tested a restore and that's what I'll try once I have this file copied. Any advice for setting this up in a vm as if a bmr?

Thanks for any tips or advice.

---

### Post by TheFu on 2013-08-22
**Tar** is the 1980s way to backup servers.  It is fine for small backups of a few MB, but probably shouldn't be used for anything larger. There are far better tools than tar - by far.  rbackup, rsnapshot, a custom rsync script with versioning, rdiff-backup, duplicity ... lots of options that will be faster and easier to restore.

I wouldn't trust that "cd" command to work.  I'd point the tar directly at /mnt/backup-`date "+%Y%m%d"`.tgz, but only after validating that the drive was actually mounted somehow. ... either by looking for a specific file that is only on the other media or by checking the mtab via a **df** command.  It is possible to write to /mnt with no media actually mounted there. It might fill the partition to 100% capacity and make lots of bad things happen.  There are a few threads here where people lots 100G+ of storage and couldn't find it. It was buried under a mount that failed once.

Versioned backups are important.  You should be able to get the system back from yesterday, last week, last month.

100% automatic backups are critical. If a human needs to swap in a HDD, it will fail eventually.  Backups are my life and I can't be bothered to connect a HDD for backups even weekly. Automatic.

Efficient on storage.  Having 60 days of backups shouldn't require 60x the storage.  OTOH, for 1.2x the original storage, you can have 60 days worth of versioned backups. I do this today across more than a few servers. Modern backup tools completely rock.

Do you have multiple servers on the same LAN or do you need to push the data over a WAN connection?  That first backup can suck, but the incrementals should be minimal.  I like having a local backup, then a mirror of those backup areas off-site.  The off-site backups have **never** been needed in 10 yrs, but the local ones have been used about once a year.

Whether a restore will work to a VM or not depends on how tightly the OS is connected to non-standard hardware.  The network device will certainly change names - it is controlled by the MAC address ... so if you have eth0, you will get an eth1 in the new VM ... until you clean that up or change the MAC in the appropriate /etc/udev/.... file.

In the last week, I've written replies here on backups with lots of links to presentations about different backup tools, including my favorite, **rdiff-backup**. If you are interested, you can search and find those links and presentations. I hope they are helpful.  There's an example script in those links too.

If you need to store the backups on untrusted remote storage (Amazon S3 or an FTP site), then look at duplicity which can encrypt the files on the way to the storage.  I don't like the "set" of files it uses - need the tool to restore 1 file, unlike rdiff-backup which stores the most recent backup as a mirror - want to restore 1 file - copy/scp/sftp rsync it back where you need it.  Same for the entire directory. It is only to restore files that are older where the tool is handle ... even then, it isn't required. I really like rdiff-backup for those reasons. The data isn't stored in some weird format. I can get to it easily when my mind isn't working fully at 4am.

I've been thinking about cleaning up my current backup script so it is safe to publish. Someday.  For every server here, the backup scripts are just a little different - sometimes I need to shutdown a SQL server first, or dump the SQL to a file before running the backups to avoid corruption with changing files.  OTOH, I have used rsync to migrate a running blog server to a different box and everything turned out fine.

Testing the restore is a good idea.  BTW, if you have just 1 partition of 100G, I think your server isn't setup in a "smart" way.  It is a good idea to have the OS and apps on 1 partition and the data for the main app of the server on a different partition.  It will make OS upgrades easier, trust me.

I'm confused. Why use **webmin** at all?  mounting a USB device is pretty easy for a script.

Good question. Thanks.

---

### Post by CharlesA on 2013-08-22
Don't forget to exclude /dev too.

This probably has more information than you need but give it a read anyway.
[https://wiki.archlinux.org/index.php/Full_System_Backup_with_tar](https://wiki.archlinux.org/index.php/Full_System_Backup_with_tar)

As far as checking to see if a folder is mounted, mountpoint works wonders. ;)

I don't usually backup my server installs as they are easy to reinstall from scratch. I do backup my data via rsync.

EDIT: I can dig up the rsync script I use that uses hard links to do incremental backups.

---

### Post by TheFu on 2013-08-22
Hey Charles!

Loved the '**mountpoint**' command. Taught me something new, but it doesn't always work.
```
$ mountpoint /Data
mountpoint: /Data: Value too large for defined data type
```
Tried it with sudo too, same failure.  It worked fine on most directly connected mounts ... just the external, network ones failed.

The rsync examples website [https://rsync.samba.org/examples.html](https://rsync.samba.org/examples.html) has lots of great sample scripts. I think **rsnapshot** and **rbackup** are based on those versions from there.

To backup a list of packages on Debian or Ubuntu or Mint, use **dpkg --get-selections > ~/list-o-pkgs.txt**.  Then when it is time to restore on a new HDD use **dpkg --set-selections < ~/list-o-pkgs.txt**.

---

### Post by CharlesA on 2013-08-22
Nice catch The Fu. :) So far I have only ever used mountpoint in bash scripts for local media. I guess if you want to test to make sure a remote file system is mounted, you'd have to do something else.

---

### Post by Dan_Joyce on 2013-08-22
Great advice all. I'll be messing with this extensively as soon as the file moves to my drive for testing. Love copying huge files....

Sadly, I have to have a solution that works between external drives. I'll read through this all and see if I can make that work with one of the tools recommended. The problem is they're on a pretty miserable DSL connection with terrible uploads that would probably take weeks or months to establish the first off-site backup and could take days as large files are changed. Hey, at least it isn't satellite like some of my clients. Can anyone think of another solution? Rotating external HDDs is all I can come up with. A couple large-ish SSDs would speed things up and as long as they had at least 3 plus a mirrored HDD in the box, I'd be pretty comfortable with that. Doubt they'll want to spend double on the SSDs though.

So, with this in mind, same suggestions? If at all possible a GUI the client can use would be fantastic. In fact, here would be my ideal. I mean ideal and realize all of this is unlikely:

What the client sees
One day each week the client would just pull one USB drive and plug in another. This would happen each week. That's what they'd have to know and all they'd need to know until/unless something goes wrong and we need a restore. At that time I'd have given the client a boot disk to put in the optical drive that would ask for the external HDD with the latest backup and it would be back to working a while later. 

What I need to do/think about
I realize to do that I'd need incremental backups that could recognize states of various drives -- one would be weeks behind and rsync or similar would have to look at a config/status file to know the last backup on that specific drive. So, the first day a backup drive is swapped the incremental backup would be different by a few weeks. It would back up daily for a week and the next would be rotated.

I'd like to know more about the Ubutnu core and apps and data backups separate. Specfically, I'd like to know how a restore could be simplest for my client. In the end, if it would require me doing the restore, that's fine too. I could reinstall Ubuntu then restore their data if the other is impossible or overly-complicated

As for different partitions, that's not currently the case. This was set up for them a long time ago by someone else. They're running a webserver (Apache, MySQL, PHP) for SugarCRM and file sharing out to Windows and Mac OS clients. So, SMB server. We may be either ditching Sugar or moving it around anyway, so now would be a good time to do this right, but I doubt they'll go for it. Trying to do the best I can with what I have now. Weekly backups using Tar are good enough if they can be restored, but something better would be great. 

Hopefully that info explains what they're doing better. Nothing fancy. No DHCP server, no domain. Just Sugar and files.

---

### Post by TheFu on 2013-08-23
If you are backing up a DB, you need to take extra steps to ensure non-corrupt backups.

I don't think I can help anymore in this forum than what I've said already or what my signature links provide. 

If you'd like more help, PM me.

---

### Post by Dan_Joyce on 2013-08-23
> **TheFu said:**
> If you are backing up a DB, you need to take extra steps to ensure non-corrupt backups.

I don't think I can help anymore in this forum than what I've said already or what my signature links provide. 

If you'd like more help, PM me.

Thanks. I'm reading through all this and have a big hill to climb. I spent most of my time yesterday trying to copy one of the backup files to my own drive so I can return the client's. Sadly, Virtualbox will only copy up to about 1.5MBps, making a single move tens of hours. I used an ext plug-in for Windows to copy but every time I copy one of the 100gb files they end up stopping just over 40gb. 

So long as I know the backups are working I don't necessarily need one. My goal now is to run a restore just so I can tell them their backups work. I'm doing that using instructions here: [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR) 

You're right that I'll have to back up that database seperately. I hadn't thought about that. If it's not already I can just install PHP MyAdmin and back that up as well. I'm sure I'll find plenty of ways to script that online.

Again, thanks for all the info and links. I plan to read a bunch of that as soon as I'm able.

BTW, I have a portable HDD I can use to get a copy of the backup from my client directly from their server. It's currently NTFS. Copying the backup file to it isn't a problem in any way, is it? Or, do I need to reformat the drive to EXT?

Thanks again.

---

### Post by Dan_Joyce on 2013-08-23
I just found out they still access the server while is't running the backup. Will that screw things up? It should probably back up at night while they're away, right?

---

### Post by TheFu on 2013-08-23
> **Dan_Joyce said:**
> Thanks. I'm reading through all this and have a big hill to climb. I spent most of my time yesterday trying to copy one of the backup files to my own drive so I can return the client's. Sadly, Virtualbox will only copy up to about 1.5MBps, making a single move tens of hours. I used an ext plug-in for Windows to copy but every time I copy one of the 100gb files they end up stopping just over 40gb. 

So long as I know the backups are working I don't necessarily need one. My goal now is to run a restore just so I can tell them their backups work. I'm doing that using instructions here: [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR) 

You're right that I'll have to back up that database seperately. I hadn't thought about that. If it's not already I can just install PHP MyAdmin and back that up as well. I'm sure I'll find plenty of ways to script that online.

Again, thanks for all the info and links. I plan to read a bunch of that as soon as I'm able.

BTW, I have a portable HDD I can use to get a copy of the backup from my client directly from their server. It's currently NTFS. Copying the backup file to it isn't a problem in any way, is it? Or, do I need to reformat the drive to EXT?

Thanks again.

I know a little about virtualbox - give presentations on improving the performance at different groups in the US and a few other countries. [See this]("http://www.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox").  You should see 80-95% of the native performance for disk, networking and CPU on a properly tuned VM.  Anyway, virtualbox is NOT a good choice for server-on-server virtualization, but should be fine to test a server restore. VirtualBox is meant for Desktop-on-Desktop VMs. 

USB2 is slow.  USB3 has queuing issues with every use I've ever seen - too many different processes seems to confuse the USB bus - sometimes I see ZERO bytes transferred for 20+ seconds if more than 2 processes attempt to use USB storage.

Tar retains user, group and simple permissions, but the VM where you restore needs to have 100% matching /etc/passwd files or the file permissions will be all screwed for non-system accounts. That could be bad.  **Tar really is a terrible choice for your backups, they are too large. Seriously. **You have too much data for tar to be effective. On my servers, I see less than 50MB of change data daily, so pushing backups to a remote system is almost nothing even over slow DSL with a smarter backup tool.  Definitely do the first backup local, then take that disk to a remote location and let the magic of incrementals help.  It will also mean less downtime for the backups to happen.  

For 100G source, I'd estimate less than 120G would be needed for 60 days of backups using rdiff-backup. Obviously, the amount of change data matters, so this is just a guess.  For all the other backup methods except duplicity and tools based on it, you will want a Linux file system - NOT NTFS.  Sorry, but it is just an inferior file system for Linux backups.

Forget the GUI. Those are a huge liability to server stability.  Think PowerShell - which is based on **bash**.

---

### Post by TheFu on 2013-08-23
> **Dan_Joyce said:**
> I just found out they still access the server while is't running the backup. Will that screw things up? It should probably back up at night while they're away, right?

If the DB server is running, then the DB is open and the data is NOT in a known, stable, state. Corruption can happen. You have 2 choices to solve that issue.

---

### Post by Dan_Joyce on 2013-08-23
> **TheFu said:**
> I know a little about virtualbox - give presentations on improving the performance at different groups in the US and a few other countries. [See this]("http://www.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox").  You should see 80-95% of the native performance for disk, networking and CPU on a properly tuned VM.  Anyway, virtualbox is NOT a good choice for server-on-server virtualization, but should be fine to test a server restore. VirtualBox is meant for Desktop-on-Desktop VMs. 

USB2 is slow.  USB3 has queuing issues with every use I've ever seen - too many different processes seems to confuse the USB bus - sometimes I see ZERO bytes transferred for 20+ seconds if more than 2 processes attempt to use USB storage.

Tar retains user, group and simple permissions, but the VM where you restore needs to have 100% matching /etc/passwd files or the file permissions will be all screwed for non-system accounts. That could be bad.  **Tar really is a terrible choice for your backups, they are too large. Seriously. **You have too much data for tar to be effective. On my servers, I see less than 50MB of change data daily, so pushing backups to a remote system is almost nothing even over slow DSL with a smarter backup tool.  Definitely do the first backup local, then take that disk to a remote location and let the magic of incrementals help.  It will also mean less downtime for the backups to happen.  

For 100G source, I'd estimate less than 120G would be needed for 60 days of backups using rdiff-backup. Obviously, the amount of change data matters, so this is just a guess.  For all the other backup methods except duplicity and tools based on it, you will want a Linux file system - NOT NTFS.  Sorry, but it is just an inferior file system for Linux backups.

Forget the GUI. Those are a huge liability to server stability.  Think PowerShell - which is based on **bash**.

Fantastic advice. My client is worried about changing anything at all. In fact, they retrieved their backup drive because they don't want to switch the steps from : Mount external / run Tar creating the archive on the server / copy to external / unmount / delete archive --- to --- run Tar / mount drive / copy to drive / unmount / delete archive. Seriously. 

So, my primary concern is to be sure what they have does actually work. At the same time I'm sitting down with them today to retrieve a backup on my own disk so I can attempt a restore as well as talk them into using a better system, possibly off-site. The more I think about it the more I think you're right that an off-site backup could work. I'd want a local disk left attached there at all times backed up incrementally and a remote disk (S3?) incrementally, nightly. That first backup will be torture though at ~400kbsp upload. Any magic advice there?

In your opinion is this a good strategy and cost effective? They're looking at switching CRMs so I think I'll push them to a hosted solution there and maybe switch to just a simple NAS for file storage. Then I could have the NAS back up to S3 and to a local HDD or they could just cycle HDDs off-site if they want. The CRM database would be handled and all would be well. Please tell me if you think this is the right direction.

As background, someone else set this Ubuntu server up for them and they've never done anything with it but use it and follow his Tar instructions. He did not provide restore instructions and they've never known if the backups even work. They are so nervous about it all they don't update Ubuntu or Sugar and just hope things don't break. They actually thought if the server went down they could just plug in this external drive and reboot. I'm working for them now and know enough to get it doing with some advice.

Thanks you, thank you, thank you.

---

### Post by Dan_Joyce on 2013-08-23
TheFu,
Thank you again for all your help. I'm meeting with the client today when they've completed their daily backup so see if I can get myself a copy of that file. I'm a bit nervous about mounting my drive on their server and copying directly from their backup drive, but don't see other options. Virtualbox will only copy at ~1.5MBps for me, so that's not really an option through my laptop. 

Is there any reason I couldn't let them keep doing what they do now and set a separate process up for a nightly backup using one of the tools you mentioned in your first post? Then I can handle that database any way I want, whether it be exporting the database separately or shutting down PHP/MySQL/Apache as necessary then restarting them after. I'll read a lot more about this -- and probably have a lot more questions -- after I meet with them. Good news is I can test all of this on my own server and need to set up a backup strategy for it that would be very similar. So much better having a low-risk environment to test.

---

### Post by SeijiSensei on 2013-08-23
That RAID1 mirror you mentioned initially would be a good start.  If you use the RAID code in the kernel to set up an array with mdadm, both halves of the RAID1 can be separately booted in an emergency.  If your client wants to be able to pull a drive and replace it with a new one, I'd suggest investing in a hardware RAID card and "hot-plug" drive enclosures instead.  In a hot-plug set up, you can pull a drive from the operating array.  When the new one is inserted it is automatically included into the array.

[Hot-plug enclosures]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&Description=raid+hot+plug+drive+bay&N=-1&isNodeId=1")
[Assorted RAID controllers](http://www.newegg.com/Controllers-RAID-Cards/BrandSubCat/ID-1640-410?Order=REVIEWS)

---

### Post by Dan_Joyce on 2013-08-23
> **SeijiSensei said:**
> That RAID1 mirror you mentioned initially would be a good start.  If you use the RAID code in the kernel to set up an array with mdadm, both halves of the RAID1 can be separately booted in an emergency.  If your client wants to be able to pull a drive and replace it with a new one, I'd suggest investing in a hardware RAID card and "hot-plug" drive enclosures instead.  In a hot-plug set up, you can pull a drive from the operating array.  When the new one is inserted it is automatically included into the array.

[Hot-plug enclosures]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&Description=raid+hot+plug+drive+bay&N=-1&isNodeId=1")
[Assorted RAID controllers]("http://www.newegg.com/Controllers-RAID-Cards/BrandSubCat/ID-1640-410?Order=REVIEWS")

read my mind. This is my next set of questions. Today I looked at the machine. I backed up their SugarCRM database--PHPMyAdmin was already installed, so that was easy and I taught their person how for now. She'll do that every few days to her own machine. As for RAID 1. This machine is a standard HP Pavilion 6000 series. It's running a WD 1.5 TB Green drive, which worries me a bit. In short, not server hardware--cheap. They are totally on-board with setting up a reliable, daily backup including RAID1. The motherboard (H-Alvorix RS880) supports RAID1 already. 

My next questions were going to be whether to do software or hardware RAID and whether the first setup will cause data loss. I'll probably use clonezilla to create a clone to a backup drive first, but still want to know if I'll lose that data. 

Here are my current questions while I research rdiff-backup and whether it allows me to cycle external drives for an incremental backup:
[LIST=1]
[*]This hot-swap is interesting. What is the cost going to be, roughly? I'm thinking this might be overkill in this situation, but sounds sweet. I wish I knew they were running off a consumer machine before. I'll read up on these more, but would appreciate your thoughts as to whether they are worthwhile in this situation.
[*]WD Green drive: should I replace that and get two Reds, Blacks, or RE4s? I could then buy a cheap enclosure and turn that Green into one of the externals.
[*]RAID: do I need a controller or just use the AMD RAIDXpert? Or software RAID?
[/LIST]

Again, thank you all for your suggestions. Learning a ton as I go.

---

### Post by SeijiSensei on 2013-08-23
Based on the products I linked to, you're probably looking at $50-80 for the hot-swap enclosure plus the cost of the drives.  However I'd do some research on whether the onboard RAID controller supports hot-swap drives (or Linux for that matter).  My bet is the controllers on consumer-oriented machines probably don't.  A search for "[RAIDXpert linux hotswap](https://www.google.com/search?q=AMD+RAIDXpert+linux+hotswap)" didn't bring up much helpful documentation.

I don't have much if any experience swapping out drives using software RAID.  Usually I've shut down the machine entirely before changing devices.  Other people may be more knowledgeable about this than I.  You certainly can remove a drive from the command line using mdadm, but that isn't something I'd suggest to ordinary office workers.

---

### Post by Dan_Joyce on 2013-08-23
> **SeijiSensei said:**
> Based on the products I linked to, you're probably looking at $50-80 for the hot-swap enclosure plus the cost of the drives.  However I'd do some research on whether the onboard RAID controller supports hot-swap drives (or Linux for that matter).  My bet is the controllers on consumer-oriented machines probably don't.  A search for "[RAIDXpert linux hotswap]("https://www.google.com/search?q=AMD+RAIDXpert+linux+hotswap")" didn't bring up much helpful documentation.

I don't have much if any experience swapping out drives using software RAID.  Usually I've shut down the machine entirely before changing devices.  Other people may be more knowledgeable about this than I.  You certainly can remove a drive from the command line using mdadm, but that isn't something I'd suggest to ordinary office workers.

Oof, meant to remove the question about price as I saw your link after typing it out. 

The hot swap thing is interesting. Then they could leave one external on-site that gets daily incrementals and just have a couple hot-swappable drives that they cycle off-site. Easy. However, will the array know which one is old/new when they come back on-site? For instance, today I put disks 1&2 in and they mirror. Great. Now I remove 2 and put in 3. It would mirror from 1 to 3, right? Then a week later I bring back 2 that has week-old data and remove 3. When I put 2 in does it know 1 is still the authoritative drive? 

This means fewer cables, no expense on USB enclosures, etc. I think you're onto something. I'd still want my incremental in at least one location for those "oops" moments where something was deleted a month ago. Am I thinking about this all correctly? Eventually they want to use off-site for their incremental as well. This combo would be great.

Again, thank you.

---

### Post by TheFu on 2013-08-25
RAID is not a backup, it is for high availability only.  After all, when a software glitch or virus hits the box, any disks in the RAID will be corrupted "all together." That isn't any good.  For a cheap client like you have, they'd probably be better off using the "Google Model" - 2 cheap systems with a primary and a mirror. That way you get redundant storage, PSU, CPU, RAM, HDD, controllers, networking, cables, well, redundant everything, for the price of 2 cheap desktops.  If you compare the prices - 1 highly redundant server or 2 cheap desktops - it is very clear which wins by over $1000 - the 2 cheap desktops.

Backups - plan on a staged solution.
* Server to local storage ... full rdiff-backup.  No need to swap anything. Leave it connected all the time.  USB2 will be slow, but better than nothing. eSATA or USB3 work fine for backups. eSATA works fine for running OSes. A USB3 card and external dock - you want a dock - is $50 total. Look up the performance differences between USB2 and anything else. You really want something faster so your backups don't get system data from different timezones that was a joke, but if a backup takes too long, there are non-homogeneity risks to the data.
* removable storage that rsyncs from the rdiff-backup stuff.  This you can do weekly, monthly, and carry away.  You'll have the versioned backups off site this way, but also have extremely efficient transfers.

However, once you see how efficient rdiff-backup is with the client data, you may determine that rsync to a remove location overnight will work just fine. It is just the 1st rsync that will be huge.  The amount of extra storage used daily probably is almost nothing.

If there is financial data involved, please use encrypted storage for anything that is portable. HDDs can walk away easily. If it is encrypted, it doesn't matter as much.

---

### Post by CharlesA on 2013-08-25
> **TheFu said:**
> 
If there is financial data involved, please use encrypted storage for anything that is portable. HDDs can walk away easily. If it is encrypted, it doesn't matter as much.

+1. I've thought about encrypting my external backup drives in the past, but always run into the issue of how to provide the passphrase to decrypt them via script or even what encryption software to use.

I think the main reason I have stayed away from encryption is that is seems so.. intimidating, especially when I already have the backup scripts written up.

EDIT: I found [this]("http://askubuntu.com/questions/59487/how-to-configure-lvm-luks-to-autodecrypt-partition"), but I don't know how secure it would be.

---

### Post by TheFu on 2013-08-25
> **CharlesA said:**
> +1. I've thought about encrypting my external backup drives in the past, but always run into the issue of how to provide the passphrase to decrypt them via script or even what encryption software to use..

In 2 days, my partners had 2 smartphones stolen in Barcelona last year. Neither was password protected or encrypted and had almost full access to our internal network, their corporate email accounts, files, plus personal data.  Since then, I've started using as much encryption as possible.

[LIST]
[*]My netbook is fully encrypted. I don't keep anything on it at all. Wiped before leaving on a trip and after I return to ensure no leakage.
[*]My laptop doesn't leave the country, so it only has encrypted partitions for non-OS stuff.
[*]My servers aren't going anywhere - no encryption - not even my HOME. I may retink this in the future.
[*]My portable drives - some are encrypted others are not.  My goal is for all of them to be completely encrypted.  Anything that can walk off, needs to be encrypted.
[/LIST]

Some of my backups ARE on encrypted storage - the backup software doesn't know anything about it, just sees a file system. My goal is for all backup areas to be encrypted.

---

### Post by CharlesA on 2013-08-25
> **TheFu said:**
> In 2 days, my partners had 2 smartphones stolen in Barcelona last year. Neither was password protected or encrypted and had almost full access to our internal network, their corporate email accounts, files, plus personal data.  Since then, I've started using as much encryption as possible.

Ouch.

> [LIST]
[*]My servers aren't going anywhere - no encryption - not even my HOME. I may retink this in the future.
[*]My portable drives - some are encrypted others are not.  My goal is for all of them to be completely encrypted.  Anything that can walk off, needs to be encrypted.
[/LIST]

Some of my backups ARE on encrypted storage - the backup software doesn't know anything about it, just sees a file system. My goal is for all backup areas to be encrypted.

That's a good start. As it stands now, none of my backup drives or server are encrypted, but these are at my home, and if someone breaks in and steals things, I have bigger things to worry about than the loss of my data.

I think I have looked at LUKS or Truecrypt in the past, but gave up on it as I didn't want to test it on a production system at the time.

---

### Post by SeijiSensei on 2013-08-25
> **TheFu said:**
> RAID is not a backup, it is for high availability only.

RAID1 does work well for those that want to pull a drive out of the array every so often and store it as a backup snapshot.  Otherwise I entirely agree that RAID by itself is no substitute for backups.

---

### Post by Dan_Joyce on 2013-08-27
Hey all, I've been reading and testing and building a bathroom. So, less reading and testing than I'd like right now. But---

I finally was able to get a good copy of the TAR archive and unpack it, boot from it, etc. Seems to work. I'm spot-checking files now to be sure they contain data.

TheFu, I read back on some of your other posts. To be honest, I read a bunch for days back from my initial post and you could write a whole novel. Thanks for giving so much to the community. However, I hope I'm not asking things you answered. I sifted through finding the ones about backup and probably missed some. I apologize if I ask something you specifically answered. As for the second machine idea, that's good, but they won't go for it. I think in the near-ish future I can move them to something simpler anyway (NAS) when we move their CRM to the cloud. 

So, I've been looking into rdiff-backup and it looks promising. Very much so, in fact. I was also told I should consider using Clonezilla. Plus there's the RAID part. If you all don't mind, I'll run through my current thoughts and questions.

I'm going to move forward with RAID1 and rotated external drives. Those are nearly certain. Right now I'm thinking these two are best

1) RAID1 array. Though the hot-swap drives would be slick, I don't think they're worth the cost now. So, I'm thinking I'll replace that single WD Green drive with two either Reds or Blacks (or RE4s if I find a good deal) in RAID1. That way they have redundancy for a single drive failure. I'll just use the onboard RAID unless someone sees a good reason not to. 
    a) So, which drives should I use for internal? Red, Black, RE4? Any real reason to choose one over the other in this case? 
    b) What's my best way to configure the array initially? Pop out the live drive, put in the two new ones and configure the array, then use clonezilla from the old Green to the new ones? Is there a better way?

2) Incremental backup to external drives rotated weekly. They don't want an online backup yet, so I'm thinking 2-3 externals rotated off-site are fine. I haven't found any info saying rdiff-backup can or cannot handle this setup. My understanding of Clonezilla is that it would handle this fine, but I'd have tons of full clones like I do now, not incremental backups. Rdiff-backup looks like the winner here. But, I have questions.
    a) Can rdiff-backup handle multiple target drives rotated like this or will it get confused looking for old archives?
    b) is there any way for me to do an incremental that would keep all drives the same so that each successive week isn't missing from some drives?

Please tell me if I'm on the right track and if you could answer my four questions that would be great.

As always, thanks.

---

### Post by CharlesA on 2013-08-27
As far as drives go, I've been running [these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822236521") on my file server. When I bought them they were the same price as [WD Black drives]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822236424"). They are a little bit less now, but I mainly got them because they were NAS drives and built for RAID and came with a 5 year warranty as opposed to the 2 or 3 year warranty of other drives.

If you already have a RAID1 set up, you can remove one drive and put the new one in and tell the RAID software to rebuild it. It will take a long time, but it might not take as long as a bit-for-bit copy would (using dd).

As for your other questions, I don't know as I do not use rdiff-backup.

---

### Post by Dan_Joyce on 2013-08-27
> **CharlesA said:**
> As far as drives go, I've been running [these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822236521") on my file server. When I bought them they were the same price as [WD Black drives]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822236424"). They are a little bit less now, but I mainly got them because they were NAS drives and built for RAID and came with a 5 year warranty as opposed to the 2 or 3 year warranty of other drives.

If you already have a RAID1 set up, you can remove one drive and put the new one in and tell the RAID software to rebuild it. It will take a long time, but it might not take as long as a bit-for-bit copy would (using dd).

As for your other questions, I don't know as I do not use rdiff-backup.
Good tip. I've run the Reds, Blacks, and REs, but somehow didn't even know about the SE line in the middle there.

---

### Post by CharlesA on 2013-08-27
> **Dan_Joyce said:**
> Good tip. I've run the Reds, Blacks, and REs, but somehow didn't even know about the SE line in the middle there.

I found out about them from another forum member after looking into replacing the drives in my array after some issues with the SMART data.

If you want a headache, you can find the thread here:
[http://ubuntuforums.org/showthread.php?t=2157352](http://ubuntuforums.org/showthread.php?t=2157352)

---


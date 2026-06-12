---
title: "gzip and tar hang around and don't die.  Locks up my backup drive."
date: 2011-04-20
forum: Server Platforms
---

### Post by EarlsFurniture on 2011-04-20
Okay, so this is really the result of another problem.  There seems to be an issue with CPU spiking to 99% forever (until reboot) if I run apt-get or synaptic or update manager while an external USB drive is plugged in.  Note, other USB peripherals are no problem, just an external HD.

So my work around was to eject the drive when doing apt-get or other installation work, then reattaching it to remount.

Now, on to the present problem...

I'm using the basic backup script (the rotating one) found in the Ubuntu Server manual.  It uses tar and gzip to store a compressed version of the desired directories on my external USB. (which sits in a fire proof safe - this is for a business)

However, it seems tar and gzip which run nightly 6 days a week via cron as root, don't ever want to die, and they don't release the drive.  I have to reboot the system (I can't logoff) to release the drive, unplug it, the I can do update/install work.

Of course, if apt etc. would work fine without conflicts with the external device, I'd not care about the tar/gzip problem other than it generally isn't a proper way for them to function and it chews up some CPU cycles. (they run about 0.6 and 1.7 percent respectively)  I also can't kill them via kill or killall.  They seem undead.

Any ideas?

---

### Post by dtfinch on 2011-04-20
The first problem, in my experience, is a combination of sync() nowadays waiting for all writing to finish (rather than just writes that occurred before the sync, and for reasons unknown to me it's worse when there's a usb drive mounted), and dpkg calling sync() after every file it writes, rather than just once after the installation. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/624877](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/624877)

For the second problem, my best guess is that the fire safe external drive is formatted ntfs. We have several such drives (1.5 and 2gb iosafe drives). Our nightly secondary backups were taking 5+ hours, with 100% cpu usage in mount.ntfs (I think), using rsync which only updates files that actually change. When I reformatted them as ext3/4, backup times dropped to under 30 minutes. We're using 10.04.

---

### Post by EarlsFurniture on 2011-04-21
> **dtfinch said:**
> The first problem, in my experience, is a combination of sync() nowadays waiting for all writing to finish (rather than just writes that occurred before the sync, and for reasons unknown to me it's worse when there's a usb drive mounted), and dpkg calling sync() after every file it writes, rather than just once after the installation. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/624877](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/624877)

Yes, I've read the bug report.  But thanks for the link.  I'll keep an eye on it for solutions if any crop up.

> For the second problem, my best guess is that the fire safe external drive is formatted ntfs. We have several such drives (1.5 and 2gb iosafe drives). Our nightly secondary backups were taking 5+ hours, with 100% cpu usage in mount.ntfs (I think), using rsync which only updates files that actually change. When I reformatted them as ext3/4, backup times dropped to under 30 minutes. We're using 10.04.

Nope, it is formatted ext4.  And it takes 10 to 12 hours to backup about 10-20GB.  Checking my log, I see several days recently that started but never completed. My script writes a beginning and ending time stamp along with what is being backed up and a directory listing in between.  For the past few days, all I get are the beginning time stamps.  My guess is what is happening is that one is not finishing, and that is getting all hacked up when the next one starts.

I also forgot to mention that I also can't even access the drive while gzip and tar are hanging around.  I can [FONT=Lucida Console]cd[/FONT] to its location in [FONT=Lucida Console]/media[/FONT] but I can't do an [FONT=Lucida Console]ls[/FONT] on it.  I downloaded Bacula and intend to set that up, but it looks like I'll need a solid weekend of reading just to get up to speed on it, so I've put it off.

I'm not familiar with rsync.  Would that be a better solution than the tar/gzip combo, or are they essentially using rsync in the process?

---

### Post by dtfinch on 2011-04-21
Have you tried a different usb port? That sounds like it's running at USB 1.1 speeds (which caps out at 1.5 mb/s) instead of 2.0.

rsync doesn't compress the destination files, and it copies files individually, so it wouldn't be the same. I use it to copy modified files, while moving deleted files and previous revisions (using --delete and --backup-dir= options) to a second folder. For copying only modified files without the extra backup, something like "cp -au" would work as well.

We're backing up millions of files using over 1tb of space, so a tar backup would take a long time and wouldn't leave much room for past revisions. If your backups are a lot smaller, you might be better off with .tar.gz (or bzip2) and changing the filename according to the day of the week (like "backup`date +%u`.tar.gz") or month.

---

### Post by EarlsFurniture on 2011-04-21
I'll try a different port, but[FONT=Lucida Console] lsusb -v[/FONT] returns a [FONT=Lucida Console]bcdUSB[/FONT] of [FONT=Lucida Console]2.00[/FONT] so my guess is, it's a 2.0 port.  (this is a six month old eMachine, I think all the ports are 2.0)

In searching for how to find the port speed though, I found this: [http://brainstorm.ubuntu.com/idea/15648/](http://brainstorm.ubuntu.com/idea/15648/)

It looks like there is an issue with transferring large (GB+) files through USB.  That would explain why it takes so long to transfer, and why each day's backup starts tripping over the last one eventually.  (after a reboot, it works for a few days then I get this issue)

Right now, I think I'm 4 or 5 days nested with no completion, and from the looks of it, they'll never finish.  So reboot time it is.

I guess as a temp work around, I can break up the backup into smaller files (sub GB) rather than one large one and just dump it in a daily folder.  (I'm currently having the script name and rotate the backups by day of week, week of month as you mentioned)

Maybe I can find a way to incorporate rsync to lighten the backup size since it will only do changed files.

Short of a fix for the USB transfer problem and the aptitude problem, it looks like a more pared down backup till I can learn Bacula.

Thanks for your help and suggestions.

---

### Post by dtfinch on 2011-04-21
Is tar/gzip's cpu usage really high when it runs? "tar -czf ..." doesn't give you the option of controlling the compression level, and I've heard (but not confirmed) that it defaults to 9, the slowest. If you had tar output to stdout, and piped it to gzip or bzip2, you could specify a lower/faster compression level.

Edit/add: Excerpt from my home rsync backup script (I'm not at work now):
/usr/bin/rsync -rbutpog --delete --backup-dir=/store/past --modify-window=65 /home/david/Documents /store/backup >> /store/backup.log 2>&1
Backs up my Documents folder to /store/backup/Documents, saving one previous revision to /store/past/Documents.

On our backup servers, we also have something to keep several days of revisions. There are 30 folders named day1 to day30. Before each backup last/oldest folder is copied into a "veryold" folder and deleted (copy&delete because mv doesn't work for merging folders). Then it renames (mv) each day's revision folder to the next day, starting from the last.  Then a new day1 folder is created and passed in the --backup-dir rsync option.

---

### Post by EarlsFurniture on 2011-04-23
> **dtfinch said:**
> Is tar/gzip's cpu usage really high when it runs? "tar -czf ..." doesn't give you the option of controlling the compression level, and I've heard (but not confirmed) that it defaults to 9, the slowest. If you had tar output to stdout, and piped it to gzip or bzip2, you could specify a lower/faster compression level.

I'm not sure.  (it runs mon-sat at 11:59 pm when I'm not here) As I recall it didn't take long the first time I ran it as a test.  I'm not sure why when it runs automated it is taking so long.  I'll modify the script to backup a subset and see what happens.

> Edit/add: Excerpt from my home rsync backup script (I'm not at work now):
/usr/bin/rsync -rbutpog --delete --backup-dir=/store/past --modify-window=65 /home/david/Documents /store/backup >> /store/backup.log 2>&1
Backs up my Documents folder to /store/backup/Documents, saving one previous revision to /store/past/Documents.

Looks simple enough.  I'll try a version of that and see how that compares.

Thanks again for your help and suggestions.

---


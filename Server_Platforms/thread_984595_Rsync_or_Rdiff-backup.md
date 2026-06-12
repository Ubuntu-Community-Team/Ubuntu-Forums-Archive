---
title: "Rsync or Rdiff-backup?"
date: 2008-11-16
forum: Server Platforms
---

### Post by flip79 on 2008-11-16
Hello!

Currently I'm keeping a nightly backup of my web server files with Rsync: with crontab I synchronize files between the server (CentOS) and my "home server" (an old-fashioned Pentium III with Ubuntu server).

I just discovered that rdiff-backup makes, more or less, the same work, but it has incremental features, allowing me to recover the last version of the backup, or a previous one. Rsync is protecting me from disasters, but an incremental backup with... "time machine" features (see Apple :KS ) will protect me also from "human errors".

I'm asking if:
- does rsync can do incremental+differential backups?
- does rdiff work in ssh tunnels?

Thank you for answers!! :)

---

### Post by Philio on 2008-11-16
You could quite easily setup an incremental backup with rsync and the aid of a shell script so that prior to each backup the previous backup data was copied to another folder (with the previous backup date as the name), then the changes synced to the previous version. I'm not sure rsync can do a fully automated incremental backup on it's own though!

There are some nice backup programs out there that do things like mirror your entire drive (incrementally) on a daily basis so that in the event of a complete drive failure or something you can recover the enter drive to the exact state of the last backup. These are commercial products though and pricey.

I've no idea what Apple's time machine is but I assume it's something they ripped off from someone else and then branded as a 'revolutionary' new product like most of their product range :P

---

### Post by flip79 on 2008-11-16
> **Philio said:**
> I've no idea what Apple's time machine is but I assume it's something they ripped off from someone else and then branded as a 'revolutionary' new product like most of their product range :P

LOL! Ok, it's something that keeps trace of differences between directory contents and allow to "bring the clock back" to a certain date :)

The solution you suggest (use a scheduled command to copy the old backup in another directory, then syncronize the original) is ok, but it will require a lot of space... rdiff-backup creates service files in the backup directory where only changed files are stored, to recreate the files' structure in a specified date in the past (here's the similarity with apple's time machine). With this method, it reduces the space requirements at the minimum...

---

### Post by Philio on 2008-11-16
> **flip79 said:**
> LOL! Ok, it's something that keeps trace of differences between directory contents and allow to "bring the clock back" to a certain date :)

The solution you suggest (use a scheduled command to copy the old backup in another directory, then syncronize the original) is ok, but it will require a lot of space... rdiff-backup creates service files in the backup directory where only changed files are stored, to recreate the files' structure in a specified date in the past (here's the similarity with apple's time machine). With this method, it reduces the space requirements at the minimum...

So they copied System Restore off Windows? :)
Or maybe cvs/svn is a better comparism!

Back to the topic though, rdiff certainly sounds better, I've never actually used it personally. I was just suggesting this as a possible method with rsync, you could obviously improve things further by retaining backups for x number of days then clean them, zipping up folders etc but then if rdiff does incremental backups on it's own it would be a better solution.

---

### Post by psusi on 2008-11-16
I have read of people using rsync ot make daily backups with a little trickery.  Google for "rsync backup" and you should be able to find it.  The gist of it is that you copy yesterday's backup to a new directory, but you pass a switch to cp instructing it to hard link the files instead of actually copy them, that way it doesn't take up any more space.  Then when you rsync to today's copy, there was a switch to rsync to have it copy, unlink, and replace a file before it updates it so as not to modify the original copy still linked to by the previous directories.

That way you end up with a different directory for each day you back up that appears to contain all of your files as they existed that day, but it doesn't take up additional space for each day where a given file wasn't changed.  Then after a few days, you delete the oldest directory you don't want to keep any more.

---


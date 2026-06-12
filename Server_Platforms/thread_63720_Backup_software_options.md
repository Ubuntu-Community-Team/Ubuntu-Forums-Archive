---
title: "Backup software options"
date: 2005-09-08
forum: Server Platforms
---

### Post by mcewen98 on 2005-09-08
Does anybody have some recommendations for backup software?  I have seen rdiff-backup and backupPc, and neither seem to be what i'm looking for.   (Maybe I just havent' spent enough time looking at backupPc?)

I have a machine running ubuntu that I use for my home media server, web server(drupal), mythtv backend, etc etc... and I would also like to use it as my central backup machine for my network, consisting of 2 or 3 machines.  Each machine only has a couple of folders each to be backed up.

All I want is something with a gui that will backup local folders and shared samba network folders to an external hard drive.

I don't care about incrimental backups, copying files that have changed since the last backup is fine.  Removing files that no longer exist on the source directory would be even better.

Thanks,
Spencer

---

### Post by Nequeo on 2005-09-08
[QUOTE=mcewen98]Does anybody have some recommendations for backup software?  I have seen rdiff-backup and backupPc, and neither seem to be what i'm looking for.   (Maybe I just havent' spent enough time looking at backupPc?)

I have a machine running ubuntu that I use for my home media server, web server(drupal), mythtv backend, etc etc... and I would also like to use it as my central backup machine for my network, consisting of 2 or 3 machines.  Each machine only has a couple of folders each to be backed up.

All I want is something with a gui that will backup local folders and shared samba network folders to an external hard drive.

I don't care about incrimental backups, copying files that have changed since the last backup is fine.  Removing files that no longer exist on the source directory would be even better.

Thanks,
Spencer[/QUOTE]
 I don't have anything with a GUI... but if you want a backup script you can configure once, schedule to run nightly (or whenever), and then just leave alone and let it do its thing, I've got a script I can give you and help configure.

Basically you just fill in the folders you want to back up (recursively), the location you want to back up to, and how many old backups you want to keep. Optionally, it can also check free disk-space and e-mail you if it doesn't look like there will be enough - and e-mail you the output of the backup-job.

It doesn't do incremental backups, or even comparative backups. It does a full dump of every directory you name. 

The only catch is that you will have to mount your SAMBA shares locally using CIFS or SMBFS, but this is a trivial step that any of us could talk you through if you encountered problems.

In any case, it's absolutely free and only requires you to download one teeny file. If you wanna give it a shot, just let me know.

Cheers,

---

### Post by kevcool on 2005-09-09
[QUOTE=mcewen98]Does anybody have some recommendations for backup software?  I have seen rdiff-backup and backupPc, and neither seem to be what i'm looking for.   (Maybe I just havent' spent enough time looking at backupPc?)

I have a machine running ubuntu that I use for my home media server, web server(drupal), mythtv backend, etc etc... and I would also like to use it as my central backup machine for my network, consisting of 2 or 3 machines.  Each machine only has a couple of folders each to be backed up.

All I want is something with a gui that will backup local folders and shared samba network folders to an external hard drive.

I don't care about incrimental backups, copying files that have changed since the last backup is fine.  Removing files that no longer exist on the source directory would be even better.

Thanks,
Spencer[/QUOTE]
 I do this at my place with rsync to backup to both local and remote folders - both to and from Windows.  If you install cygwin on the windows machine, you can rsync to a directory on the server and you don't have to worry about using samba or nfs.  It will simply sync the files that are new or have changed.

You can also sync from a Linux machine to a remote Windows machine.  I use a script like this:

#!/bin/bash
# Nightly script to sync to a remote computer
#
rsync -av -e "ssh -i /home/<someuser>/rsync-key" /some/local/path/ user@machine:/cygdrive/j/somepath/

I use an ssh key so the script can be automated with cron.  Otherwise you'll simply need to enter a password.

Of course you can do the same from Windows to Linux - again, providing cygwin is installed (easy).

- Kev

---

### Post by mcewen98 on 2005-09-09
Thanks for the suggestions.  I'de like to avoid something that does a full dump of the directories to be backed up, every time it is executed.  All I want is a single copy of the up to date files, replacing only modified or new files.

I am surprised there is nothing for free (with a gui) out there that does this.  Even something like Iomega's free backup program for windows that comes with it's external drive's would be fine.

If I had the time, I think even I could write a little java app, triggered by cron, to do this.  Wouldn't all you need to do is check either the timestamp or md5 checksum of the file, and if it doesn't match re-copy the file?

Kevcool, I think i'll end up probably looking more into rsync

Thanks again,
Spencer

---

### Post by mcewen98 on 2005-09-09
I just did some searching and found this site, which seems to have a ton of backup scripts:

[http://www.linux-backup.net/App/](http://www.linux-backup.net/App/)

---

### Post by mcewen98 on 2005-09-09
I also found this, [http://lrs.linbox.org/wiki/FileBackup](http://lrs.linbox.org/wiki/FileBackup)

which uses backupPc, but provides an interface to the configuration file.

---

### Post by strikeforce on 2005-09-09
rsync could be a possibility.  I do two types of backups. 1 full compressed backups of the required files that I need.  Another one is that I rsync to another harddrive all the latest files and changes.

rsync might be your option.

---

### Post by LordHunter317 on 2005-09-09
For actual backups though, rsync is silly and won't do what he wants.

Why do people keep continually suggesting rsync when **the OP** mentioned rdiff-backup?

Scripting something off rdiff-backup is my solution.  There's no GUIs because it's literally a one-line cron job for most setups.

---

### Post by lao_V on 2005-09-09
[QUOTE=LordHunter317]
Why do people keep continually suggesting rsync when **the OP** mentioned rdiff-backup?
[/QUOTE]

Maybe because the op said this:

  [QUOTE=mcewen98]
I have seen rdiff-backup and backupPc, and neither seem to be what i'm looking for. (Maybe I just havent' spent enough time looking at backupPc?)[/QUOTE]

---

### Post by LordHunter317 on 2005-09-09
Yes, but the point is, rdiff-backup does everything rsync does, but does it better, so.... if rdiff-backup is an inadequate solution, then rsync must also be inadequate, because it's included in rdiff-backup.

---

### Post by mcewen98 on 2005-09-09
Thanks for the replys.  So does somebody have an rsync example to copy a folder from a samba share?

Also, I want to exclude a specific sub directory from the directory being backed up.   Any suggestions?

Thanks again

---

### Post by LordHunter317 on 2005-09-10
It would be something like:```
rsync -a --exclude='bar' /local/dir example.com:/remote/dir
```But understand, using rsync means you can only get back the latest copy of what you had (it doesn't perserve backups in any way, shape, or form).  If that's all you need, that's fine, otherwise, you should use rdiff-backup which has almost identical syntax, uses rsync internally, and can keep backups around.

---

### Post by mcewen98 on 2005-09-10
That's simple.  I was playing around with mounting some smb shares in ubuntu from my windows machine.  I got it to mount fine and put it in /etc/fstab, but  ubuntu didn't seem to like it when I mounted the share, shut down the pc, then turned it back on again.  In fact, Ubuntu got really unresponsive when that happened, so it looked like it wouldn't automatically remount the share.

Since ubuntu will be on all the time, and the pc's to be backed up will be on and off inbetween backups, I don't see how this will work.

Any suggestions, or should I go the SSH and encryption key route, so that no login is needed?

---

### Post by mcewen98 on 2005-09-10
I"ve been doing some thinking.  I'm wondering if having my clients push to the ubuntu server would be better then having the server do a pull from all the clients.  One of the clients I want to backup is OSX, and there is rsyncx which looks hopeful, for that.

Then I wouldn't have to worry about mouning and unmounting samba shares from all over the place.  I would just create a writable share on the server, then have OSX and rsyncx on the mac, and have the iomega app on the pc, push to a mounted samba share located on the server.

---

### Post by LordHunter317 on 2005-09-10
[QUOTE=mcewen98 I got it to mount fine and put it in /etc/fstab, but  ubuntu didn't seem to like it when I mounted the share, shut down the pc, then turned it back on again.[/quote]If Ubuntu paniced, something is amiss.  Post what you did to mount the share.

> Since ubuntu will be on all the time, and the pc's to be backed up will be on and off inbetween backups, I don't see how this will work.This is a push scheme can be superior, perhaps.  If you're willing to install cygwin on windows both rsync and rdiff-backup can be made to work.

> Any suggestions, or should I go the SSH and encryption key route, so that no login is needed?I'm confused... even if you use keypairs they still have to have an account to login to on your backup machine, they just cannot get a shell.

---

### Post by mcewen98 on 2005-09-10
[QUOTE=LordHunter317]If Ubuntu paniced, something is amiss.  Post what you did to mount the share.

This is a push scheme can be superior, perhaps.  If you're willing to install cygwin on windows both rsync and rdiff-backup can be made to work.

I'm confused... even if you use keypairs they still have to have an account to login to on your backup machine, they just cannot get a shell.[/QUOTE]

Sorry for the lack of clarity.  First about the samba share problem.  I created a file share on my windows XP machine, and mounted it on the Ubuntu machine using "sudo mount -t smbfs .... -o username=xxx,password=xxx".  The problem I had was when I shut down the XP machine, then tried to access the share in Ubuntu (ls /mnt/share), the entire OS hung badly.  When I turned the XP machine back on, it did not remount automatically and I eventually ended up rebooting ubuntu.

Therefore, since the XP desktop and OSX laptop will constantly be on or off (and maybe causing mount problems), I think it will be better to have them push the files to the ubuntu machine (which will always be on with the backup directory shared), rather than ubuntu pull the files from from the 2 clients.  Maybe the mounts should automatically become re-established? I don't know... but the push rather then pull seems to make more sense to me.

The backup directory in ubuntu is just a samba share. I have XP and OSX automaticlly establish their connection to that directory on startup.

I thought my other alternative would be to use a keypair so that Ubuntu could automatically log into the XP and OSX machines to grab the files.  Doing the push, rather than pull, I dont need to worry about this either.  And yeah, I realize an account would be needed, which would have been fine.

The Iomega automatic backup software, which came with the 40gb external usb2 drive that I use to store the backups is pretty good.  It seems to work fine and supports scheduling, revisioning, etc.  For OSX, rsyncx looks pretty good too.  For files that i'm backing up on Unbuntu itself, I'll just use rsync.  

I can't think of any negatives to doing it this way. 

Spencer

---

### Post by LordHunter317 on 2005-09-10
[QUOTE=mcewen98]Sorry for the lack of clarity.  First about the samba share problem.  I created a file share on my windows XP machine, and mounted it on the Ubuntu machine using "sudo mount -t smbfs .... -o username=xxx,password=xxx".[/quote]Don't use smbfs, it's broken under 2.6.  Use CIFS instead (-t cifs).  For mounting Windows boxen, it's identical.  For Samba boxen, it behaves like NFS.

> The problem I had was when I shut down the XP machine, then tried to access the share in Ubuntu (ls /mnt/share), the entire OS hung badly.Yeah, mounted shares don't like to have the remote end ripped out underneath them.  This is true regardless of protocol.

One easy solution to that is autofs, which can be rigged to cause automatic unmounting after a specified period of inactivity.

> I can't think of any negatives to doing it this way.For me, essentially only have the most current data would be a big negative.  I highly recommend you write a script to tar up the files in the share periodically so you can store them off machine.

---

### Post by mcewen98 on 2005-09-10
[QUOTE=LordHunter317]
For me, essentially only have the most current data would be a big negative.  I highly recommend you write a script to tar up the files in the share periodically so you can store them off machine.[/QUOTE]

Ah, I did not know that about smbfs.  If it's broke, why leave it in?

For me, only having a copy of the current data is fine.  If these were mission critical or business related files then I would want some revisioning.  But these are just my personal files, most of which rarely change all that much.  Most likely, just new files will be added, such as pictures and things like that.

If I did want to do revisioning, the Iomega backup application on my PC supports it, and I could always use rdiff-backup instead of rsync for the local ubuntu files.  I'm not sure what rysncx supports, but it looked pretty robust.

Spencer

---

### Post by LordHunter317 on 2005-09-10
[QUOTE=mcewen98]Ah, I did not know that about smbfs.  If it's broke, why leave it in?[/quote]Because CIFS can't do everything it can do yet, and not all servers can talk CIFS.

---

### Post by jmsullivan73 on 2005-09-14
I was looking at doing this also.  You might like to check out rsnapshot...

Good Luck.

---


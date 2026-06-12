---
title: "Backup with tar"
date: 2010-08-28
forum: Server Platforms
---

### Post by scorchgeek on 2010-08-28
I've been trying to back up my system to a tarball for quite a while now. I recently bought a tape drive, and it works. But I'm having a little bit of trouble getting tar to work--whenever I try to copy the files (either directly to the drive at /dev/st0 or to a tarball), I end up with a "file changed as we read it" error, and tar quits before the archive is done.

Is there some way I can either prevent this from happening and/or tell tar to just skip that file and keep the job going?

```

$ cd /home
$ sudo tar -czf /dev/st0 soren {soren being my home directory, /dev/st0 the tape drive}
[sudo] password for soren: 
tar: soren/.gvfs: Cannot stat: Permission denied
tar: soren/.local/share/Trash/files/From Removable Media/16GB Flash Drive Dump/Cliffs of Incognita/Cliffs of Incognita Music/Audio/Stereo 01_01.wav: File shrank by 7289884 bytes; padding with zeros
tar: soren/.local/share/akonadi/akonadiserver.socket: socket ignored
tar: soren/.config/google-chrome/SingletonSocket: socket ignored
tar: soren: file changed as we read it

$ sudo tar -df /dev/st0 soren {diff between the archive and homedir}
[sudo] password for soren: 
soren/.cache/ubuntuone/log/syncdaemon.log: Mod time differs
soren/.cache/ubuntuone/log/syncdaemon.log: Size differs
soren/.cache/gwibber/facebook-sorenbjornstad_friends.cache: Mod time differs
soren/.cache/gwibber/gwibber.log: Mod time differs
...

```

---

### Post by minigeek on 2010-08-28
Hi 

Try the following

```
sudo tar -df /dev/st0 soren > /dev/null 2>&1
```
:)

---

### Post by scorchgeek on 2010-08-28
> Hi 

Try the following

Code:
sudo tar -df /dev/st0 soren > /dev/null 2>&1


Correct me if I'm wrong, but it seems to me that that code will do nothing more than get rid of the error messages, without fixing the problem. 

Also, the second command wasn't to back up, rather to check if the backup had completed successfully. (The d option checks the archive against the original without actually copying anything.)

---

### Post by BkkBonanza on 2010-08-28
That just hides the problem by sending warnings away.

Your problem here is that the files **are** changing while the tar program is archiving them. This is typical of logs that get continuously updated, and database files if a database is active. Ideally backups are done when the system is not doing anything else that could affect them.

Another approach is to snapshot the affected files and then back up those. By snapshot I mean make a duplicate copy before the tar command. For databases (likely not your issue) it requires more thought but can also be done. 

You have warnings concerning cache files for UbuntuOne. So dare I say, stop any programs that are monitoring/accessing that while a back up is in progress.

Also in your tar command you may want to add an **--exclude** for any paths that give permission troubles or just don't make sense to backup. eg. You cannot backup open sockets.

---

### Post by scorchgeek on 2010-08-28
Would there be an easy way to shut down all the programs that might cause a file to change, then? --exclude on a couple of them sounds like a good idea, but I would like to get my config files on the backup somehow.

---

### Post by BkkBonanza on 2010-08-28
config files in /etc should be fine as they rarely change.
but you may want to exclude .cache directories and any tmp paths
sockets are ignored anyway so not really a problem
(sockets are like pipes for inter-program communication, can't be backed up)

As far as shutting down programs... well, sometimes admins will change runlevels to do a backup in single user mode, and then change back. That is pretty disruptive though. 

You could script certain programs to shutdown and then start them after. Usually you would do this by sending signals with kill or **pkill** but it has to be well thought out.

Regarding UbuntuOne specifically, I don't use it, you would have to check the doc on it's monitoring. Maybe it supports a signal to "pause" and "resume", or maybe just kill and start it again.

---

### Post by scorchgeek on 2010-08-29
Thanks for the ideas--I managed to get a valid backup last night, and I'll be considering everything you said as I try to get it on a schedule.

---


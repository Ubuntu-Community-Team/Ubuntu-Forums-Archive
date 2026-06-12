---
title: "Rsync error Mkdir Failed"
date: 2007-11-01
forum: Server Platforms
---

### Post by cjbujold on 2007-11-01
I keep receiving the following error:

2007/11/01 11:53:41 [3352] rsync: mkdir "/home/administrator/MyBackups/Home/Program" failed: No such file or directory (2)

How can i correct ir I'm using Ubuntu 7.10

Thanks

---

### Post by MJN on 2007-11-01
Does it only happen occasionally, and for certain parts of the backup (i.e. the rest of the backup goes okay)? If so, it sounds like it could be a disk issue - what's the destination drive? A Windows share, NAS, USB disk etc?

What's your rsync command? And how are you running it?

Mathew

---

### Post by cjbujold on 2007-11-01
It happens on the first directory, everytime. the full directory does not exit on the server ("/home/administrator/MyBackups" does exist).  the server is ubuntu 7.10.

The server has 3 disk drives, two ext3 and one NTFS.  The disk drive  I'm backing up to is Linux drive (ext3).  I will try saving it to a secondary drive, to see if it makes a difference.

The rsync comand is run via cwrsync on a Windows XP .  The command is:
rsync -avizo  --progress --stats --delete --log-file=backupLog.rtf -e  'ssh.exe -p 3010 -c blowfish-cbc'  /cygdrive/C/Home/gebtax07'backupopt@backup.accrads.com:MyBackups/Monday/home/gebtax07'

I can ssh to the the system and create a single directory without errors.

Any suggestion would be appreciated.

---

### Post by MJN on 2007-11-02
I think that's your problem - the intermediate directories of the destination path do not exist on the server. Try creating the full path manually, or shrinking the rysync command to a higher level, and rerunning.
 
It might be worth also using the full path (i.e. from /) as the destination portion of the rsync command.
 
Having said all that your paths don't seem to match up anyway - your first post mentions "/home/administrator/MyBackups/Home/Program" yet your rsync command has the destination "MyBackups/Monday/home/gebtax07'' - even ignoring the parent levels the child domains aren't the same (Home != home, Program != gebtax07).
 
Mathew

---


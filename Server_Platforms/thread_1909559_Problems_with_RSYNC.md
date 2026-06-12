---
title: "Problems with RSYNC"
date: 2012-01-15
forum: Server Platforms
---

### Post by bubylou on 2012-01-15
buby@Bubylou:~$ rsync -rvz /Share /mnt/Backup
sending incremental file list
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: ERROR: cannot stat destination "/mnt/Backup": Cannot allocate memory (12)
rsync error: errors selecting input/output files, dirs (code 3) at main.c(583) [Receiver=3.0.8]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.8]

/Share is samba share dir containing videos, pictures, and music.
/mnt/Backup is a shared folder on another machine that i mounted.

i want to be able to do the occasional backup of all my shared files on the server to another computer for a backup.

---

### Post by papibe on 2012-01-15
Could you post the result of these commands?
```
mount -l

df -h
```
Regards.

---

### Post by bubylou on 2012-01-15
turns out it was my windows machine giving me problems. a few reg edits and it works fine now. i do have one question though i started the back but it appear to be backing up data locally as well as on the windows machine which led to me running out of disk space on the server. any help on what i did wrong.

---


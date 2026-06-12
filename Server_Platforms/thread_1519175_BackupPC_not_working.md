---
title: "BackupPC not working"
date: 2010-06-27
forum: Server Platforms
---

### Post by JKyleOKC on 2010-06-27
I'm trying to set up a unified backup system for my home office LAN, which consists of three Xubuntu boxes running Hardy 8.04.4 and one Win98SE box that's my fax receiver. I've installed BackupPC via Synaptic on the box with the most file space, following the instructions in "The Official Ubuntu Server Book." Initially, I'm only backing up "/etc" from the three Xubuntu boxes, using tar as the Xfer method. However, it's not working.

Here's the complete error log from the most recent attempt at localhost:
```
Running: /usr/bin/ssh -q -x -n -l backuppc localhost sudo env LC_ALL=C /bin/tar -c -v -f - -C /etc --totals --newer=2010-06-27 08:56:28 .
incr backup started back to 2010-06-27 08:56:28 (backup #0) for directory /etc
Xfer PIDs are now 26333,26332
Tar exited with error 65280 () status
tarExtract: Done: 0 errors, 0 filesExist, 0 sizeExist, 0 sizeExistComp, 0 filesTotal, 0 sizeTotal
Got fatal error during xfer (Tar exited with error 65280 () status)
Backup aborted (Tar exited with error 65280 () status)

```

I can connect to a second box using ssh, and its error messages are slightly different:
```
Running: /usr/bin/ssh -q -x -n -l backuppc mehitabel sudo env LC_ALL=C /bin/tar -c -v -f - -C /etc --totals .
full backup started for directory /etc
Xfer PIDs are now 27977,27976
[sudo] password for backuppc: 
tarExtract: Done: 0 errors, 0 filesExist, 0 sizeExist, 0 sizeExistComp, 0 filesTotal, 0 sizeTotal
Got fatal error during xfer (No files dumped for share /etc)
Backup aborted (No files dumped for share /etc)
```

I'm at a loss as to where to look next, and while the BackupPC documentation (and the book's instructions) are quite good for doing the installation and initial configuring, they seem to be totally silent when it comes to troubleshooting!!!

Suggestions, anyone???

EDIT: Got one response over on the BackupPC mailing lists that led me to the solution; posting here in case someone else has a similar problem. It turned out to be a question of permissions all around. Creating the backuppc user on the two client boxes automatically created a password of some sort despite my telling it not to. Deleting the passwords via passwd -d on each box made it possible to connect. Then discovered that my edit of the /etc/sudoers file to allow the daemon to use sudo with no password was a bit dicy. When that was corrected, everything began working...

---


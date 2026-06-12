---
title: "Backuppc failing"
date: 2008-12-18
forum: Server Platforms
---

### Post by happyhacker on 2008-12-18
I've gone through all the How-tos and googled but I cannot get backup PC to successfully run. I am using the smb method and trying to setup a test method from my laptop I use to configure the server (8.10). I have removed the "-N" flag from the backuppc config. file SmbClientFullCmd, etc. of the Smb paths/commands section as I noted this was a Ubuntu bug on the web somewhere. The result log I get is:

2008-12-18 14:12:06 Got fatal error during xfer (No files dumped for share adminDocuments)
2008-12-18 14:12:44 Backup aborted (No files dumped for share adminDocuments)

But that seems pretty unuseful!

I can ping my laptop with it's smb name so I'm pretty sure everything is in place. And I have added the user to the XP backup group.

Any advice appreciated.

Any advice

---

### Post by happyhacker on 2008-12-22
Further trials with this is that if I type:

smbtree -b into the server command line all I get out is a workgroup of "HOME" which I do not have! I do NOT see my workgroup and connected machines.

Is this a red herring or has something not been setup properly in Samba to get backuppc working for SMB method of backup?

---

### Post by Zeosa on 2008-12-23
Probably a long shot, but try disabling XP's built in firewall for testing....just in case (I know it blocks smb requests by default)

---

### Post by eL_vErDe on 2008-12-23
You're not looking at the right log file.
This looks like being BackupPC main log file. Check the XferLog or XferLogBad for this client.

---

### Post by happyhacker on 2009-01-03
Below the log for this case. It does not give much clue as to the real problem. Advice appreciated.

Contents of file /var/lib/backuppc/pc/lt7/XferLOG.bad.z, modified 2008-12-22 16:17:16 

Running: /usr/bin/smbclient \\\\lt7\\acdoruser -U ACDorUser -E -d 1 -c tarmode\ full -Tc -
full backup started for share acdoruser
Xfer PIDs are now 11419,11418
tarExtract: Done: 0 errors, 0 filesExist, 0 sizeExist, 0 sizeExistComp, 0 filesTotal, 0 sizeTotal
Got fatal error during xfer (No files dumped for share acdoruser)
Backup aborted (No files dumped for share acdoruser)
Not saving this as a partial backup since it has fewer files than the prior one (got 0 and 0 files versus 0)

---

### Post by happyhacker on 2009-01-07
I've now installed rsync both ends. Backuppc now reports that the client has timed out. This may be slight progress but I still have not got backuppc working. I thought I would try a bit longer before I give up and uninstall it. Can anyone advise how I can find out why it's timing out?

---


---
title: "[Samba] Multi-simultaneous write access to a file on a Samba share"
date: 2016-11-09
forum: Server Platforms
---

### Post by mdewhirst on 2016-11-09
I am running Ubuntu 16.04 LTS Server (no GUI) upgraded from 12.04 via 14.04 with Samba providing disk space as a Windows file server. Plain vanilla local area network, no Windows domain.

I am also successfully running an application written in Paradox 7 for Windows on the Windows workstations (7 and 8.1) which requires write access to a file called PDOXUSRS.LCK and all other files in the directory in which it lives. The application runs separately on each workstation and Paradox 7 accesses the database in that directory using Borland BDE. 

Currently only one user at a time can have that application open. It is vital for my business so I'm stuck with it. C'est la vie.

Some years ago before discovering Ubuntu,  I had OpenSUSE with a Novell Netware VM providing the file serving for that application. That was successfully running multiple simultaneous Paradox users. Novell (and Windows for that matter) was able to permit this. 

Thanks for reading this far. Here is my question:

How can I set up Samba (and/or directory permissions) to do the same thing?

Thanks in advance

Mike

---

### Post by volkswagner on 2016-11-10
Without seeing smb.conf and file permissions, I'll give my best guess.

Likely the issue is, UserA starts/opens the Pdox application and the lock file is created with permissions like
```
-rw-r--r--  6 UserA UserA   4096 May 14 23:57
```
or
```
-rw-rw-r--  6 UserA UserA   4096 May 14 23:57
```

Or some other variation that doesn't allow UserB to write to the same file.

The exact solution will depend on other variables for your specific file share/permissions requirements.

Basically you need to force file creation in the directory to allow all users in a group like "pdoxUsers" to read/write
the file.  Again this can be done in many ways, simplest being allow new files created to be world writeable (the least secure method).

[This document]("http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm") has been my go to resource for learning/implementing more complex share permissions.

If you need additional help or suggestions please post the following:
simple version of smb.conf (without comments)
```
testparm -s
```
file permissions for the directory in question
```
ls -al /path/to/share/dir
```
If you're already using ACLs:
```
getfacl /path/to/share/dir
```

PS: A very good friend of mine has been a heavy Paradox user for decades! He wishes Corel was the winner in the desktop database suite over Microsoft.
He has only very recently (past two years) slowly moved applications to other platforms (Sql, Excel, &/or C#)

---


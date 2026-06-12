---
title: "Ubuntu pi  unable to ftp/sftp with client (filezilla)"
date: 2020-12-30
forum: Server Platforms
---

### Post by dayvkaos on 2020-12-30
I have an a headless server running on a raspberry pi (ubuntu pi image). I can ssh into it no problem, but I cannot transfer any files to a mounted hdd due to the user not having root privileges. In addition I can't seem to log in as root from the client as it doesn't have a password, much like sudo su. How doe's everyone SFTP/FTP into their ubunti pi servers with a client like filezilla?

Your help is appreciated.

---

### Post by TheFu on 2020-12-31
We use a different account. Never root.

---

### Post by dayvkaos on 2020-12-31
We still have the question "[COLOR=#000000]How doe's everyone SFTP/FTP into their ubuntu pi servers with a client like filezilla?"

Any help would be greatly appreciated. 

[/COLOR]

---

### Post by TheFu on 2020-12-31
Nobody should be using plain FTP anymore - or for the last 19 years.

[https://trac.filezilla-project.org/ticket/12089](https://trac.filezilla-project.org/ticket/12089)  On my 20.04 system, 
```
filezilla                             3.46.3-1build1
```
which is one of the broken versions according to the bug report.  On Windows, use WinSCP or a version of Filezilla older than 3.46.0.

On Linux, use one of the Linux file managers with sftp support built-in - which should be any of them. 
[https://www.techrepublic.com/article/how-to-use-linux-file-manager-to-connect-to-an-sftp-server/](https://www.techrepublic.com/article/how-to-use-linux-file-manager-to-connect-to-an-sftp-server/)
Some sftp clients don't appear to work with modern ssh-keys, so it might be necessary for some GUI programs to keep using the old RSA keys, just be certain they are at least 4K length.

Hope this helps.

---

### Post by TheFu on 2020-12-31
If the issue is not about the sftp connection, but just simple file/directory permissions, then you'll want to learn Unix permissions: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) also about owners and groups.  

If the storage you can't write to doesn't use a native Linux file system, you'll need to fix the problem at mount time.  But before we head that direction, which file system is used?
```
df -Th
```
will show the mounted storage and the file system for each.  Hopefully, it isn't FAT32, exFAT or NTFS.

---


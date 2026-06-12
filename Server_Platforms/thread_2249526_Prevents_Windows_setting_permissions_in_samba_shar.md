---
title: "Prevents Windows setting permissions in samba share"
date: 2014-10-22
forum: Server Platforms
---

### Post by Robert_Kosmac on 2014-10-22
I have a rather major problem here.
We have a Ubuntu Server (14.04.1) which hosts several shared folders to multiple windows users. It is also acting as the Active Directory Domain Controller.

The problem is that whenever some one saves a file or folder in one of these shares, the permissions change and then the only person who can alter that file or folder is the creator.
Is there any way to prevent this so that all users can edit each others files in the samba folders?


This is the Samba smb.conf entry to the problematic file:

**[Data]**
**        comment = Network Data folder**
**        path = /CompanyFolder/samba/Data**
**        read only = no**
**        writable = yes**
**        browsable = yes**
**        create mask = 0666**
**        directory mask = 0777**

The folder was set with the permission set:
[B]drwxrwxrwx+  root    sambausers
[/B]
The Windows User Created folders set permissions of:
[B]drwxrwxr-x+  3000000   users
[/B]
Which is not what I want.


Some help would be greatly appreciated.
Thanks! :)

---

### Post by bab1 on 2014-10-23
> **Robert_Kosmac said:**
> I have a rather major problem here.
We have a Ubuntu Server (14.04.1) which hosts several shared folders to multiple windows users. It is also acting as the Active Directory Domain Controller.

The problem is that whenever some one saves a file or folder in one of these shares, the permissions change and then the only person who can alter that file or folder is the creator.
Is there any way to prevent this so that all users can edit each others files in the samba folders?


This is the Samba smb.conf entry to the problematic file:

**[Data]**
**        comment = Network Data folder**
**        path = /CompanyFolder/samba/Data**
**        read only = no**
**        writable = yes**
**        browsable = yes**
**        create mask = 0666**
**        directory mask = 0777**

The folder was set with the permission set:
[B]drwxrwxrwx+  root    sambausers
[/B]
The Windows User Created folders set permissions of:
[B]drwxrwxr-x+  3000000   users
[/B]
Which is not what I want.


Some help would be greatly appreciated.
Thanks! :)
Looks like you have not set group inheritance and the correct directory and file permissions.   [Here]("http://ubuntuforums.org/showthread.php?t=2246424") is some info on how I set up a share with a common group.  Read all of it and then ask questions.

---


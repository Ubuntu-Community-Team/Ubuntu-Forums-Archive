---
title: "samba permissions Issues"
date: 2009-02-20
forum: Server Platforms
---

### Post by cougar97536 on 2009-02-20
Hey all, I am running Ubuntu Server 8.10, and trying to setup a samba box.  I have samba configured so that the proper folders are shared, and all the windows workstations (xp & vista) can see the shares.  My problem is a permissions issue.  if I issue the command
sudo chmod -R 770 folderName
then whoever writes to a file first has full access.  however the permissions are being set to something like owner rwx group r__ other ___ .  this is not what I want at all... any Idea how I can stop the file permissions from changing during editing? Excel 2003...
thanks for your help,
Christopher King

ps: it has been suggested that it might be something called "Opportunistic locking" but I have no real understanding of what this is...

---

### Post by capscrew on 2009-02-21
> My problem is a permissions issue. 

Lets see if we can resolve the issue.

> if I issue the command
sudo chmod -R 770 folderName
This is when you are NOT using Samba.  You are operating in the Linux OS > 
then whoever writes to a file first has full access. however the permissions are being set to something like owner rwx group r__ other ___ . this is not what I want at all... This needs to be resolved using Samba configuration.> 
any Idea how I can stop the file permissions from changing during editing? Excel 2003...

How did you configure Samba?  What version of Ubuntu are you using?  You can control the permissions with create mode and directory mode statements in the /etc/samba/smb.conf file.  This is the most direct way, but it requires you to configure without using the GUI (Nautilus) methods.  If you did configure the share using the GUI then the configuration files should be at /var/lib/samba.

---


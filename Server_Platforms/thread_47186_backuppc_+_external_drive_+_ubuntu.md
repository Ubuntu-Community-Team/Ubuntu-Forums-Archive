---
title: "backuppc + external drive + ubuntu"
date: 2005-07-07
forum: Server Platforms
---

### Post by tigerstripedcat on 2005-07-07
My computer is backedup nightly with backuppc to an external usb hard drive (maxtor onetouch).  The backups work, but the problem is that the drive has some internal spin down time.   When the drive spins down I'm fairly sure I lose the mount point. (I know I lose the mountpoint, but I'm not certain it's from the drive, acpi is disabled though). 

Now the reason this problem is particular to ubuntu is that ubuntu seems to have hard coded the backup location into the backuppc scripts (seems like a stupid idea to me).  So I followed the lead of this guy:

[http://yyhh.org/blog/2005/03/use-old-computer-as-backup-server.html](http://yyhh.org/blog/2005/03/use-old-computer-as-backup-server.html)

and created a symbolic link from /var/lib/backuppc (hard coded ubuntu backup location) to my external hard drive mount point.

But the scripts need to read from this loaction to tell the hard drive to wake up and accept backups.  But if the drive has spun down this is impossible.  So the reason it worked on mandrake is that I was able to keep my backup scripts separate from my backup location.  

Does anyone know backuppc well enought to shine some light on this.   I still don't know if I have the right idea of why this is not working.  I wish I knew what file it needed access to off the external hard drive (that spins down), or why it worked in mandrake.

Sorry this is so long.  Just want to be as detailed as possible


thanks

---

### Post by tigerstripedcat on 2005-07-07
[QUOTE=tigerstripedcat]My computer is backedup nightly with backuppc to an external usb hard drive (maxtor onetouch).  The backups work, but the problem is that the drive has some internal spin down time.   When the drive spins down I'm fairly sure I lose the mount point. (I know I lose the mountpoint, but I'm not certain it's from the drive, acpi is disabled though). 

Now the reason this problem is particular to ubuntu is that ubuntu seems to have hard coded the backup location into the backuppc scripts (seems like a stupid idea to me).  So I followed the lead of this guy:

[http://yyhh.org/blog/2005/03/use-old-computer-as-backup-server.html](http://yyhh.org/blog/2005/03/use-old-computer-as-backup-server.html)

and created a symbolic link from /var/lib/backuppc (hard coded ubuntu backup location) to my external hard drive mount point.

But the scripts need to read from this loaction to tell the hard drive to wake up and accept backups.  But if the drive has spun down this is impossible.  So the reason it worked on mandrake is that I was able to keep my backup scripts separate from my backup location.  

Does anyone know backuppc well enought to shine some light on this.   I still don't know if I have the right idea of why this is not working.  I wish I knew what file it needed access to off the external hard drive (that spins down), or why it worked in mandrake.

Sorry this is so long.  Just want to be as detailed as possible


thanks[/QUOTE]
 After researching some more, maybe the difference is that mandrake has the ability to spin up drives with access.   I googled and see that debian has a kernel patch to have scsi drives spin up at access.  Could a similar problem be occuring here?

---

### Post by tigerstripedcat on 2005-07-08
[QUOTE=tigerstripedcat]After researching some more, maybe the difference is that mandrake has the ability to spin up drives with access.   I googled and see that debian has a kernel patch to have scsi drives spin up at access.  Could a similar problem be occuring here?[/QUOTE]
 One thing to note (and maybe the solution to my problem):  When you alias a dev node-- for example, when you alias /dev/sda1 to /dev/usbhd using udev (becasue I don't want to confuse my ipod with my external harddrive and delete data AGAIN)-- make sure you use BUS="scsi" and SYMLINK it in the rules file.  If you don't, things like gparted wont recognize it as a hard drive.  I hope it fixes my problem.  I'll let you know.

---

### Post by tigerstripedcat on 2005-07-09
[QUOTE=tigerstripedcat]One thing to note (and maybe the solution to my problem):  When you alias a dev node-- for example, when you alias /dev/sda1 to /dev/usbhd using udev (becasue I don't want to confuse my ipod with my external harddrive and delete data AGAIN)-- make sure you use BUS="scsi" and SYMLINK it in the rules file.  If you don't, things like gparted wont recognize it as a hard drive.  I hope it fixes my problem.  I'll let you know.[/QUOTE]
 yep the above fixed it.

---


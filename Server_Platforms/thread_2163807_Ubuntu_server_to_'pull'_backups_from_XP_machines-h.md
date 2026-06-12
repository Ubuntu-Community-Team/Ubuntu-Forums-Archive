---
title: "Ubuntu server to 'pull' backups from XP machines-howto?"
date: 2013-07-19
forum: Server Platforms
---

### Post by three_jeeps on 2013-07-19
I am looking for pointers on a) a program that runs on ubuntu server, or b) a how-to of scripts/descriptions to pull and sync files on XP, W7 machines as backups.  I am looking for something easy to configure and use.   My intention is to run ubuntu server with two identical disks as storage volumes, one mirroring the other.  I plan on using mdadm to configure and manage the two disks as RAID1.


I would like a program to run on the server that will periodically check the windoz machines on the local network and essentially synch the files.
Ideally, I'd like the files on the server to be automatically compressed, and when I restore them, have them automatically decompressed.

I'd also like to look at the backups on the server and open them if necessary, I plan on adding a light weight GUI to the server config (or even a web based broswer (Webmin?)

I've looked at PCBackup (tried it and resulted in strange behavior - I don't trust it), and amanda - way overkill for what I want.
Suggestions/critiques welcomed.

-J

---

### Post by TheFu on 2013-07-19
For your requirements, only **amanda** seems to fit. Sorry.

If you can push the backups, then all sorts of those tools become possible. **Duplicati** or even the built-in Windows7-Pro tool can backup to Samba network volumes. The downside is that Win7-Home backup does NOT support writing to network shares.

I would caution against just having a mirror and calling that a backup.  Mirrors get corrupted files. Mirrors don't let you restore a file with a virus that wasn't uncovered until 2 weeks later.  Only versioned backups support those very important modes.  There are lots and lots of Windows backup tools if you don't want Duplicati.

Lastly, running webmin should only be considered inside a safe, LAN, environment, never over the internet.

I'm happy that I only need to backup 2 Windows PCs and for our requirements a monthly image + daily data-only backups is sufficient. I use **partimage**, but many people like **clonezilla**.  Doing image-based backups for lots of systems is not realistic.

---

### Post by SeijiSensei on 2013-07-19
What about reversing the situation?  Create a backup directory somewhere on the Ubuntu machine and share it with the Windows machines using Samba.  Then you could run a Windows-based backup program if that would be easier.

---

### Post by SeijiSensei on 2013-07-19
What about reversing the situation?  Create a backup share on the Ubuntu machine and share it with the Windows machines with Samba.  Then you could run a Windows-based backup program if that would be easier.

Otherwise you can mount the Windows filesystems on the Ubuntu box with smbfs.  If you share the directories on Windows that you want to backup and mount them on the Ubuntu box, then you can script a rsync job to copy from the mounted machine to the Ubuntu machine.

---

### Post by TheFu on 2013-07-20
> **SeijiSensei said:**
> What about reversing the situation?  Create a backup share on the Ubuntu machine and share it with the Windows machines with Samba.  Then you could run a Windows-based backup program if that would be easier.

Otherwise you can mount the Windows filesystems on the Ubuntu box with smbfs.  If you share the directories on Windows that you want to backup and mount them on the Ubuntu box, then you can script a rsync job to copy from the mounted machine to the Ubuntu machine.

The problem with this is that a complete backup cannot be made, thanks to MS file locking. Without support of shadow copies, lots of important files will not be backed up. Very sad, but true.  Of course, for data files, rsync can work fine to create a mirror.  I don't know whether the versioned rsync facilities work for Windows source drives or not. Versioned backups are very important.

---

### Post by SeijiSensei on 2013-07-20
I create versioned backups by creating a separate dated target directory for each day's backup.

I never try to clone disks myself; I'm usually only concerned about backing up home directories and the like, so my suggestion reflected that experience.  For his task, I would probably use something like clonezilla to create an initial snapshot of the Windows machine, then use daily backups of the volatile files.

---

### Post by tripp98 on 2013-08-07
Try looking at backuppc

It will pull from the desktops if you give the user rights.  Just make sure you are pulling from non-opened files.  IE swap files windows folders etc.

---


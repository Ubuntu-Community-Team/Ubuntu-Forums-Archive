---
title: "Server 8.10 - Automated backup and archive on removable SATA drives"
date: 2009-02-20
forum: Server Platforms
---

### Post by vaf on 2009-02-20
Hi all

I am a pretty basic user, used KDE and Gnome, but I am more familiar with Mac and PC - forgive me, I'm trying my best to switch!

I have built a machine I want to use as a file server - it has 2 internal hardware RAID 1 1Tb drives and 4 SATA removable slots. I have installed Ubuntu Server 8.10 and setup the \Server directory as a share using SAMBA, which works perfectly fine. The RAID 1 is essential for data reliability and security.

I have installed two 1Tb SATA drives in the removable slots and mounted them as /Backup and /Archive. I would like to have the system do the following
[LIST]
[*]Every hour COPY (backup) any file in the /Server directory that has changed since the last backup to the /Backup directory under a folder structure that is built upon the backup time 
[*]Every month any file in the /Server directory that hasn't been ACCESSED within the past 6 months be MOVED to the /Archive directory 
[/LIST] 

The Backup drive is to be removed every night and taken offsite as an additional security measure, so it needs to be able to be hot swapped (pretty sure this is okay, but obviously when drive isn't in the automated backup needs to keep a 'list' of what to backup when the drive returns (ie if /backup not mounted, then accumulate list of changed files and copy those files on next backup along with other changes))

The Archive drive should accumulate files and when a critical percentage of files is reached (say 90% then an email or some sort of notifier should be sent, then when the drive is full the archive process/application will be suspended and notification sent. Then a new drive will be put in its place (mounted in /Archive) - what partitioning app should i use for this?

The /Backup and /Archive directories are read-only shares on SAMBA. 

I haven't installed any GUI, as I was hoping to keep processor usage to a minimum, but I'm happy to if needed.  (which one, and which version (is -core enough?)

I know that it is a very specific ask, but I'm sure it is a common way to setup a file server. The data needs to be 100% reliable (hence the setup) whilst security is not anywhere near as important (so no encryption needed) as it is mainly for photos. I would really appreciate any help on this, as I want to get it right! Please help me with:
[LIST]
[*]applications (preferably non-GUI based) to get me what I want
[*]partitioning application
[*]suggestions/alternatives/comments/criticisms on this setup
[/LIST]
Thanks!:p

---

### Post by vaf on 2009-02-20
Oh and I have installed a DVD-DL burner in the server - is it possible to share the drive so that connected WinXP machines can use the drive as a burner - I can only figure out how to mount the drive as a shared folder, rather than as a device!

Thanks again:D

---


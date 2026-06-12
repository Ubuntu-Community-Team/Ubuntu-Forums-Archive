---
title: "Samba behaviour with Symlinks"
date: 2011-08-29
forum: Server Platforms
---

### Post by byb3 on 2011-08-29
A brief background, I'm trying to archive some DVD/Bluray disks by doing the following command:

cp -sR /mnt/cdrom/bluray/* /mnt/r1/archive/cd1/

This copies a symlink of every file/dir from the CD to the hard disk.  It is browsable when the DVD/Bluray is removed, and if the DVD/Bluray is put in, the file will open.  This is achieved through using Autofs which I did eventually get working as well.

My problem is with Samba.

This is the imporant parts of my smb.conf file

> 
[global]
unix extensions = no

[r1]
path = /mnt/r1
valid users = bob,root
browsable = yes
writable = yes
follow symlinks = yes
wide links = yes
This lets me follow symlinks with samba fine and it works well.  But only if the actual DVD/Bluray is inserted in the drive.  Once the disk is removed, the symlinks are broken and samba no longer presents this to the end user.  It goes invisible.

I was wondering if there was a way that the the default behavior of samba could be changed so that the user could at least see a filename instead of nothing at all.  If they could see the filename and know what was on the disk before having to insert it that would be fantastic.

I know via SSH I can see the symlinks, so it is the way samba interprets the symlinks.

Or if someone can offer an alternative solution to what I'm trying to achieve I'd really like to hear it.

---


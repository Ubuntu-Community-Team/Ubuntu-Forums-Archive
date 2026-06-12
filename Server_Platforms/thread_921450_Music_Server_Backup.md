---
title: "Music Server Backup"
date: 2008-09-16
forum: Server Platforms
---

### Post by TigerWolf on 2008-09-16
I have an interesting problem that I was wondering if you guys may be able to offer some help.

I have a running ubuntu server and would like to use it for backup - in this case music. I want to be able to have the master copy on the server and then be able to add to it and then allow all of the clients to get a copy of it.

I use CVS for my software projects but it would be great to have a system that works like CVS but it seems that CVS has too much overhead and creates all these extra CVS folders. Probably not the best solution but its the one I am familiar with.

I also looked at rsync but there doesnt seem to be any good windows clients out there. If only the whole family used ubuntu.

So in summary im looking for:
- A way to easily backup my music
- A way to easily add to this music collection
- A way to update remote copies of this collections on a LAN from the master copy
- A way to automate this in windows so that it can say update every week.

EDIT: Thinking of other solutions - is it possible to have samba so that it doesnt allow deletion but allows write. A possible way could be to share the music through samba and then use backup on the server (localhost rsync) to ensure that the the music is safe - is this a better solution? Anyone have a good system that they use?

---

### Post by lazyart on 2008-09-16
I'll explain my setup for something no too dissimilar, you can decide if you want to tailor it for your needs.

My daughter recently went away to college.  Worried that she might drop the laptop or have it stolen, I decided a backup would be nice, especially if one of those things happens a couple days before a term paper is due...

I set up my Ubuntu desktop with vsftp.  I created an account for her on the desktop and gave her permission to connect via ftp and access her home folder (within her home folder is a symlink to a mirrored array on another Windows machine, but i digress).

Using SyncBackSE from [www.2brightsparks.com](www.2brightsparks.com), if her machine is on at 1:00 it automatically connects via FTP and syncs up her Desktop, My Documents and Favorites folder back to the raid array.  If she has deleted any files on her machine, those files will go away on the backup as well.  This morning I got a report saying it deleted 4 files and added 11 to the backup.

FTP might be overkill for the lan, but it will certainly work if you go that route.  Or, share it via Samba and use SyncBack.  Enter the share password for the sync profile but don't tell anyone else the password and your files are safe.  Then only you can add to the collection.  Once a week (different days for each machine I would suggest) you can sync the music files.

A once-a-week sync to each machine, especially if done on different days, would probably suffice as a backup as well.

---


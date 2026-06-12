---
title: "umask setting for filezilla from windows to ubuntu"
date: 2014-04-06
forum: Security
---

### Post by denywinarto on 2014-04-06
Hi, i have an ubuntu server (well not purely server, i've got some GUI installed)
and i frequently transfer media files from windows to this ubuntu using filezilla..
(i have to use windows because some editing programs is x86 only)
And i'd like the media to be playable but not editable by some clients, so i set the permission to 755

Problem is, i have to set the permission manually to 755 everytime i transfer the media files..

1. Transfer files from windows to ubuntu using filezilla
2. Set permission from filezilla or ubuntu to 755

I read somewhere this has something to do with umask setting..
Filezilla only reverts back to that file's original permission,

But when i check my umask setting it's 0022..
Which should give 755 to folders, but that's not always the case because i occassionaly get 700

Is there anyway to force filezilla or umask setting to always set the permission to 755?
Or maybe there's another alternative to filezilla for this?

thanks.

---


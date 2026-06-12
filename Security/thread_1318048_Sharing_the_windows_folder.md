---
title: "Sharing the /windows folder"
date: 2009-11-07
forum: Security
---

### Post by Stolea on 2009-11-07
A problem that has bedeviled me since I first started with Ubuntu, is how to set permissions for my /windows (NTFS) folders.
I know that in order to set permissions you have to log in as root which I do with "sudo nautilus"
If I then click on the permission settings for the /windows folder I can change the "owner" from root to peter (me). But in the moment I leave the field it changes back to root. The same applies to "groups" and "others".

I have tried this with other folders and don't have the problem, only the /windows folder. 

If I run ls -l /windows it tells me that the owner is root and the group is plugdev.

Can anyone shed any light as to what and why this is happening?

---

### Post by sisco311 on 2009-11-07
FAT and NTFS don't support unix/linux file permissions and ownership.

You can set the ownership and permissions at mount time (for all files).

uid=username
gid=group name
umask=[user mask]("http://en.wikipedia.org/wiki/Umask")
dmask=directory mask
fmask=file mask

i.e.:
```
UUID=<...>    /windows   ntfs    uid=peter,gid=plugdev,dmask=027,fmask=137    0    0
```

---

### Post by Stolea on 2009-11-07
Thanks for that,
That makes sense. I had suspected that it had something to do with the fact that it was an NTFS file system, but couldn't find anything to confirm that notion.
Cheers

Silly question, Why is the "Group" listed as plugdev. Every other folder is listed as root. Is this also because the folder is an NTFS partition?

---


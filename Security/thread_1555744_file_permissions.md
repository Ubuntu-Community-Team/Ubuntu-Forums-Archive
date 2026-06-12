---
title: "file permissions"
date: 2010-08-18
forum: Security
---

### Post by teddy101 on 2010-08-18
I am trying to change the file permissions so that I may install a windows game (lord of the rings battle for middle earth II). However when I go to properties/permissions: click the button to allow said file to be executed as a program, I get an error message telling me; Sorry, could not change the permissions of "AutoRun.exe": Error setting permissions: Read-only file system?
Is there any way I can change this?

Thanks

I hope I put this in the right secsion.

Tom

---

### Post by stlsaint on 2010-08-18
Are you using this from a disk? If so than you probably need to mount the disk as read/write

```
sudo mount -o remount,rw /media/disk
```
where /media/disk is the cd.

If you are using a downloaded exe...
Have you tried it with wine?

---

### Post by teddy101 on 2010-08-18
Yep its a .exe file.
The problem is I cant turn it in to an executable program via propties as it says its a read only.

However this is def worth a try,

Thanks :)

Tom

---


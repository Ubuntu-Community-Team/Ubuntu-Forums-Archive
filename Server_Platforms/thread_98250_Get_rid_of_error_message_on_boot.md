---
title: "Get rid of error message on boot"
date: 2005-12-02
forum: Server Platforms
---

### Post by jbiggs77 on 2005-12-02
I was going to originally set up my server with SATA Raid 1 but had problems getting it configured right.  Instead, I just used the automatic wizard to format /dev/sda and installed Ubuntu server. 

Last night I went to format /dev/sdb to use as a backup drive.  I am now getting this error on boot:

*Checking all file systems...
fsck.ext3: Bad magic number in super-block while trying to open /dev/sdb
/dev/sdb:
The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid....run e2fsck

I can hit Ctrl-D and the server will boot correctly.  I am going to move this server to a colo soon though and don't want this error to come up every time I reboot.  How can I get rid of it?

Side Question:  Is it possible to convert to a RAID 1 system now that I have the system running?

---

### Post by amohanty on 2005-12-02
> I can hit Ctrl-D and the server will boot correctly. I am going to move this server to a colo soon though and don't want this error to come up every time I reboot. How can I get rid of it?

Edit your  /etc/fstab file:
sudo gedit /etc/fstab

and remove any references to /dev/sdb.

> Side Question: Is it possible to convert to a RAID 1 system now that I have the system running?

Well RAID 1 is mirrored only, so theoretically you should be able to do that, unfortunately I am not sure I have sufficient enough know-how to answer the question.

HTH
AM

---

### Post by LordHunter317 on 2005-12-03
You can, but you'll want to take a backup first.

Anyway, running filesystems on raw disks is a no-no, really on x86.  Fix that thing so it's partitioned first and mke2fs that.  Go from there.

---

### Post by jbiggs77 on 2005-12-06
What partitioning scheme would you recommend for a webserver (handling PHP CRM)?

---


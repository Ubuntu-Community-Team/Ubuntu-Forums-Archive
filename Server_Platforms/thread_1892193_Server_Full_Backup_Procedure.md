---
title: "Server Full Backup Procedure"
date: 2011-12-07
forum: Server Platforms
---

### Post by tgftw on 2011-12-07
So, I've found several ways to do a "full backup" of your server, which typically involves a complete filesystem backup to a tar archive.

I've done this a few times, and restored from it a few times, only to find that the server was not in working order post-restore.

In my experience, the filesystem has been returned to it's previous state, but my services are not working, such as web server, FTP server, MySQL server, etc. I didn't really analyze why they weren't working, other than rebooting the system, because I figured it'd be easier to start over than to troubleshoot each service.

The point of my post: Is there anything other than a filesystem backup that is necessary to return a completely crashed server back to complete working order? I'm familiar with making disk images in Windows, and in my experience a full disk image has always been working exactly how it was when I made the image.

The methods I've tried so far are creating a gzipped tar archive of the entire root of the drive, (recursive)
as well as using Webmin's Filesystem Backup feature, which does basically the same thing.

If the answer is just "you did something wrong," I'm fine with that, I just want to know, **_is there anything other than a file system backup that should be required to completely recover a server?_**

I'm using Ubuntu 10.04 64-bit Minimal on a VPS, so everything is done via SSH.

Typical services I have running are Apache2, vsftpd, MySQL, etc. (standard stuff)

EDIT: I've been reading into PartImage, but I'm not sure if it's going to work any differently than what I've tried before... It's looking promising though, so I'll be playing with that while I wait on any replies ;) Thanks guys.

EDIT 2: After looking at PartImage, it seems I'd have to have another equal or larger partition to mount the primary partition to, and from what I can tell it doesn't look like I can save it to my home computer from my VPS, unless I'm missing something. I'd even be willing to set up a Linux box at home for the PartImage to go to, if need be, but I just haven't seen any documentation on anything like that so far.

---

### Post by Vegan on 2011-12-07
clonezilla is the open source favorite for a full working backup

---

### Post by deonis on 2011-12-07
same here ... Clonezilla or dd...

---

### Post by tgftw on 2011-12-07
Thanks guys, Clonezilla looks to do what I need.

---


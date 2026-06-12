---
title: "Help with plex server"
date: 2019-01-14
forum: Server Platforms
---

### Post by hilario_ferreira on 2019-01-14
Hi:
I have a dual boot instalation on my mini pc:win10 /Ubuntu mate. I want to install plex servers on both systems, to watch my library on my devices, tablets and smart tvs. My library is stored on external disk. With windows everything went fine as it very simple. Concerning Ubuntu I don't find a way to show to plex server where I have my media stored. I read somewhere about that but steps are too complicated for my knowledge. Is there any simple way to do that???
Tks in advance

---

### Post by TheFu on 2019-01-14
[http://localhost:32400/web](http://localhost:32400/web)

Visit that webpage on the Linux machine and setup the location for the different media types.  This depends on the storage being available and mounted in such a way that Plex can read it.  It doesn't need to have write, just read.

BTW, NTFS storage is kinda slow if you don't use a proper mount via the fstab.

---

### Post by slickymaster on 2019-01-14
*Thread moved to **Server Platforms**.*

---

### Post by hilario_ferreira on 2019-01-16
> **TheFu said:**
> [http://localhost:32400/web](http://localhost:32400/web)

Visit that webpage on the Linux machine and setup the location for the different media types.  This depends on the storage being available and mounted in such a way that Plex can read it.  It doesn't need to have write, just read.

BTW, NTFS storage is kinda slow if you don't use a proper mount via the fstab.

Tjhis is what I did in windows and what I tried to do in ubunu.

The problem is that when in ubuntu I can't  find the location of my midia !! or better saying I can't indicate to plex server where it is !!
And the usb disk is visible on my desktop !!

---

### Post by TheFu on 2019-01-16
You probably need to use a real mount, not gvfs.
Mount the storage using the fstab.  Lots of how-tos for that.  And it will be faster.

---

### Post by hilario_ferreira on 2019-01-16
Sorry I have to rectify my last post:I can indicate the place where the videos are located , but plex says there's nothing there !!!

---

### Post by hilario_ferreira on 2019-01-16
> **TheFu said:**
> You probably need to use a real mount, not gvfs.
Mount the storage using the fstab.  Lots of how-tos for that.  And it will be faster.

Sorry but I don't know how to do that.

---

### Post by TheFu on 2019-01-16
If the storage is mounted, but cannot be "seen", then it is likely a permissions issue.  Google "Ubuntu Permissions tutor" and work through it.  After that, create 3 userid and 2 groups.  Mix and match the users inside the groups and practice with each in different terminals using a directory and files in /tmp/ somewhere.  Takes about 45 minutes until the lightbulb of understanding "clicks."  If you don't do these things, you will be frustrated with all Unix computers until you do.

As for mounting with fstab - there are at least 50 posts here about doing that. Google "fstab ubuntu" to find the how-to guide on help.ubuntu.com.

Just trying to teach you to fish, not hand you a fish today.

---


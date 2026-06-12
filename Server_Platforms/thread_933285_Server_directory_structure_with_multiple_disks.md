---
title: "Server directory structure with multiple disks?"
date: 2008-09-29
forum: Server Platforms
---

### Post by gpsmikey on 2008-09-29
Greetings -- I'm putting together a home server and have been reading all the good documents and comments I can find on this, but need a bit of guidance.  I realize I can mount drives and
share directories however I want, but I am trying to find what
the currently "suggested" structure is -- should the drives that are going to be shared be mounted in the /media directory then shared via Samba from there ?  ( /media/disk1/data etc ).  I thought I remember reading somewhere recently that it was now prefered to mount stuff through the /media path.  Or is it better to have additional drives mounted on some other mount points ??  I realize I can do it however I want, but I would prefer to do it the "normal" way ... whatever that is :)
FWIW, most of the other machines on the LAN in the house are XP-Pro machines.

Thanks 
mikey

---

### Post by prshah on 2008-09-29
> **gpsmikey said:**
> 
should the drives that are going to be shared be mounted in the /media directory then shared via Samba from there ?  

Yes, that's right; though, as you say, there is no "right" or "wrong" way, but this is the "accepted" way. You can also just share the "/media/" directory, to expose all the drives/partitions through a single share; but watch out for permissions issues!

---

### Post by puppywhacker on 2008-09-29
The directory tree is standardized [filesystem hierarchy standard]("http://www.pathname.com/fhs/")

/srv : Data for services provided by this system
/media : Mount point for removeable media
/mnt : Mount point for a temporarily mounted filesystem

So if you want to act perfectly pure you'd use /srv

---

### Post by lykwydchykyn on 2008-09-29
Another popular option is to mount the second drive on /home and put the shared data there, either in user home directories or in a shared directory.

---

### Post by gpsmikey on 2008-09-29
Thanks for the input folks (as well as the link to the "official filesystem" docs).  Sounds like I'm mostly on the right track here so it's "full speed ahead and damn the windows" or something like that :D  

Hopefully this will also provide some insight for others who are going down the same path.

mikey

---


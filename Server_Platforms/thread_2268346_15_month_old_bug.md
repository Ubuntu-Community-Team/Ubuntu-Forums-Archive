---
title: "15 month old bug"
date: 2015-03-08
forum: Server Platforms
---

### Post by cackles on 2015-03-08
Hi, so instead of upgrading I decided to do a fresh install -this has lead to great regret. You can see all the upgrades I have done over the last seven years and in my divine wisdom I had a thought (dangerous) and it was just to start afresh, new hardware and went from 32 to 64 bit.

Anyways, the jist of it is I am getting an error;  

no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory

This bug has been around since the backend of 2013. I've worked around it by removing the offending package. But between this and another few long term bugs it is making simple setup and deployment problematic.

Is there anyone that can get things like this kicked up the chain?

---

### Post by kerry_s on 2015-03-08
> Is there anyone that can get things like this kicked up the chain?


i'll see what i can do. ;)

---

### Post by tgalati4 on 2015-03-08
Perhaps tell us the package and the hardware that you are having problems with.  Have you updated the bug report?

---

### Post by Doug S on 2015-03-08
> **cackles said:**
> Anyways, the jist of it is I am getting an error;  

no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory

This bug has been around since the backend of 2013.I entered [the bug report]("https://bugs.launchpad.net/debian/+source/samba/+bug/1257186") on 2013.12.02, during trusty daily testing. It does seem to be taking an excessive amount of time to fix. That being said, I still have never noticed any issue other than the message itself.

---

### Post by kerry_s on 2015-03-08
so the answers on #14
Fix:
run "pam-auth-update" and remove "SMB password synchronization".

apparently not a bug but a feature. lol

---

### Post by cackles on 2015-03-09
> **kerry_s said:**
> so the answers on #14
Fix:
run "pam-auth-update" and remove "SMB password synchronization".

apparently not a bug but a feature. lol

lol, yup :)

It is better if you don't install Samba from options during the initial setup, well, means less work. Seems they have it disabled when you apt-get samba. So someone-somewhere is aware of it.

---


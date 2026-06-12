---
title: "How to change hostname in Lucid"
date: 2012-01-05
forum: Server Platforms
---

### Post by vfclists on 2012-01-05
Some off my Lucid systems revert back to the original hostname whenever I try to change it.

I run the hostname command, edit the /etc/hostname, and change it /etc/hosts, yet the old hostnames tend to persist.

Is there some script or setting causing them to revert?

/vfclistsGUY

---

### Post by 2F4U on 2012-01-05
My understanding is that you must change the hostname in

/etc/hosts

and in

/etc/hostname

and finally execute 

sudo hostname -F /etc/hostname

---

### Post by vfclists on 2012-01-08
Thanks, it works

> **2F4U said:**
> My understanding is that you must change the hostname in

/etc/hosts

and in

/etc/hostname

and finally execute 

sudo hostname -F /etc/hostname

---


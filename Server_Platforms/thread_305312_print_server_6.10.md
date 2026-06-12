---
title: "print server 6.10"
date: 2006-11-23
forum: Server Platforms
---

### Post by 13ojo on 2006-11-23
Hello,

How do i set up a print server for my linux box?.

Its terminal only, connected all remotely (via LAN, eg SSH).

I've installed samba and can stuff around with it, eg sharing some folders so the windows pcs can read/write into it.

However i'm meant to install cups?, i have no idea how to.

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package cups is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cups has no installation candidate

```

and most tutorials seem to assume cups is installed... :(.

Can some1 guide me on how to set up cups, make it print, then share this printer over the network?

---

### Post by 13ojo on 2006-11-23
> 
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

The uncommented lines in my sources.list if anyone was curious

---

### Post by DerHesse on 2006-11-23
$ sudo apt-get install cupsys    

....should install it for you. 

If dependencies are still missing use synaptic.

---


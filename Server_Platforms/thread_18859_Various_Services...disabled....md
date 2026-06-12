---
title: "Various Services...disabled..."
date: 2005-03-09
forum: Server Platforms
---

### Post by paradox on 2005-03-09
Hi!

How I can disable certain service like rpcbind or other unknow service on port 603 or 608 (sift-uft...hu?!?)? In /etc/inetd.conf don't appears...exist a file with a list of various services like inetd.conf?

TNX

---

### Post by alastair on 2005-03-10
Various things are started from initscripts in :

/etc/init.d

You manage the runlevels using something like :

update-rc.d

see : man update-rc.d

and :

[http://www.debian.org/doc/manuals/reference/ch-system.en.html#s-runlevels](http://www.debian.org/doc/manuals/reference/ch-system.en.html#s-runlevels)

---

### Post by paradox on 2005-03-11
[QUOTE=alastair]Various things are started from initscripts in :

/etc/init.d

You manage the runlevels using something like :

update-rc.d

see : man update-rc.d

and :

[http://www.debian.org/doc/manuals/reference/ch-system.en.html#s-runlevels](http://www.debian.org/doc/manuals/reference/ch-system.en.html#s-runlevels)[/QUOTE]

Yes I think is fam daemon cause that...

---


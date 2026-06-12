---
title: "REQUEST: Twinkle"
date: 2006-06-28
forum: Ubuntu Backports
---

### Post by mikearthur on 2006-06-28
The version in Dapper is hilariously outdated, and the version in Edgy works fine on Dapper, if I do a dpkg --unpack (which, I know, is unwise).

---

### Post by mlind on 2006-06-30
[QUOTE=mikearthur]The version in Dapper is hilariously outdated, and the version in Edgy works fine on Dapper, if I do a dpkg --unpack (which, I know, is unwise).[/QUOTE]

I built twinkle straight from Debian upsteam, but didn't test it though. Building happened on clean-room environment and everything looked okay.
[http://www.freefilehoster.com/uploads/1151647672twinkle-0.7.1-dapper.tar.gz](http://www.freefilehoster.com/uploads/1151647672twinkle-0.7.1-dapper.tar.gz)

---

### Post by ivomans on 2006-07-02
[quote=mlind]I built twinkle straight from Debian upsteam, but didn't test it though.[/quote] 
Just installed and tried your package: works great!

---

### Post by mulvila on 2006-07-02
[QUOTE=mlind]I built twinkle straight from Debian upsteam, but didn't test it though. Building happened on clean-room environment and everything looked okay.
[http://www.freefilehoster.com/uploads/1151647672twinkle-0.7.1-dapper.tar.gz](http://www.freefilehoster.com/uploads/1151647672twinkle-0.7.1-dapper.tar.gz)[/QUOTE]

Works with me also. Thanks a bunch.

Marko

---

### Post by kthonos on 2006-07-26
Thanks! It would be great if it would be picked up and updated in the repos.

---

### Post by ivomans on 2006-07-26
I just noticed in launchpad [https://launchpad.net/products/dapper-backports/+bug/51208]("https://launchpad.net/products/dapper-backports/+bug/51208") a link to a newer 0.8 version .deb package. Works good for me.

---

### Post by kblood on 2006-09-21
Hi there,

I just installed the .deb linked at the Launchpad page. Works great, thanks!

However, I am trying to find a .deb with iLBC included. I have found some information on conflicting licenses, but Ekiga includes it, so... :confused: 

Anybody knows of any Ubuntu .deb for Twinkle with iLBC? It would make me a very happy man indeed!

---

### Post by smolko on 2007-01-16
The new Twinkle 0.9 is out for about 3 months, but it's not in the ubuntu repositories. I've tried to install a package from debian, but there were some problems with dependencies and I don't want to mess up my system.
Do you know about a ubuntu repository or a single package for edgy with twinkle 0.9?
Thanks.

---

### Post by sergio.callegari on 2007-02-17
Actually Twinkle 1.0 is now out with new features wrt Twinkle 0.8 (the one in edgy).
Also Twinkle 1.0 is in feisty... so maybe a backport to edgy could be possible...

---

### Post by smolko on 2007-02-17
It depends on some other packages, that are in feisty... In a few weeks feisty will be out, I think I'll wait for the official release.

---


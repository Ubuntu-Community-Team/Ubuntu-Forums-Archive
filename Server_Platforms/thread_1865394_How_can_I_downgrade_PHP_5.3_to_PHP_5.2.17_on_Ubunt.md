---
title: "How can I downgrade PHP 5.3 to PHP 5.2.17 on Ubuntu Server?"
date: 2011-10-20
forum: Server Platforms
---

### Post by webweaver on 2011-10-20
I've been working on this issue for the last few days, and cannot seem to find a solution, so I would really appreciate any help anyone can give.

I have Ubuntu Server 11.10 (64-bit) installed on a virtual machine, and when I install the rest of the LAMP stack I end up with PHP 5.3.6, as expected. However, I really need to downgrade to PHP 5.2.17 (latest stable), but can't find any way to do it.

I have seen other solutions for installing PHP 5.2.10 via Karmic repos, however I really need 5.2.13 or higher, so these solutions don't work for me.

Any help would really be appreciated!

---

### Post by vasile002 on 2011-10-20
you can just compile it from sources to some custom location like /usr/local/php52 and use it from there

---

### Post by webweaver on 2011-10-20
> **vasile002 said:**
> you can just compile it from sources to some custom location like /usr/local/php52 and use it from there

Unfortunately it's been quite a long time since I've compiled anything from source, and I wouldn't be sure what configuration options to set, etc.

Especially for all these packages:
libapache2-mod-php5
php5-cli
php5-common
php5-mysql

---

### Post by Lars Noodén on 2011-10-20
I'd hold off on compiling from source as a last resort.  Even then, it should still be rolled up as a package so that it can be in the database of installed applications.

Rather than compiling from source, you might look first at [apt-pinning](https://help.ubuntu.com/community/PinningHowto).  That can be used to tell the package manager to stay with a certain version number for a particular package.  I've used it in the past to get newer versions from the testing distro.  However, it should also work just fine to point you to an older version.  If the older version of PHP is not in the repository, you may also need to tweak the repositories in APT.

---

### Post by webweaver on 2011-10-20
> **Lars Noodén said:**
> I'd hold off on compiling from source as a last resort.  Even then, it should still be rolled up as a package so that it can be in the database of installed applications.

Rather than compiling from source, you might look first at [apt-pinning](https://help.ubuntu.com/community/PinningHowto).  That can be used to tell the package manager to stay with a certain version number for a particular package.  I've used it in the past to get newer versions from the testing distro.  However, it should also work just fine to point you to an older version.  If the older version of PHP is not in the repository, you may also need to tweak the repositories in APT.

Thank you! I'm not sure I completely understand how that works, but after looking over it and using Backports, it seems I can either use 5.2.4 or 5.3.6. So does this mean I'd have to build from source to get 5.2.17?

---


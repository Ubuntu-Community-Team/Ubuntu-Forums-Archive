---
title: "Local repo for different distros"
date: 2007-10-22
forum: Repositories &amp; Backports
---

### Post by penguinfan on 2007-10-22
Guys and Gals,

How do i create a local repository for Dapper, Feisty and Gutsy.

I have 3 computer running different versions of Ubuntu. I have a LOT of deb files that i acumulated and which is all in one folder. I keep this folder updated by rsync the different /var/cache/apt/archives folders.
But now i have 'old' deb files that i want to get rid of as well as creating a 'sort of a local mirror' with just the applications that i regularly install.

How do i do this without downloading the whole mirror as i have quite a lot of deb files allready? AND how do i keep this mirror updated and remove the old deb files?

Thanx for your help.

---

### Post by x0as on 2007-10-22
I use apt-proxy to keep a couple of ubuntu & debain boxes updated.     Seems like the best solution for what you want to do.

[https://wiki.ubuntu.com/AptProxyHowTo](https://wiki.ubuntu.com/AptProxyHowTo)

---

### Post by penguinfan on 2007-10-23
I'll check it out and let you know how i find it. Thanx

---


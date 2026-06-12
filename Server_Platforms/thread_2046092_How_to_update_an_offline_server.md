---
title: "How to update an offline server?"
date: 2012-08-22
forum: Server Platforms
---

### Post by niallmac on 2012-08-22
Hi all, i've been searching the internet for an answer to this but I haven't found anything comprehensive (or anything that won't take me hours of tedious downloading to do).

How do you update a headless server with no internet access?

Situation is I run a small network for a hospital department. We have no internet access to this network. I've resurrected an old Dell Poweredge 2800 and put Ubuntu server 11.10 on it. Sited it in another building across the road and it serves as perfectly stable off-site storage. I administer it via webmin. It all works perfectly!

However, what I'd like to do is install the Dell open manage software ([http://linux.dell.com/repo/community/deb/latest/](http://linux.dell.com/repo/community/deb/latest/)) so I can keep track of the RAID array etc. (I'm presuming this will work with my hardware...).

I've manually downloaded all the open manage packages (tedious), but obviously this alone is not enough. I need to access a load of packages from the ubuntu repository..... I draw the line at manually doing this!

I have internet access on a windows XP (yes yes, I know, what century is this?!) machine, but I'm not supposed to install any software on it (obviously there's a way around this)...

How can I generate a list of files I need (on a webmin command line interface) then download them on a windows XP machine?

Is this an impossible situation?

Many thanks in advance.

---

### Post by LHammonds on 2012-08-22
Yes, there are several different ways to do this.  But you need a machine to have access to the Internet to sync the repository locally...then move the machine to your non-access network and point your server to your repository.

I cannot remember the names of the packages but I know there are at least 2 that will allow you to maintain a local copy of the repository...similar to Window's Update Server (WSUS)

EDIT: 

[http://www.unix-ag.uni-kl.de/~bloch/acng/](http://www.unix-ag.uni-kl.de/~bloch/acng/)

[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

LHammonds

---


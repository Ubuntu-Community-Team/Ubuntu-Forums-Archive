---
title: "Begining Server???"
date: 2009-07-15
forum: Server Platforms
---

### Post by charly17201 on 2009-07-15
Okay, I hope I'm in the right place to ask this. If not, please point me in the right direction.

I'm running 2 computers on Ubuntu (8.04 and 9.04) and a 3rd computer on WinXP (I know, but I gotta be able to do my AS400 over Citrix Access  at the house).

I'm on a build for a 4th that I want to make into a server so I can tie everything together and also access it from work.

My question(s) is/are: where do I start reading on how to set up the server? Other than getting the Ubuntu Server version, where do I go next, what should I read, etc.

Thanks for any help/guidance you might have.

---

### Post by lisati on 2009-07-15
The [Ubuntu server edition]("http://www.ubuntu.com/products/whatisubuntu/serveredition") has a [handbook]("http://www.ubuntu.com/files/server/UbuntuServerBrochure804LTS.pdf") you can download.

Other forum users more experienced in setting up and using servers might be able to offer other suggestions.

---

### Post by cariboo on 2009-07-15
There is also the Howtoforge [guide]("http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2")

---

### Post by ugm6hr on 2009-07-16
> **charly17201 said:**
> I'm on a build for a 4th that I want to make into a server so I can tie everything together and also access it from work.

Decide exactly what you want the server to do first.  Then decide what hardware to use.  Most hardware appropriate for servers is cheap, and the only expense is really the storage. I used an old P4 as a FreeNAS server for home use.

It shares files on Samba (to Windows and Linux), NFS (Linux only) and FTP (rapid transfers), acts as a media server (to XBMC), and also has a simple home web server, amongst other things.  This can be done much more easily with FreeNAS than any other distro; if your needs are simple, I would recommend it.

Of course, Ubuntu server is a more complete option for web serving and database use, but is often overkill for most home servers.

Check out the FreeNAS link below for complete details.

---


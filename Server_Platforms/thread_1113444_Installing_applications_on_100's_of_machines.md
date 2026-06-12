---
title: "Installing applications on 100's of machines"
date: 2009-04-01
forum: Server Platforms
---

### Post by Aeonsies on 2009-04-01
Greetings everyone,

Can anyone point me in the right direction on what software or service I can use to deploy an installation of software on 100's of workstations without having to do it by hand?  I've been looking for this solution for a long time now but haven't had much luck.

If this could be done on my server that would be ideal.  (Aside from making a PXE server and making all my workstations basically thin clients).

Any help would greatly be appreciated.

Thanks much,

---

### Post by HermanAB on 2009-04-01
Parallel SSH and cron.
[http://www.theether.org/pssh/](http://www.theether.org/pssh/)

---

### Post by bluefrog on 2009-04-02
Open Computer and Software Inventory Next Generation, the open source automated inventory and deployment system

[http://www.ocsinventory-ng.org/index.php?page=English](http://www.ocsinventory-ng.org/index.php?page=English)

---

### Post by tarps87 on 2009-04-02
> **HermanAB said:**
> Parallel SSH and cron.
[http://www.theether.org/pssh/](http://www.theether.org/pssh/)

+1 also as you will presumable be installing the same program on the OS and you have a server set up you may want to look a apt-cacher. It should run on any Debian based distro and will decrease internet usage.

[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

---

### Post by BkkBonanza on 2009-04-02
I never saw pssh before. That's pretty cool!

---

### Post by Aeonsies on 2009-04-02
Oh ya, just what I was looking for.  Thanks much to everyone for the info :p

---


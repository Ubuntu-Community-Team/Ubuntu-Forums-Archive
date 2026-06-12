---
title: "ubuntu-desktop has no internet access"
date: 2010-08-26
forum: Server Platforms
---

### Post by jschmeau on 2010-08-26
I have ubuntu server 10.04 installed with wired internet access through my router.  I recently installed the ubuntu-desktop packages and cannot get internet through the gui, firefox never gets past the "looking up" stage.
I can access the internet through the command line and through webmin httptunnel.  Wget, apt-get install, apt-get update, apt-get upgrade all work fine from the command line.  I have local access to the GUi as well in the form of VNC that is working fine.
I know i am missing something simple here, any ideas??
Thanks in advance for any help offered!

---

### Post by jschmeau on 2010-08-26
Anyone?  Bueller?  Bueller?

---

### Post by jschmeau on 2010-08-26
Solved.

Added valid nameserver to /etc/resolv.conf 


My connection was fine, I just had no nameservers set to resolve dns.

---


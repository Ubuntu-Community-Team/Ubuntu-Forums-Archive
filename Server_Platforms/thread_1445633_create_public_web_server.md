---
title: "create public web server"
date: 2010-04-02
forum: Server Platforms
---

### Post by gotenks05 on 2010-04-02
I am trying to setup a web server, in order to launch an author's website and having a bit of troubles.  I am running The latest version of Ubuntu 8.04 LTS and have Apache, MySQL, and PHP 5 installed.  My IP address is dynamic, so I setup a Dynamic DNS account.  On my router, I forwarded port 80 and setup DynamicDNS, unknown to me, it sent the DDNS server my private IP, instead of public IP, thanks to some help from a different forum.  However, I cannot get my pages broadcasted.  I have a feeling that this is a problem on Ubuntu side or something, since I am greeted by a login page that takes me to a ZyXel configuration menu, when I don't have anything of ZyXel.  My computer is a 20-inch iMac5,1 and my router is WGT624 v2.  Since everything else was done properly, what else do I need to do?

**Update:** I found the problem.  I forwarded port 80 from only the router, not the modem.

---


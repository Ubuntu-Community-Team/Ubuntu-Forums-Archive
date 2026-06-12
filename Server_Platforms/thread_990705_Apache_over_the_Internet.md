---
title: "Apache over the Internet"
date: 2008-11-23
forum: Server Platforms
---

### Post by cmkrause on 2008-11-23
So I have been using Ubuntu for about 1.5 years and consider myself alright with configuration and such.  However I can't figure out how to make a nameserver for my server.  I have about 5 or so sites that I wish to host on my servers, but can not figure out how to take my static ip and link it to the domains.  I am pretty sure that I need to use BIND, but I can't figure out how to configure it.  I also will have to setup virtual hosts with Apache.  Any user-friendly advice, tutorials, etc. that you guys know of would be appreciated.  If it helps, I can post my static ip and domain names.  Lastly I tried doing it based off a youtube tutorial in webmin, is there a way to undo those changes and start with a clean slate?

Thanks!

---

### Post by cariboo on 2008-11-23
You don't need bind, that just complicates matters. Have a look at his howto on creating virtual hosts. It is for Gutsy, but it still works the same way for later versions:

[http://www.daryl.mu/2008/01/20/howto-set-up-apache-virtual-hosts-on-ubuntu-gutsy-gibbon/](http://www.daryl.mu/2008/01/20/howto-set-up-apache-virtual-hosts-on-ubuntu-gutsy-gibbon/)

Jim

---

### Post by Lars Noodén on 2008-11-23
Perhaps the name-based virtual host tutorial is one of the items you are looking for:

[http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)

---


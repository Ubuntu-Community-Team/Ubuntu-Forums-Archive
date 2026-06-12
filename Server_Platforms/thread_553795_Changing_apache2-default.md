---
title: "Changing /apache2-default/"
date: 2007-09-18
forum: Server Platforms
---

### Post by breakaway on 2007-09-18
Hello,

I'm running Ubuntu Server 7.04.

Typing in the address of my web server into a browser results in it automatically redirecting to [http://localhost/apache2-default/](http://localhost/apache2-default/). 

How can I change this? I've done several google searches and cannot find anything.

It's almost like the apache2.conf is incomplete.

Anyone? :D

---

### Post by Brazen on 2007-09-18
It's not in apache2.conf.  It's in /etc/apache2/sites-available/default.  There should be a RedirectMatch rule that you can just comment out.

---

### Post by breakaway on 2007-09-19
Oh that's right. For some reason I keep thinking everything I need is in the apache.conf file :(

---


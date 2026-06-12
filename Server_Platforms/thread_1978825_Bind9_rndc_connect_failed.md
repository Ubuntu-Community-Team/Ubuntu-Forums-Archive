---
title: "Bind9 rndc: connect failed"
date: 2012-05-12
forum: Server Platforms
---

### Post by LinuxLi on 2012-05-12
Hi all, I have recently installed a LAMP server using ubuntu 11.10 and have installed Bind9 for dns. The problem I am having is that when I restart Bind9 it gives me the error message rndc: connect failed: 127.0.0.1#953: connection refused.

I have tried changing the named.conf.local to named.conf.

I have changed all the entries in above file to the correct server names and I am still running into this issue.

Can someone please suggest a fix?

---

### Post by chrislau on 2012-06-04
Hi, 
I had the same problem.
First, I am using [_[COLOR="Blue"]webmin[/COLOR]_  ]("http://webmin.com/") which is a very helpfull tool for managing a Debian or Ubuntu Server.
As there is no package avaible in the ubuntu repositories you must download it from the website.
In the index of the BIND module just click on install RNDC, and then it should works.
Regards.

PS: If you don't want to use webmin, [[COLOR="Blue"]_this_[/COLOR]]("http://macosx.com/forums/84067-post5.html") may be usefull.

---


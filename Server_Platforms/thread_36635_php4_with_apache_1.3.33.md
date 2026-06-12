---
title: "php4 with apache 1.3.33"
date: 2005-05-24
forum: Server Platforms
---

### Post by doni on 2005-05-24
hi there

i'm having trouble to get php with my apache 1.3.33 to work.  :-| 

i successfully installed apache (apt-get install apache) and it works. after that i did a "apt-get install php4" accoring to a tutorial. 
but that didn't load the php4 module. so i tried to do it manually by writing it to /etc/apache/modules.conf but that won't work.

one thing: the php4mod is in /usr/lib/apache2/modules/libphp4.so.....apache2??
i want to use apache 1.3.33....isn't that possible with php4?

any ideas how to get this work?
thanks
doni

**SOLVED:** libapache-mod-php4 did the trick!

---


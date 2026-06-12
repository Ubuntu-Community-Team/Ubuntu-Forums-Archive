---
title: "[SOLVED] Apache Document Root??"
date: 2008-06-09
forum: Server Platforms
---

### Post by melrom on 2008-06-09
Hi

I'm trying to configure egroupware to work. The server was not previously set up.

I'm using CentOS 5.1 and following this guide:

[http://www2.maxsworld.org/howtos/egroupware.html](http://www2.maxsworld.org/howtos/egroupware.html)

However, I'm not sure where the document root is for apache. The guide points to /usr/local/apache/htdocs, but /usr/local/apache does not exist. I know apache is working though, because if I go to [http://localhost](http://localhost), I get the right message.

-MelRom

---

### Post by quelx on 2008-06-09
Ubuntu */var/www/*
Centos */vaw/www/html/*

---

### Post by melrom on 2008-06-09
thank you!!

---


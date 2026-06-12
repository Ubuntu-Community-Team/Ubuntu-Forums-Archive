---
title: "FTP server"
date: 2005-03-12
forum: Server Platforms
---

### Post by FLEO on 2005-03-12
Hi everybody,

I got a question for you guys. I'm pretty new to linux and I'm looking for a FTP server to run on my ubuntu server. 

I want a FTP server that I can set ratio for upload and download as Serv-U in Windows.

Of course I want a server to be able to run in console mode.

If you have program suggestion, just let me know.

Thanks,

FLEO

---

### Post by BoBoB on 2005-03-14
I'm running ProFTPD (with a somewhat special setup with SQL authentication) but it's running without problems and you'll find quite a lot of docs and examples on the internet.
It's capable of anonymous login, per-user authentication, and hiding/showing folders and files based on file mask and/or user/group access.
(and much more...)

---

### Post by az on 2005-03-14
apt-cache search ftp |grep server

---

### Post by FLEO on 2005-03-14
Thanks for your advices I'm trying that tonight and I'll give you news,

Thanks,

FLEO

---

### Post by lightyear on 2005-03-16
I also installed Proftpd (and i am new to linux) but can't figure out how to run the server and alter it's config. How do i start the server?

Thanks Bas

---

### Post by Myles3 on 2005-03-16
to start proftpd run this in the comand line
```
sudo /etc/init.d/proftpd start
```

Also if you are new to linux then you might consider getting [webmin](http://www.webmin.com).

it has a module for proftpd

---


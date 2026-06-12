---
title: "help with proftpd install"
date: 2007-01-28
forum: Server Platforms
---

### Post by bigredcherokee on 2007-01-28
Hello all I'm new to Ubuntu, but have been trying to make the move  to linux for quite some time now. 

I'm working on a new web server trying to phase out my Win2003 server. I have now install 6.06 Draper w/ webmin. 

I'm trying to get proftpd install, but when I do an sudo apt-get install proftpd I get an error cant find packages same thing when I try phpmyadmin.

I'm using putty to connect to my server and Win SCP to move files duing the install. 

Any help is greatly appreciated.

Thanks,
Chris
[www.nashsystems.biz](www.nashsystems.biz)

---

### Post by bigredcherokee on 2007-01-29
anybody?

---

### Post by jrock2004 on 2007-01-29
try sudo -i
put admin passwd
apt-get install proftpd

see if that works

---

### Post by thornomad on 2007-01-29
Is proftpd in the universal repositories ? or in the regular ones ?  If so, you need to enable that ... in case you haven't already.  That's all I can think of.

D

---


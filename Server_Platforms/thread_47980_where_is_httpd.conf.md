---
title: "where is httpd.conf"
date: 2005-07-10
forum: Server Platforms
---

### Post by jsgoodrich on 2005-07-10
I am trying to set up the server - I am new at this - I can get to the localhost page but can't make changes re system admin and all that. Can't find a httpd conf file that I can edit. Any advice? Thanks so much

---

### Post by DaturaX on 2005-07-10
[QUOTE=jsgoodrich]I am trying to set up the server - I am new at this - I can get to the localhost page but can't make changes re system admin and all that. Can't find a httpd conf file that I can edit. Any advice? Thanks so much[/QUOTE]

/etc/apache2 if you're using Apache2.

if not  /etc/apache

---

### Post by LordHunter317 on 2005-07-10
For apache 1.3, try /etc/apache
For apache 2, try /etc/apache2.

In either case, read the README.Debian file in the appropriate /usr/share/doc directory first.

---

### Post by jsgoodrich on 2005-07-10
it's there but has virtually nothing in it re admin settings...thus my confusion

---

### Post by deuce868 on 2005-07-10
Apache2 broke out the configuration files a bit. Check out apache2.conf, httpd.conf and the modules & sites available folders for the same information that used to all be in httpd.conf in 1.3

---

### Post by mohtasham1983 on 2006-11-02
apache configuration file in ubuntu 6.06 is /etc/apache2/apache2.conf

---


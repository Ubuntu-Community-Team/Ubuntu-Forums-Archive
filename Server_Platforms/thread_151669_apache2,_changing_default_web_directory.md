---
title: "apache2, changing default web directory"
date: 2006-03-28
forum: Server Platforms
---

### Post by mads-b on 2006-03-28
as a standard, [http://localhost/](http://localhost/) points to /var/www/ in the system, but I want to change it to something else, let's say /mnt/hdb/www/. In windows this was a setting in the httpd.conf file. How do I do it in ubuntu?

---

### Post by localzuk on 2006-03-28
edit the apache2.conf file in /etc/apache2/

---

### Post by MJN on 2006-03-28
The **DocumentRoot** directive will more likely be in /etc/apache2/sites-available/default if you're/he's using the modularised Apache.

Mathew

---

### Post by mads-b on 2006-03-29
There it was! Thanks MJN. I'm bad at looking for stuff.. ](*,)

---


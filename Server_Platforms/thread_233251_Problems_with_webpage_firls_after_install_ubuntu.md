---
title: "Problems with webpage firls after install ubuntu"
date: 2006-08-09
forum: Server Platforms
---

### Post by jfreimer on 2006-08-09
I was wondering how you turn off indexing in apache.
Do you just replace:
IndexOptions FancyIndexing VersionSort
with:
IndexOptions
or comment it out?


I was also wondering what is the best way to allow me to put files into /var/www/ should I just chown username:usergroup www or is there a better or more secure way?

---

### Post by d3ck4 on 2006-08-10
Create a .htaccess file in your main directory or directory of your choice.

Add this line to that file:

> Options -Indexes

---


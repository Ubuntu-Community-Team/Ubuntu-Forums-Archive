---
title: "Ubuntu Server Questions"
date: 2011-01-12
forum: Server Platforms
---

### Post by DanHorniblow on 2011-01-12
I am running Apache and the web root is currently /var/www/ I want to change it to my home directory, how do I do this?

I also want this server to be an email server, anyone know of a good email server for ubuntu?

Cheers

---

### Post by tgalati4 on 2011-01-12
grep var /etc/apache2/sites-enabled/000-default

As far as mail servers, they all have a learning curve to set up.  What specifically are your email needs?  Single person, small business, mass email campaign?

---

### Post by DanHorniblow on 2011-01-12
The email server will have no more than 5 or 10 email accounts, I am just trying to gain experience with linux servers as I come from a windows background.

I am currently using hMailServer for windows which has a very easy to use GUI

---


---
title: "httpd.conf"
date: 2006-07-25
forum: Server Platforms
---

### Post by Mau on 2006-07-25
I'm trying to setup a LAMP server on my desktop Ubuntu install to use for development.  I have followed and read [this guide](https://help.ubuntu.com/community/ApacheMySQLPHP), and Apache seems to be running all-right, but I wish to change my document root to my home folder.  I have looked in /etc/apache2.conf and /etc/httpd.conf but I cannot see where /var/www is defined as my document root.  How do I change the document root and where is the real config file?  Both of those files are incomplete.

---

### Post by joft on 2006-07-25
Hi,

I think, what you are searching for is in the file /etc/apache2/sites-enabled/000-default - or at least some file inside the directory /etc/apache2/sites-enabled .

It contains symbolic links to files in the directory /etc/apache2/sites-available . The same is true for apache2 module configuration (mod instead of sites in the directory names).

---


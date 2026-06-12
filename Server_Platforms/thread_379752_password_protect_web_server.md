---
title: "password protect web server"
date: 2007-03-08
forum: Server Platforms
---

### Post by DiGiTY on 2007-03-08
in Ubuntu 6.10 with Apache 2.0.55, how do I password protect the whole web server (and not just a folder)?

---

### Post by Mr. C. on 2007-03-08
You can place your authentication lines in your httpd.conf for the server, or place your properly configured .htaccess file at the root of the web server.

Search for "When (not) to use .htaccess files" in :

[http://httpd.apache.org/docs/2.2/howto/htaccess.html](http://httpd.apache.org/docs/2.2/howto/htaccess.html)

and then search for "Authentication example".

MrC

---

### Post by DiGiTY on 2007-03-10
thanx, worked like a charm. good link Mr. C

i already had a .htaccess file at the root of web server with password protecting features and then i just copied the syntax in there to <Directory /var/www/> setcion of /etc/apache2/sites-available/default (that's where Ubuntu or Apache 2.0.55 stores the directory/host configurations)

thanx again

---

### Post by Mr. C. on 2007-03-10
Fantastic!

Make sure you're clear on the differences between Directory and Location.

Best of luck,
MrC

---


---
title: "FTP and HTTP server?"
date: 2011-03-06
forum: Server Platforms
---

### Post by capitalfear on 2011-03-06
im trying to build an FTP and an HTTP server with multiple user access on the same box, with ubuntu 10.10 64 bit server edition can anyone direct me to a post or tell me how i would go about setting that up?

---

### Post by Lars Noodén on 2011-03-07
For the web server look for HOWTOs about Apache, Lighttpd or nginx.

For "FTP" look first at OpenSSh for SFTP, if you want secure file transfer.

---

### Post by yotis on 2011-03-07
This is a pretty complete one including Apachet + PHP + Mysql and FTP installation and configuration, with FTP users keeped in a database:
[http://www.howtoforge.com/virtual-hosting-with-proftpd-and-mysql-ubuntu-9.10](http://www.howtoforge.com/virtual-hosting-with-proftpd-and-mysql-ubuntu-9.10)

This is just Web server (Apache + PHP):
[http://articles.slicehost.com/2008/4/25/ubuntu-hardy-installing-apache-and-php5](http://articles.slicehost.com/2008/4/25/ubuntu-hardy-installing-apache-and-php5)

This is FTP server:
[http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux](http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux)

If you do a search you'll find a lot of examples and how-to. The Ubuntu version may be a different one, but the above how-to will work.

---


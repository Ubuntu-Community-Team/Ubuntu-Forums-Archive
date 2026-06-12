---
title: "Intrepid LAMP Installation"
date: 2009-01-14
forum: Server Platforms
---

### Post by gprest on 2009-01-14
Hi all,

I've selected LAMP during server installation and everything works perfectly. My problem is locating all the files and directories that have been spread throughout the file system.

For example, after digging around I found Apache HTTP's httpd.conf file, even though its named apache2.conf. \\:D/

Could anyone direct me to a resource that lists where everything is placed and/or named insofar as the LAMP installation provided with the Ubuntu 8.10 Server is concerned?

Thanks in advance,
Geoff

---

### Post by Titan8990 on 2009-01-14
It's fairly standard. The only difference in the Ubuntu install is that Apache uses a split configuration the config files. 

All config files in Linux are found in the /etc/ directory. You can usually take a good guess that apache config will be in /etc/apache2 and that php will be in /etc/php5.

The default root dir defined by /etc/apache2/sites-enabled is /var/www.

---

### Post by Iowan on 2009-01-14
[This]("https://help.ubuntu.com/community/ApacheMySQLPHP") help page *might* help clear some of the fog.

---

### Post by mbeach on 2009-01-14
for the apache part, this may also provide some help:
[http://wiki.apache.org/httpd/DistrosDefaultLayout#head-b5762a3e9764f34f7587e35f4db9ff35d508ced1](http://wiki.apache.org/httpd/DistrosDefaultLayout#head-b5762a3e9764f34f7587e35f4db9ff35d508ced1)

or see
 /usr/share/doc/apache2/README.Debian
as suggested in that link.

---


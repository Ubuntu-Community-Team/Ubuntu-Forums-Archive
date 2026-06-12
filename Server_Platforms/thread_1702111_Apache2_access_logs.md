---
title: "Apache2 access logs"
date: 2011-03-07
forum: Server Platforms
---

### Post by elliotbeken on 2011-03-07
Hi all, 
i have apache 2 working fine apart from the access log. the access log is empty and i am looking at the correct one !!

is there meant to be a line in /sites-enabled/***** that points to the location of the log ? any help would be great thanks ..

using Ubuntu 10.10 32-bit

---

### Post by bsntech on 2011-03-07
The default location of the access logs are:

/var/log/apache2/access.log

You can change where you want this to go based on the following syntax in a VirtualHost:

ErrorLog /location/to/error.log
CustomLog /location/to/access.log common

Brian S.
BsnTech Networks
[http://www.bsntech.com]("http://www.bsntech.com/services-provided/networking-and-infrastructure.html")

---

### Post by elliotbeken on 2011-03-07
i have just seen in the access log folder for apache2 (/var/log/apache2/) there is a file called other_vhosts_access.log and that is where the log is !

---


---
title: "Apache Virtual Host (ubuntu style) What is the loading order"
date: 2009-06-30
forum: Server Platforms
---

### Post by thepreacher on 2009-06-30
As we all know ubuntu installs apache with a default virtual host already setup and most updated apache virtual host setup tutorials will ask that you copy the default to your new file and make the neccessary changes. One therefore ends up with a one file per domain scenario.

What i want to know is:

1. Apart from the simplecity of having just one small file to work with when making changes to a domain, what other benefits are there? What will happen when you lump everything together?

2. What is the order of reading the files in the sites-enabled folder? ie alphabetical, or first modified - first read

---

### Post by mbeach on 2009-06-30
pretty sure the files in sites-enabled are loaded via the include directive somewhere in your apache2.conf file. As such it they will be loaded alphabetically.

[http://httpd.apache.org/docs/2.0/mod/core.html#include](http://httpd.apache.org/docs/2.0/mod/core.html#include)

I believe the benefit is the ability to allow easy enabling and disabling via the a2ensite and a2dissite commands. If you clump them all together in one file, I don't think you have any problems with the functionality of the virtual hosts. I would think this methodology of having the smaller multiple files makes it easier for maintenance purposes, but that depends on how you work and what your needs are.

---

### Post by mbeach on 2009-07-01
bit of a discussion on some other reasonings at:
[http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)

quote from that site:
# Have a simple main configuration file

# Do be able to edit or create a new host by creating/editing a file from /etc/apache2/sites-available/

# In case your web server doesn't restart because of misconfiguration, you can simply remove the link from the file in /etc/apache2/sites-enabled/ pointing to the malformed file in /etc/apache2/sites-available/

---

### Post by Vegan on 2009-07-01
As for as I have noticed, I have my sites numbered from 001 up (000 is the default) and the loader loads them in that order. If you have alternate names they may load differently.

At the end of the day it makes no difference unless you have an error to find.

---

### Post by Abzddon on 2009-07-01
Guyz this is a really stupid question so im not making a new thread for it.

I just installed apache2 on ubuntu 9.04. Im completely new to linux. I cant find the apache2 folder anywhere on my computer. Can someone help me?

:lolflag:

---

### Post by mbeach on 2009-07-05
if you are looking for the files for configuration purposes they are in:

/etc/apache2

---


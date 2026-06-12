---
title: "[SOLVED] Updated Ubuntu Server 8.04 And Now A problem"
date: 2011-01-21
forum: Server Platforms
---

### Post by sligoman on 2011-01-21
Hi All

Desperate for help here.. I have tried everything but to no avail.

Backed up my server and did an update through Webmin as 67 files needed updating, update went flawless (no Error Messages) or that is what I thought.

Problem now is that all web browsers show a pop-up window when I try to open any of my websites that have PHP as the file extension, HTML sites are ok 

If anyone could help me to shed light on the problem I would very grateful..

Regards

Liam

---

### Post by HugoSerrano on 2011-01-21
try to see if you got libapache2-mod-php5

dpkg -l | grep mod-php

---

### Post by sligoman on 2011-01-21
Hi 

Thanks for the reply

This is the result of your command: dpkg -l | grep mod-php

ii  libapache2-mod-php5                 
5.2.4-2ubuntu5.14              
server-side, HTML-embedded scripting languag

hopefully you can make something of it

Liam

---

### Post by sligoman on 2011-01-21
Hi All

Have Managed to solve this one.

[Fri Jan 21 14:56:24 2011] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.


Problem was caused by /etc/phpmyadmin/apache.conf

# phpMyAdmin default Apache configuration

# Alias /phpmyadmin /usr/share/phpmyadmin this line was missing a #

<Directory /usr/share/phpmyadmin>
	Options Indexes FollowSymLinks
	DirectoryIndex index.php

Everything up and running now so one happy bunny.

Thanks to HugoSerrano for the reply

Liam

---


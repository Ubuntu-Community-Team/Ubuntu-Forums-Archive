---
title: "LAMP install"
date: 2009-06-01
forum: Server Platforms
---

### Post by mbender on 2009-06-01
I recently installed a lamp setup on my xubuntu machine with the single command method found on the web.  I am getting a save/open file prompt when I try to view a simple phpinfo() file in /var/www.  Viewing localhost works fine, I get It works, but php files won't work.  I've tried the tips in the forum as well as installing and re-installing with no luck.

Any ideas?

---

### Post by Sef on 2009-06-01
Moved to server platforms.

---

### Post by LepeKaname on 2009-06-01
Usually it has to work out of the box... 
check if you have a symlink from 

/etc/apache2/mods-enabled/php5.* to /etc/apache2/mods-available/

Also check if you have installed:  libapache2-mod-php5

thats all

---

### Post by Iowan on 2009-06-01
You can see if [this]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205") helps.

---

### Post by mbender on 2009-06-01
The symlink to mods-enabled did the trick.  Thanks.

---


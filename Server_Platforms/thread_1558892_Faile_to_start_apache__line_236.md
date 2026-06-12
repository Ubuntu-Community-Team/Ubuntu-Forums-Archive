---
title: "Faile to start apache : line 236"
date: 2010-08-22
forum: Server Platforms
---

### Post by waloshin on 2010-08-22
Failed to start apache :
 * Starting web server apache2
apache2: Syntax error on line 236 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/000-default: No such file or directory
   ...fail!

---

### Post by modmadmike on 2010-08-23
> **waloshin said:**
> Failed to start apache :
 * Starting web server apache2
apache2: Syntax error on line 236 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/000-default: No such file or directory
   ...fail!

It's as it says, ether create && configure the file manually or usee webmin to configure it. (I use lighttpd which has an easily editible config in /etc/lighttpd/lighttpd.conf).

---

### Post by Ryan Dwyer on 2010-08-23
Try running this: sudo a2ensite default

Then start Apache.

---

### Post by waloshin on 2010-08-25
Thanks everyone.

---

### Post by sanlinhtet on 2010-10-15
> **Ryan Dwyer said:**
> Try running this: sudo a2ensite default

Then start Apache.

I tried as you guide for that error. but cann't..I got this error 

ERROR: /etc/apache2/sites-enabled/000-default is a dangling symlink!
ERROR: Site default does not exist!

please help me....what should I do?

---


---
title: "Apache2 Virtualhosts - failed to launch"
date: 2010-08-11
forum: Server Platforms
---

### Post by fela on 2010-08-11
I have three virtual hosts setup on my Apache2 installation (one of which is in the httpd.conf directory). However if I add another one (to the sites-enabled dir), apache fails to launch.

thanks in advance
Fela

---

### Post by Ryan Dwyer on 2010-08-11
A few things:

1) What httpd.conf directory?
2) Hosts should be added in sites-available then enabled with a2ensite which creates a symlink in sites-enabled.
3) What error are you getting when you try to start Apache?

---

### Post by fela on 2010-08-11
> **Ryan Dwyer said:**
> A few things:

1) What httpd.conf directory?
2) Hosts should be added in sites-available then enabled with a2ensite which creates a symlink in sites-enabled.
3) What error are you getting when you try to start Apache?


thanks for the reply
Sorry, I meant httpd.conf file, lol. Yes, I've been using a2ensite to add the sites.

Basically, if I enable the fourth site, I get (when I restart apache):


```
/etc/init.d/apache2 restart
Restarting web server: apache2apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Wed Aug 11 14:40:47 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Wed Aug 11 14:40:47 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
 failed!

```

---

### Post by Ryan Dwyer on 2010-08-11
Please post the contents of the fourth vhost config file as well as your httpd.conf.

---

### Post by fela on 2010-08-11
Never mind, I figured it out (well not figured it out, but fixed it anyway). I commented out the log entries in the VirtualHost config and it's working now :)

(must have been a simple syntax error)

cheers

EDIT: turned out it was because I hadn't created the directory where it was supposed to put its logs! Lol :)

---


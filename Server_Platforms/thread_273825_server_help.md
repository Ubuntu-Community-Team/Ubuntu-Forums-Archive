---
title: "server help"
date: 2006-10-08
forum: Server Platforms
---

### Post by tmez on 2006-10-08
Apache Webserver  	

The Apache server executable /usr/local/apache/bin/httpd does not exist. If you have Apache installed, adjust the module configuration to use the correct path.

---

### Post by paul.maddox on 2006-10-08
Jees, you're going to have to be a bit more specific than that.

It looks like a webmin error, but that's just a guess!

---

### Post by tmez on 2006-10-08
it says that apache is not installed on my webmin

---

### Post by paul.maddox on 2006-10-08
If it is a webmin error, try changing the path to httpd executable in the module config to:

/usr/sbin/apache2 

If you're running apache 1.3.x then i'm not sure where the executable would be, I'm guessing:

/usr/sbin/apache

---


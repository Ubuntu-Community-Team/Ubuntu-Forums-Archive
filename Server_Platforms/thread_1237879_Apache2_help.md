---
title: "Apache2 help"
date: 2009-08-11
forum: Server Platforms
---

### Post by NMWindows on 2009-08-11
Hey all, 

I just installed Apache2 on on my Ubuntu Box, and It won't let me change the etc/apache2/sites-available file to do a symbolic link, I tried gksudo nautilus, but that did not work, 

can anyone help me?

---

### Post by rudy.b on 2009-08-12
To create the symbolic link to your config file, you can use the a2ensite command like so: ```
sudo a2ensite mysite
``` where mysite is the name of your config file in /etc/apache2/sites-available.  Also remember you have to restart apache in order for the change to take effect.  

See [Installing Apache 2]("https://help.ubuntu.com/community/ApacheMySQLPHP#Installing Apache 2") for more info.

---


---
title: "Terminals message when restart Apache2"
date: 2010-08-08
forum: Server Platforms
---

### Post by staroad888 on 2010-08-08
Hallo, i am a begginer on Ubuntu and on server Apache2

When i've tried to restart Apache the terminal gave this message

Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

Can someone know what this means?

Thanks for your time! :D

---

### Post by clrg on 2010-08-08
You haven't configured Apache's domain name correctly (for example, [www.mywebsite.com](www.mywebsite.com)). Since you want it to start anyway, it assumes its IP address to be its name. 

To correct this, edit */etc/apache2/httpd.conf* .

---


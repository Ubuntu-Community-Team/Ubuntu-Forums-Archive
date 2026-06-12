---
title: "Apache2 and 2 domains"
date: 2007-10-13
forum: The Cafe
---

### Post by nickburns on 2007-10-13
Anyone know where there is good help on getting apache2 to handle / configure 2 different domains?

For instance can I make a /var/www2 folder and have domain1.com go to /var/www and domain2.com go to /var/www2?

It this even possible?

also can [www.domain1.com](www.domain1.com) go to /var/www and test.domain1.com go to /var/wwwtest ?

---

### Post by nickburns on 2007-10-13
Figured it out, here it is if someone wants it:

Add to your /etc/apache2/sites-available/default file:



<VirtualHost *>
    DocumentRoot /var/www/domain1
    ServerName [www.domain1.com](www.domain1.com)
</VirtualHost>

<VirtualHost *>
    DocumentRoot /var/www/domain2
    ServerName [www.domain2.com](www.domain2.com)
</VirtualHost>

---

### Post by ventvent on 2007-10-13
Nick Burns hit it on the spot.  Virtual directories work like a champ!

---

### Post by ventvent on 2007-10-13
Depending on what type of site your running you may also want to include a 301 redirect so that it doesn't appear that you have two sites.  Search engines dilute your ranking if you don't.

---


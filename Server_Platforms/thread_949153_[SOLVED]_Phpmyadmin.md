---
title: "[SOLVED] Phpmyadmin"
date: 2008-10-15
forum: Server Platforms
---

### Post by kerryhall on 2008-10-15
A quick question. Why can i visit 127.0.0.1/phpmyadmin/index.php in my web browser and have the phpmyadmin login come up, but there is nothing in /var/www besides index.html?

---

### Post by kerryhall on 2008-10-16
bump

---

### Post by condonm on 2008-10-16
As far as I'm aware you can simply go 127.0.0.1/phpmyadmin and you will be able to access the phpmyadmin log in screen.

---

### Post by Dr Small on 2008-10-16
> **kerryhall said:**
> A quick question. Why can i visit 127.0.0.1/phpmyadmin/index.php in my web browser and have the phpmyadmin login come up, but there is nothing in /var/www besides index.html?
There is probably a line in your httpd.conf file aliasing /phpmyadmin to the actually location of phpmyadmin on the server.

---

### Post by mbeach on 2008-10-16
see:
[http://ubuntuforums.org/archive/index.php/t-892326.html](http://ubuntuforums.org/archive/index.php/t-892326.html)
for a discussion of this.

---

### Post by lykwydchykyn on 2008-10-16
have a look at /etc/apache2/conf.d/phpmyadmin.conf

---

### Post by kerryhall on 2008-10-22
Aha! Thanks to everyone! This was very helpful.

---


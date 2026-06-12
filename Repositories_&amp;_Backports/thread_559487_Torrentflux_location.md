---
title: "Torrentflux location?"
date: 2007-09-25
forum: Repositories &amp; Backports
---

### Post by JohnLi on 2007-09-25
Hi! I have Ubuntu 7.04 installed, and I'm trying to use it to download some torrents through Torrentflux.

I installed it using Synaptic, but while files exist in [http://localhost/torrentflux](http://localhost/torrentflux) , when I browse to /var/www/ there is only a directory named apache2-default. 

Where can I find the Torrentflux config.php file? 

I want to insert the MySQL user name & password.

---

### Post by emf1105 on 2007-10-06
the location for the config.php is /usr/share/torrentflux/www. Hope this helps.

---

### Post by emf1105 on 2007-10-06
sorry, jumped the gun a bit there, you need to edit them in the /etc/torrentflux/config-db.php file.

---


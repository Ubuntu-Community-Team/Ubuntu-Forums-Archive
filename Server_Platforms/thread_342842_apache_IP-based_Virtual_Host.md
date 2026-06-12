---
title: "apache IP-based Virtual Host"
date: 2007-01-20
forum: Server Platforms
---

### Post by frankabel on 2007-01-20
Hi all!

The line “NameVirtualHost *” in the file “/etc/apache2/sites-available/default” inabilities the possibility of use IP-based Virtual Host? I read carefully the doc of the apache and all seem like that line don’t allow me configure any IP-based Virtual Host.

Salute
Frank Abel

---

### Post by mssever on 2007-01-20
Change NameVirtualHost to VirtualHost. See [http://httpd.apache.org/docs/2.2/vhosts/ip-based.html](http://httpd.apache.org/docs/2.2/vhosts/ip-based.html). You can set up Apache however you like. Just edit the configuration files as necessary.

The * simply creates a catchall VH in case a request comes in that doesn't match any other VH. IIRC, the order of the declarations is significant; be sure to read the docs about that.

---


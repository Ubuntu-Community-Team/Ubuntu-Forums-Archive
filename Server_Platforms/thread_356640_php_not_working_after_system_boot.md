---
title: "php not working after system boot"
date: 2007-02-08
forum: Server Platforms
---

### Post by weekendli on 2007-02-08
After my system reboot, the php server seems not working properly. The browser shows a download windows on a php test page, instead of interpreting it.  Does anyone knows why? Many thanks.

apache2, php4, mysql5.0 on ubuntu edgy
sudo apt-get install apache2 php4 mysql-client mysql-server libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql phpmyadmin

---

### Post by weekendli on 2007-02-08
I answer my question here. The problem solved. Althought there are some suggestion about adding  > "httpd.conf: AddType application/x-httpd-php .php"

Or

reinstall the php4 by using synaptic packages manager to remove the packages completely, especially the configure files. it works!!

---

### Post by scrupul0us on 2007-02-09
just a suggestion, i highly recommend moving to php 5.x

---


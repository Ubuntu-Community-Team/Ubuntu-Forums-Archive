---
title: "PHPMYADMIN problems"
date: 2010-05-05
forum: Server Platforms
---

### Post by ductiletoaster on 2010-05-05
Ok so simply put i installed phpmyadmin on my Ubuntu LAMP server and i cant seem to access phpmyadmin

tried [http://myipaddress/phpmyadmin](http://myipaddress/phpmyadmin)

i have installed this contless times on other machines. I dunno what im missing. THoughts

Ubuntu-desktop 8.04lts LAMP server... running in virtual box(i use this for development purposes)

---

### Post by Naitsirhc Hsem on 2010-05-05
is the service started

---

### Post by wojox on 2010-05-05
See if any of this helps [https://help.ubuntu.com/community/ApacheMySQLPHP#Phpmyadmin%20and%20mysql-admin](https://help.ubuntu.com/community/ApacheMySQLPHP#Phpmyadmin%20and%20mysql-admin)

---

### Post by ductiletoaster on 2010-05-06
Haha ironic! I remember editing /etc/apache2/apache.conf and placing this at the bottom "Include /etc/phpmyadmin/apache.conf" on previous installs. Well thank you guys

---

### Post by wojox on 2010-05-06
Your welcome.

---


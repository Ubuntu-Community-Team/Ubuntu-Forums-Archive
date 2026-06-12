---
title: "Need help: I deleted www-data user !!!!"
date: 2007-05-23
forum: Server Platforms
---

### Post by CoMfUcIoS on 2007-05-23
i need a way to re-create Apache user and group  ( www-data )!!!
i deleted them by mistake ! ( webmin )

---

### Post by CoMfUcIoS on 2007-05-23
never mind ... i just
```
sudo apt-get remove apache2 apache2-common --purge
```
and reinstall and comfigure it from the very begginin :)

---

### Post by craigp84 on 2007-05-23
groupadd -g 33 www-data
useradd -g www-data -c "www-data" -h /var/www -u 33 -s /bin/sh www-data

hth,

-c

---

### Post by CoMfUcIoS on 2007-05-25
Thanx a lot :) i ll remember it for the next time :D

---


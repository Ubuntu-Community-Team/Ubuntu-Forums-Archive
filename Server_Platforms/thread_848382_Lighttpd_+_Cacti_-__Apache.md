---
title: "Lighttpd + Cacti -  Apache"
date: 2008-07-03
forum: Server Platforms
---

### Post by marshal on 2008-07-03
Hi,

i want to run cacti on my homeserver (okay its just for fun and testing:rolleyes:)

at the moment i am running xubuntu 8.04 with a LLMP setup.

if i want to install cacti with

```
apt-get install cacti
```

the dependencies force me to install 
```
apache2-mpm-prefork apache2-utils apache2.2-common dbconfig-common libapache2-mod-php5 libapr1 libaprutil1 libphp-adodb librrd2 php5-snmp rrdtool snmp ttf-dejavu ttf-dejavu-extra
```

is there a way not to install all the apache stuff?

thx marshal

---

### Post by erwall on 2008-07-03
Cacti is web based, therefore must run on a webserver.

EDIT: Sorry, just saw you want to run it on lighttpd.

---


---
title: "difference between httpd and apache2 daemons"
date: 2005-04-03
forum: Server Platforms
---

### Post by 11evele on 2005-04-03
what is the difference between httpd and apache2 daemons?  

to start or stop them i use this

apache2 daemon
start: /etc/init.d/apache2 start
stop: /etc/init.d/apache2 stop

httpd daemon
start: /usr/local/apache2/bin/apachectl start
stop: /usr/local/apache2/bin/apachectl stop

apache2 daemon starts on boot and uses var/www/apache-default instead of usr/local/apache2/htdocs like httpd...i'm confused!!  does it even matter?? ieeejajajslksdfkhsdiou*O!&(*U!!!!

---

### Post by bihe on 2005-04-03
/etc/init.d/apache2  is the distribution specific start/stop script whereas
apachectl is from the apache group. the std. apache working dir is configured
in httpd.conf. this file is located in /etc/apache2/

---

### Post by defkewl on 2005-04-03
It's no difference, debian put it in /etc/init.d and name it to apache2.

---

### Post by 11evele on 2005-04-03
ok rad thank you for the replies!!!

---


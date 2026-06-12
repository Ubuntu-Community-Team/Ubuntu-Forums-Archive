---
title: "Apache run as"
date: 2010-01-15
forum: Server Platforms
---

### Post by tlsarles on 2010-01-15
Was just curious what user Apache2 runs as by default, also what group this user is a member of. Also, for extra credit, where could I go to see/find these settings. (Might help me answer my own questions in the future)

---

### Post by slakkie on 2010-01-15
egrep -ir "user|group" /etc/apache2/


/etc/apache2/apache2.conf:User ${APACHE_RUN_USER}
/etc/apache2/apache2.conf:Group ${APACHE_RUN_GROUP}

Have a look in that file :)

/etc/apache2/envvars:export APACHE_RUN_USER=www-data
/etc/apache2/envvars:export APACHE_RUN_GROUP=www-data

And this file as well :)

---

### Post by tlsarles on 2010-01-18
Exactly what I was looking for, thanks

---


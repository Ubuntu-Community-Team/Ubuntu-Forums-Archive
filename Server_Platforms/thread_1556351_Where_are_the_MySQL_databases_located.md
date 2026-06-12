---
title: "Where are the MySQL databases located?"
date: 2010-08-19
forum: Server Platforms
---

### Post by fred2028 on 2010-08-19
Hi, I want to move all of my MySQL databases to a different partition on my HDD. Where are they located? Also, am I right in thinking that if I move it I can just create a symlink where the DB used to be and point it to the new location, and it should work fine?

Ubuntu 10.04 LTS x64

Thanks!

---

### Post by lykeion on 2010-08-19
Maybe this will help:
[http://www.ubuntu-howto.info/howto/how-to-move-mysql-databases-to-another-location-partition-or-hard-drive](http://www.ubuntu-howto.info/howto/how-to-move-mysql-databases-to-another-location-partition-or-hard-drive)

Be sure to read the comments about user permissions/apparmor as well

---

### Post by brettg on 2010-08-20
You can find the location of the databases in the config file for mysql (/etc/my.cnf)

---


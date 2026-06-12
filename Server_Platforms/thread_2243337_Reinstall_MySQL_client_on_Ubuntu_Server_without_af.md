---
title: "Reinstall MySQL client on Ubuntu Server without affecting the MySQL-server."
date: 2014-09-08
forum: Server Platforms
---

### Post by paranoiid on 2014-09-08
I did a bit of a mistake. I made a mysql cleaning script to put into a crontab. I was going to move it to /usr/bin/mysqlclean/ but I tabbed a bit too fast and now I've replaced /usr/bin/mysql with the script. 

Can I safely reinstall or get the /usr/bin/mysql from an RPM without damaging the mysql daemon? If so, how?

---

### Post by konsole on 2014-09-09
To extract /usr/bin/mysql from the client core deb```
dpkg --fsys-tarfile ./mysql-client-core-5.5.deb | tar --wildcards -xf - ./usr/bin/mysql
```will extract the full path to the current directory. Move mysql to /usr/bin/ check permissions and you should be done.

---


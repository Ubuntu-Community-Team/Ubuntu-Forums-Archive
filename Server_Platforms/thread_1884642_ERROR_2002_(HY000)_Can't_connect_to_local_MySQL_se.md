---
title: "ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysq"
date: 2011-11-21
forum: Server Platforms
---

### Post by GioMBG on 2011-11-21
Hi All,
I hope some one can redirect me to some place where this porblem was REALLY SOLVED:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
thx
GioMBG

---

### Post by rubylaser on 2011-11-21
Did you make sure that the path and file exist, and that they're owned by mysql?
```
sudo mkdir /var/run/mysqld/
```
```
sudo touch /var/run/mysqld/mysqld.sock
```
```
sudo chown -R mysql /var/run/mysqld/
```

And restart
```
sudo /etc/init.d/mysql restart
```

---


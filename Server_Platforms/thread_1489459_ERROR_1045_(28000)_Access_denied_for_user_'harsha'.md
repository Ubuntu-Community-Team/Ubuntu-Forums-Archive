---
title: "ERROR 1045 (28000): Access denied for user 'harsha'@'localhost' (using password: NO)"
date: 2010-05-21
forum: Server Platforms
---

### Post by rejuvenate on 2010-05-21
hi, i have installed mysql in ubuntu 9.10 
i think i made some error while installing bcoz it is giving error:
ERROR 1045 (28000): Access denied for user 'harsha'@'localhost' (using password: NO)

when i am trying to run mysql as
shell> mysql

---

### Post by rejuvenate on 2010-05-21
i tried to solve it by following link
[HTML]http://www.debian-administration.org/articles/442[/HTML]

i am getting an error 
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

when i am running 
```
root@steve:~$ mysql --user=root mysql
```

---

### Post by cdenley on 2010-05-21
Going from "access denied" to "can't connect", it seems you're making things worse. Make sure mysql-server is running properly:
```

sudo /etc/init.d/mysql restart
sudo netstat -tlnp
nc -z -v -w 4 127.0.0.1 3306

```

Now, when you connect, you must provide the root password you chose when you installed mysql-server.
```

mysql -u root -p

```

---

### Post by BobVila on 2010-05-21
> **cdenley said:**
> Going from "access denied" to "can't connect", it seems you're making things worse. Make sure mysql-server is running properly:
```

sudo /etc/init.d/mysql restart
sudo netstat -tlnp
nc -z -v -w 4 127.0.0.1 3306

```Now, when you connect, you must provide the root password you chose when you installed mysql-server.
```

mysql -u root -p

```

Seconded. I'm wondering if the OP didn't try to initially start mysql without sudo...

---


---
title: "mysql error"
date: 2009-10-18
forum: Server Platforms
---

### Post by bigfas on 2009-10-18
I have Xampp installed and when I try to access it from terminal

```
mysql -h root -p
```

I get this

```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

so I've created the directory 

```
sudo mkdir /var/run/mysqld/
```

then the file

```

sudo touch /var/run/mysqld/mysqld.sock
```

and the ownership

```
sudo chown -R mysql /var/run/mysqld/
```

but now I get this
 
```

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (13)

```

---

### Post by Lars Noodén on 2009-10-20
To ask the obvious, is mysql running?

[INDENT][FONT="Courier New"]pgrep -l mysql
# OR
sudo /etc/init.d/mysql status[/FONT][/INDENT]

---

### Post by karlson on 2009-10-20
> **bigfas said:**
> I have Xampp installed and when I try to access it from terminal

```
mysql -h root -p
```



Are you sure that you want to connect to host "root"?

---

### Post by karlson on 2009-10-20
> **Lars Noodén said:**
> To ask the obvious, is mysql running?

[INDENT][FONT="Courier New"]pgrep -l mysql
# OR
sudo /etc/init.d/mysql status[/FONT][/INDENT]

One more to add to this one:

```

dpkg -l | grep mysql-server

```

Will check if mysql-server is even installed.

---

### Post by Lars Noodén on 2009-10-20
> **karlson said:**
> Are you sure that you want to connect to host "root"?

Probably a typo.

mysql -h 127.0.0.1 -u root -p thedatabase

---

### Post by sahabcse on 2009-10-20
paste the o/p of

sudo /etc/init.d/mysql restart

---


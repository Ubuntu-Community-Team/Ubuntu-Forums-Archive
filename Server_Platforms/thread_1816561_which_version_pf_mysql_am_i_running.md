---
title: "which version pf mysql am i running ?"
date: 2011-08-02
forum: Server Platforms
---

### Post by kalimojo on 2011-08-02
which version pf mysql am i running ?
how do i find out ?

---

### Post by shubham1 on 2011-08-02
create a php file with this as content.
echo phpinfo();

---

### Post by Wim Sturkenboom on 2011-08-02
In the mysql client, run the following query

```

mysql> **select version();**
+-----------+
| version() |
+-----------+
| 5.0.37    |
+-----------+
1 row in set (0.00 sec)

mysql>

```

---

### Post by kalimojo on 2011-08-03
> **Wim Sturkenboom said:**
> In the mysql client, run the following query

```

mysql> **select version();**
+-----------+
| version() |
+-----------+
| 5.0.37    |
+-----------+
1 row in set (0.00 sec)

mysql>

```

when i run mysql i get the following error

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

---

### Post by Wim Sturkenboom on 2011-08-03
> **kalimojo said:**
> when i run mysql i get the following error

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
You probably have a password set; when installing mysqld form the Ubuntu repositories, it will prompt you to set a password for the root user.

```

mysql -u root -p

```
and enter the password

---

### Post by kalimojo on 2011-08-03
> **Wim Sturkenboom said:**
> You probably have a password set; when installing mysqld form the Ubuntu repositories, it will prompt you to set a password for the root user.

```

mysql -u root -p

```and enter the password

thanks

```

mysql> select version();
+-----------------+
| version()       |
+-----------------+
| 5.1.54-1ubuntu4 |
+-----------------+
1 row in set (0.00 sec)

mysql>

```

---

### Post by Wim Sturkenboom on 2011-08-03
If you thread is solved, please mark it as solved using the thread tools just above the first post

> **kalimojo said:**
> thanks

mysql> select version();
+-----------------+
| version()       |
+-----------------+
| 5.1.54-1ubuntu4 |
+-----------------+
1 row in set (0.00 sec)

mysql>
Learn to use code tags ;) It can be useful if you want to maintain the formatting.
[noparse]```

mysql> select version();
+-----------------+
| version()       |
+-----------------+
| 5.1.54-1ubuntu4 |
+-----------------+
1 row in set (0.00 sec)

mysql>

```[/noparse]

will result in 
```

mysql> select version();
+-----------------+
| version()       |
+-----------------+
| 5.1.54-1ubuntu4 |
+-----------------+
1 row in set (0.00 sec)

mysql>

```

---


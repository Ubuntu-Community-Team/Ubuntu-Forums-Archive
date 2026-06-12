---
title: "I can't seem to create a database and table"
date: 2009-01-19
forum: Server Platforms
---

### Post by Fertech on 2009-01-19
I can't seem to create a database and table
```

mysql> CREATE DATABASE accounting;
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'accounting'
mysql> 
```

---

### Post by albinootje on 2009-01-19
> **Fertech said:**
> I can't seem to create a database and table
```

mysql> CREATE DATABASE accounting;
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'accounting'
mysql> 
```

Does that database already exist ?
Try :
```

mysql> show databases;

```

---

### Post by Fertech on 2009-01-19
mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
+--------------------+
1 row in set (0.00 sec)

mysql>

---

### Post by Fertech on 2009-01-19
The only this i did was set a password when i install mysql, but i don't know if im did it under root or fertech.

---

### Post by albinootje on 2009-01-19
> **Fertech said:**
> The only this i did was set a password when i install mysql, but i don't know if im did it under root or fertech.

To create new databases in mysql you have to be root (the mysql root)
(or have a certain user priviledged to do so I assume).

Try this instead :

1) close your mysql session

2) start it :
```

mysql -u root -p

```

---

### Post by Fertech on 2009-01-19
fertech@fertech-desktop:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 46
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>

---

### Post by albinootje on 2009-01-19
> **Fertech said:**
> fertech@fertech-desktop:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 46
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>

Good.
Are you getting the same error or .. ?

---

### Post by Iowan on 2009-01-19
Try creating the database again - the error message "...user ''@'localhost'" suggests that you weren't logged in.

---

### Post by Fertech on 2009-01-20
ok now i can create databases, all i had to do is log on as root  and -pwd

---


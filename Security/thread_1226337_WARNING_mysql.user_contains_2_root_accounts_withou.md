---
title: "WARNING: mysql.user contains 2 root accounts without password! Uh-Oh, how do I fix!"
date: 2009-07-29
forum: Security
---

### Post by MechaMechanism on 2009-07-29
SOLVED

I had a lot of problems setting up mysql and had to reset my password.  Is there a way to see how many root accounts there are in total.  I think I have 1 root account with a password and 2 without.  How would I go about deleting the 2 passwordless accounts or even finding them?

---

### Post by unutbu on 2009-07-29
If you have phpmyadmin installed, you simply click on the "mysql" database, click the "user" table, and click the "X" (delete) icon next to the root accounts you wish to remove.

If you don't have phpmyadmin installed, here is a command-line way:
(names and passwords have been altered to protect the innocent)

```
% mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 104
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

```
```
mysql> use mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
```
```

mysql> select Host,Password from user where User='root';
+-----------+-------------------------------------------+
| Host      | Password                                  |
+-----------+-------------------------------------------+
| localhost | *XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX | 
| hostname  | *XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX | 
| 127.0.0.1 | *XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX | 
+-----------+-------------------------------------------+
3 rows in set (0.00 sec)
```

```
mysql> delete from user where User='root' and Host='hostname';
```

---

### Post by MechaMechanism on 2009-07-30
Thank you very much.  I used the command line way and it worked like a charm.

---


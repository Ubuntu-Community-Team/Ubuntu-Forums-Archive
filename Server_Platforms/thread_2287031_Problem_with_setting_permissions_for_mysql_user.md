---
title: "Problem with setting permissions for mysql user"
date: 2015-07-16
forum: Server Platforms
---

### Post by peter1897 on 2015-07-16
I logon as root and created new mysql user **demo** with the command:
```
create user 'demo'@'localhost' identified by 'demo';
```

Then i granted all permissions to the user with the command:
```
grant all privileges on * . * to 'demo'@'localhost';
```

Then i created a new database test:
```
create database test;
```

```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| phpmyadmin         |
| test               |
| wordpress          |
+--------------------+


```

Now, i want to remove all permissions from user demo on database **test** so it can't delete of modify it. I used this command:
```
revoke all privileges on test.* from 'demo'@'localhost';
```

but i get this error:
```
ERROR 1141 (42000): There is no such grant defined for user 'demo' on host 'localhost'
```

Why i am getting this error? When i am logged in as demo i am able to delete the database **test** with the command:
```
drop database test;
```
so the user demo have the permission to delete the database.

---

### Post by nerdtron on 2015-07-16
What is the output of:

show grants for demo@'localhost';

---

### Post by peter1897 on 2015-07-16
The output is this:  

```
mysql> show grants for demo@'localhost';
+----------------------------------------------------------------------------------------------------------------------+
| Grants for demo@localhost                                                                                            |
+----------------------------------------------------------------------------------------------------------------------+
| GRANT ALL PRIVILEGES ON *.* TO 'demo'@'localhost' IDENTIFIED BY PASSWORD '*C142FB215B6E05B7C134B1A653AD4B455157FD79' |
+----------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)

```

---

### Post by peter1897 on 2015-07-16
If i try to remove only a specific permission i get the same error:

```
mysql> revoke drop on test.* from 'demo'@'localhost';
ERROR 1141 (42000): There is no such grant defined for user 'demo' on host 'localhost'
```

And if i check the user permissions in information schema it shows for user demo that it doesn't have any permissions, i don't know why:

```
mysql> SELECT * FROM information_schema.user_privileges;
+--------------------------------+---------------+-------------------------+--------------+
| GRANTEE                        | TABLE_CATALOG | PRIVILEGE_TYPE          | IS_GRANTABLE |
+--------------------------------+---------------+-------------------------+--------------+
| 'root'@'localhost'             | NULL          | SELECT                  | YES          |
| 'root'@'localhost'             | NULL          | INSERT                  | YES          |
| 'root'@'localhost'             | NULL          | UPDATE                  | YES          |
| 'root'@'localhost'             | NULL          | DELETE                  | YES          |
| 'root'@'localhost'             | NULL          | CREATE                  | YES          |
| 'root'@'localhost'             | NULL          | DROP                    | YES          |
| 'root'@'localhost'             | NULL          | RELOAD                  | YES          |
| 'root'@'localhost'             | NULL          | SHUTDOWN                | YES          |
| 'root'@'localhost'             | NULL          | PROCESS                 | YES          |
| 'root'@'localhost'             | NULL          | FILE                    | YES          |
| 'root'@'localhost'             | NULL          | REFERENCES              | YES          |
| 'root'@'localhost'             | NULL          | INDEX                   | YES          |
| 'root'@'localhost'             | NULL          | ALTER                   | YES          |
| 'root'@'localhost'             | NULL          | SHOW DATABASES          | YES          |
| 'root'@'localhost'             | NULL          | SUPER                   | YES          |
| 'root'@'localhost'             | NULL          | CREATE TEMPORARY TABLES | YES          |
| 'root'@'localhost'             | NULL          | LOCK TABLES             | YES          |
| 'root'@'localhost'             | NULL          | EXECUTE                 | YES          |
| 'root'@'localhost'             | NULL          | REPLICATION SLAVE       | YES          |
| 'root'@'localhost'             | NULL          | REPLICATION CLIENT      | YES          |
| 'root'@'localhost'             | NULL          | CREATE VIEW             | YES          |
| 'root'@'localhost'             | NULL          | SHOW VIEW               | YES          |
| 'root'@'localhost'             | NULL          | CREATE ROUTINE          | YES          |
| 'root'@'localhost'             | NULL          | ALTER ROUTINE           | YES          |
| 'root'@'localhost'             | NULL          | CREATE USER             | YES          |
| 'root'@'localhost'             | NULL          | EVENT                   | YES          |
| 'root'@'localhost'             | NULL          | TRIGGER                 | YES          |
| 'phpmyadmin'@'localhost'       | NULL          | USAGE                   | NO           |
| 'root'@'127.0.0.1'             | NULL          | SELECT                  | YES          |
| 'root'@'127.0.0.1'             | NULL          | INSERT                  | YES          |
| 'root'@'127.0.0.1'             | NULL          | UPDATE                  | YES          |
| 'root'@'127.0.0.1'             | NULL          | DELETE                  | YES          |
| 'root'@'127.0.0.1'             | NULL          | CREATE                  | YES          |
| 'root'@'127.0.0.1'             | NULL          | DROP                    | YES          |
| 'root'@'127.0.0.1'             | NULL          | RELOAD                  | YES          |
| 'root'@'127.0.0.1'             | NULL          | SHUTDOWN                | YES          |
| 'root'@'127.0.0.1'             | NULL          | PROCESS                 | YES          |
| 'root'@'127.0.0.1'             | NULL          | FILE                    | YES          |
| 'root'@'127.0.0.1'             | NULL          | REFERENCES              | YES          |
| 'root'@'127.0.0.1'             | NULL          | INDEX                   | YES          |
| 'root'@'127.0.0.1'             | NULL          | ALTER                   | YES          |
| 'root'@'127.0.0.1'             | NULL          | SHOW DATABASES          | YES          |
| 'root'@'127.0.0.1'             | NULL          | SUPER                   | YES          |
| 'root'@'127.0.0.1'             | NULL          | CREATE TEMPORARY TABLES | YES          |
| 'root'@'127.0.0.1'             | NULL          | LOCK TABLES             | YES          |
| 'root'@'127.0.0.1'             | NULL          | EXECUTE                 | YES          |
| 'root'@'127.0.0.1'             | NULL          | REPLICATION SLAVE       | YES          |
| 'root'@'127.0.0.1'             | NULL          | REPLICATION CLIENT      | YES          |
| 'root'@'127.0.0.1'             | NULL          | CREATE VIEW             | YES          |
| 'root'@'127.0.0.1'             | NULL          | SHOW VIEW               | YES          |
| 'root'@'127.0.0.1'             | NULL          | CREATE ROUTINE          | YES          |
| 'root'@'127.0.0.1'             | NULL          | ALTER ROUTINE           | YES          |
| 'root'@'127.0.0.1'             | NULL          | CREATE USER             | YES          |
| 'root'@'127.0.0.1'             | NULL          | EVENT                   | YES          |
| 'root'@'127.0.0.1'             | NULL          | TRIGGER                 | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | SELECT                  | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | INSERT                  | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | UPDATE                  | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | DELETE                  | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | CREATE                  | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | DROP                    | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | RELOAD                  | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | SHUTDOWN                | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | PROCESS                 | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | FILE                    | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | REFERENCES              | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | INDEX                   | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | ALTER                   | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | SHOW DATABASES          | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | SUPER                   | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | CREATE TEMPORARY TABLES | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | LOCK TABLES             | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | EXECUTE                 | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | REPLICATION SLAVE       | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | REPLICATION CLIENT      | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | CREATE VIEW             | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | SHOW VIEW               | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | CREATE ROUTINE          | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | ALTER ROUTINE           | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | CREATE USER             | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | EVENT                   | YES          |
| 'debian-sys-maint'@'localhost' | NULL          | TRIGGER                 | YES          |
| 'max'@'localhost'              | NULL          | SELECT                  | NO           |
| 'max'@'localhost'              | NULL          | INSERT                  | NO           |
| 'max'@'localhost'              | NULL          | UPDATE                  | NO           |
| 'max'@'localhost'              | NULL          | DELETE                  | NO           |
| 'max'@'localhost'              | NULL          | CREATE                  | NO           |
| 'max'@'localhost'              | NULL          | DROP                    | NO           |
| 'max'@'localhost'              | NULL          | RELOAD                  | NO           |
| 'max'@'localhost'              | NULL          | SHUTDOWN                | NO           |
| 'max'@'localhost'              | NULL          | PROCESS                 | NO           |
| 'max'@'localhost'              | NULL          | FILE                    | NO           |
| 'max'@'localhost'              | NULL          | REFERENCES              | NO           |
| 'max'@'localhost'              | NULL          | INDEX                   | NO           |
| 'max'@'localhost'              | NULL          | ALTER                   | NO           |
| 'max'@'localhost'              | NULL          | SHOW DATABASES          | NO           |
| 'max'@'localhost'              | NULL          | SUPER                   | NO           |
| 'max'@'localhost'              | NULL          | CREATE TEMPORARY TABLES | NO           |
| 'max'@'localhost'              | NULL          | LOCK TABLES             | NO           |
| 'max'@'localhost'              | NULL          | EXECUTE                 | NO           |
| 'max'@'localhost'              | NULL          | REPLICATION SLAVE       | NO           |
| 'max'@'localhost'              | NULL          | REPLICATION CLIENT      | NO           |
| 'max'@'localhost'              | NULL          | CREATE VIEW             | NO           |
| 'max'@'localhost'              | NULL          | SHOW VIEW               | NO           |
| 'max'@'localhost'              | NULL          | CREATE ROUTINE          | NO           |
| 'max'@'localhost'              | NULL          | ALTER ROUTINE           | NO           |
| 'max'@'localhost'              | NULL          | CREATE USER             | NO           |
| 'max'@'localhost'              | NULL          | EVENT                   | NO           |
| 'max'@'localhost'              | NULL          | TRIGGER                 | NO           |
| 'demo'@'localhost'             | NULL          | SELECT                  | NO           |
| 'demo'@'localhost'             | NULL          | INSERT                  | NO           |
| 'demo'@'localhost'             | NULL          | UPDATE                  | NO           |
| 'demo'@'localhost'             | NULL          | DELETE                  | NO           |
| 'demo'@'localhost'             | NULL          | CREATE                  | NO           |
| 'demo'@'localhost'             | NULL          | DROP                    | NO           |
| 'demo'@'localhost'             | NULL          | RELOAD                  | NO           |
| 'demo'@'localhost'             | NULL          | SHUTDOWN                | NO           |
| 'demo'@'localhost'             | NULL          | PROCESS                 | NO           |
| 'demo'@'localhost'             | NULL          | FILE                    | NO           |
| 'demo'@'localhost'             | NULL          | REFERENCES              | NO           |
| 'demo'@'localhost'             | NULL          | INDEX                   | NO           |
| 'demo'@'localhost'             | NULL          | ALTER                   | NO           |
| 'demo'@'localhost'             | NULL          | SHOW DATABASES          | NO           |
| 'demo'@'localhost'             | NULL          | SUPER                   | NO           |
| 'demo'@'localhost'             | NULL          | CREATE TEMPORARY TABLES | NO           |
| 'demo'@'localhost'             | NULL          | LOCK TABLES             | NO           |
| 'demo'@'localhost'             | NULL          | EXECUTE                 | NO           |
| 'demo'@'localhost'             | NULL          | REPLICATION SLAVE       | NO           |
| 'demo'@'localhost'             | NULL          | REPLICATION CLIENT      | NO           |
| 'demo'@'localhost'             | NULL          | CREATE VIEW             | NO           |
| 'demo'@'localhost'             | NULL          | SHOW VIEW               | NO           |
| 'demo'@'localhost'             | NULL          | CREATE ROUTINE          | NO           |
| 'demo'@'localhost'             | NULL          | ALTER ROUTINE           | NO           |
| 'demo'@'localhost'             | NULL          | CREATE USER             | NO           |
| 'demo'@'localhost'             | NULL          | EVENT                   | NO           |
| 'demo'@'localhost'             | NULL          | TRIGGER                 | NO           |
+--------------------------------+---------------+-------------------------+--------------+
136 rows in set (0.02 sec)

```

---

### Post by nerdtron on 2015-07-16
You can't revoke only "drop" since you granted all privileges. What you can do is explicitly add each privilege to that user and then revoke specific privileges. You can't remove the grant all privileges since that is only the grants granted left for that user. Try to add some other grants then revoke the grant all privileges.

---

### Post by peter1897 on 2015-07-17
I found that to remove all global privileges granted to a user you have to delete the user and recreated it again and give him permissions only to specific databases, but not globally. Granting all privileges globally to a user is not recommended for security reasons.

---


---
title: "mysql: ERROR 1133 (42000): Can't find any matching row in the user table"
date: 2016-04-15
forum: Server Platforms
---

### Post by shamsat on 2016-04-15
I installed the ubuntu 16.04 beta2, want to setup the roundcube mail for my mail serer:
> 
mysql> CREATE DATABASE roundcubemail DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci; 

that work ok now i run this command but get error:
> 
mysql> GRANT ALL PRIVILEGES ON roundcubemail.* TO roundcube@localhost IDENTIFIED BY '';
ERROR 1133 (42000): Can't find any matching row in the user table

Also i run this command and get error:
> 
mysql>SET PASSWORD FOR root@'127.0.0.1' = PASSWORD('');
ERROR 1133 (42000): Can't find any matching row in the user table

While configuration by dpkg i set the empty password for mysql root.

---

### Post by howefield on 2016-04-15
Thread moved to the "*Server Platforms*" forum.

---

### Post by Habitual on 2016-04-15
You missed some of the GRANT statement. Try
```
GRANT ALL PRIVILEGES ON roundcubemail.* TO roundcube@localhost IDENTIFIED BY 'password'; flush privileges;
```
where 'password' should be in this format 'the_word'

Should say 1 row updated.

---

### Post by darkod on 2016-04-16
Also I don't see mentioned whether you created the roundcube user in mysql. I see you created the database, but to be able to grant privileges the user has to be created too. On top of what Habitual said above, to correct the syntax of the GRANT statement.

---


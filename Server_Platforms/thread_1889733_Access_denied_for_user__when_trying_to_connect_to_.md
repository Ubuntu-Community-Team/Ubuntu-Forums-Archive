---
title: "Access denied for user  when trying to connect to mysql"
date: 2011-12-01
forum: Server Platforms
---

### Post by Fertech on 2011-12-01
I type this code in .php place this in my dir /var/www and I get Access denied for user I'm using Ubuntu 10.04LTS can someone help me with this issue.


```
 <?php
mysql_connect("localhost", "admin", "1admin") or die(mysql_error());
echo "Connected to MySQL<br />";
mysql_select_db("test") or die(mysql_error());
echo "Connected to Database";
?>
 
```

---

### Post by agillator on 2011-12-01
First, where are you getting the error, attempting to connect or attempting to select the database?

Second, was the php you are using compiled for mysql? Check phpinfo for that. If not you will need to recompile or obtain a version that is compiled for mysql.

Third, as silly as it may sound, are you sure 'admin' is a valid user, is allowed to use that database, and is the password correct? Don't assume, check the user table in mysql, check the permissions, and if permissions are limited check the db table for permissions for that particular database.

If this doesn't help, let us know what you find out and we'll go from there.

---

### Post by Fertech on 2011-12-02
I open a terminal and type:

```
mysql -u root -p

```

then confirm the password. I replace my user name with root

---

### Post by brighty22 on 2011-12-02
Put *error_reporting(-1)* at the top of your php code, then post the complete error message.

---


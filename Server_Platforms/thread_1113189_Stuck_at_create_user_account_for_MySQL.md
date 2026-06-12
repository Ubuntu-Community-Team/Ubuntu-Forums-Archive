---
title: "Stuck at create user account for MySQL"
date: 2009-04-01
forum: Server Platforms
---

### Post by Grey08 on 2009-04-01
I have fresh installed Mysql with php5, and i was following the instruction at page [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP). The problem is, i couldn't get the exact output as the page shown, such as 

nano /etc/mysql/my.cnf

mysql -u root

mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');


It just kept saying  access denied for user 'root'@'localhost'

and i saw the info at other page, it says need to add a line at somewhereelse, but, they didn't mention which file and under which directory to edit. So i have been stuck for few days and still can not figure out how to create an user for mysql and to add a new database.


Anyone can please point out the problem? Thanks!

Regards,
Grey08

---

### Post by mregister on 2009-04-01
mysql -u [your username, assuming it's an admin user] -p 

it will then ask for your password and just use the one for the user you are logged in as. If you are an admin then that will get you to mysql prompt.

---

### Post by cdenley on 2009-04-01
To login as root on mysql:
```

mysql -u root -p

```
Use the password you entered while installing mysql-server. If you forgot it:
```

sudo dpkg-reconfigure mysql-server-5.0

```

It sounds like that guide is outdated. I think mysql used to have no root password by default, as that guide sounds like it assumes. That is not the case for current versions of ubuntu. You could skip that step of the guide.

---


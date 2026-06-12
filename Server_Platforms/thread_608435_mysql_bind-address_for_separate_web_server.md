---
title: "mysql bind-address for separate web server"
date: 2007-11-10
forum: Server Platforms
---

### Post by Pitt Stains on 2007-11-10
Hello,

I have a two-machine set up.  One machine runs Apache/PHP.  The other machine runs MySQL.

I want to set up the MySQL server to accept connections from ONLY the Apache/PHP box.

My understanding is the bind-address line in the my.cnf file determines which IP address the server will accept connections from.  If this is the case, am I supposed to use the private IP address of the web server, or the public IP address (with router set to forward port 3306 accordingly)?

Thanks.  If I'm misinterpreting the purpose of the bind-address option, please set me straight!

-Pitt

---

### Post by Wallace on 2007-11-10
Can the Apache server connect to the MySQL server using the private IP? If it can, you should just be able to bind MySQL to that IP and not your public IP.

---

### Post by k_grdn on 2007-11-10
Hi Pitt Stains,

The bind-address option is the address which the mysql deamon will listen and accept connections on, i.e the address of your mysql server.

You need to grant rights to a user from your web server private address on the desired table, if both are behind your router.

Regards,

k_grdn

---

### Post by Pitt Stains on 2007-11-11
Thanks for the responses.  So what I take from your post, k_grdn, is that changing the bind-address value is not the proper way to control where the database server is accessed from, and that the proper way to do so is to update the users table to indicate where each user may connect from.  Is that right?

> **k_grdn said:**
> Hi Pitt Stains,

The bind-address option is the address which the mysql deamon will listen and accept connections on, i.e the address of your mysql server.

You need to grant rights to a user from your web server private address on the desired table, if both are behind your router.

Regards,

k_grdn

---

### Post by k_grdn on 2007-11-12
Hi,

Your understanding is correct.

To Grant access to your database use something similar to the following:

New database;

mysql> CREATE DATABASE foo;
mysql> GRANT ALL ON foo.* TO bar@'192.168.1.10' IDENTIFIED BY 'PASSWORD';

Existing database;

mysql> update db set Host='192.168.1.10' where Db='exist-db';
mysql> update user set Host='192.168.1.10' where user='exist-user';

Obviously substitute db, user, host etc... with your own values.

Regards,

k_grdn

---


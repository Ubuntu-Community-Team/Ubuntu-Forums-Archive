---
title: "phpmyadin/mysql/apache config problem"
date: 2009-01-06
forum: Server Platforms
---

### Post by aarone720 on 2009-01-06
Hi,

I'm new to this forum and to web dev in general. I'm trying to set up phpmyadmin on a lAMP setup. I am getting the following error when trying to log into phpmyadmin for the first time:

error: 'Host '192.168.1.100' is not allowed to connect to this MySQL server'

in addition I also get the following error as well:

Cannot load mcrypt extension. Please check your PHP configuration.

Not sure if this is the right forum to post, but thought i'd start here. 

I have tried some troubleshooting in terminal and received this additional info:

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'aaronevans'@'localhost' (using password: NO)'
aaron:~ aaronevans$ mysqladmin --protocol=socket --socket=/tmp/mysql.sock version


please help
Please help

---

### Post by cariboo on 2009-01-06
To connect to mysql from your server type at the prompt:

```
mysql -u root -p
```

where the password is the one you set when you installed mysql. To connect remotely, you have to set up a user that has the privileges to connect from a remote computer. What I always do is set up a user using the following commands. You have to be in the mysql console to to this:

```
grant all privileges on *.* to <user>@'localhost' identified by '<password>' with grant option;

grant all privileges on *.* to <user>@'%' identified by '<password>' with grant option;
```

In the second command the @'%' part of the command allows for remote connection.

Jim

---

### Post by aarone720 on 2009-01-06
ok does it matter that this is on my personal mac server. I'm not having this problem connecting remotely, just from my localhost. Also, what does it mean to be in the mysql console to do this? Thanks for your time.

---

### Post by Iowan on 2009-01-06
> **aarone720 said:**
> ok does it matter that this is on my personal mac server. I'm not having this problem connecting remotely, just from my localhost. Also, what does it mean to be in the mysql console to do this? Thanks for your time.You will be in the mysql console after you (successfully) run the command (from a terminal)```
mysql -u root -p
```
If you're not having the problem remotely, you can use phpmyadmin to check privileges (I'll have to review my text to see how).

(Oops, you said it didn't work on first attempt)

---


---
title: "Can't get into MySQL prompt as root"
date: 2008-01-30
forum: Server Platforms
---

### Post by lodp on 2008-01-30
Hi everyone,

This is driving me **NUTS** here, I hope somebody can help me.

I've got a clean install of 7.10 server, and I just installed mysql-server. I was asked to provide a root password for mysql in the setup process of mysql-server-5.0, which I did. However, when I type
```

mysql -u root -p
``` ..and I type in the password I provided in setup, I get the following: ```
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
``` First I thought I had mis-typed the password when setting it up, so i purged all mysql related packages (as determined by "dpkg -l mysql*"), and installed it anew with "apt-get install mysql-server". I provide a root password again, but when I try to login, it's the same story.

Anyone got a tip for me here? I've screwed around with this for hours, and I really should have this server up and running by tomorrow..

---

### Post by faulkes on 2008-01-30
Noting that you have said you did set a root password, have you just tried to do a 

mysql -u root 

and see what happens?

---

### Post by lsmobrian on 2008-01-30
Didnt know if you had looked on the mysql site, here is a link to that error and some things to try

[http://dev.mysql.com/doc/refman/5.0/en/access-denied.html](http://dev.mysql.com/doc/refman/5.0/en/access-denied.html)

---

### Post by lodp on 2008-01-30
> Noting that you have said you did set a root password, have you just tried to do a

mysql -u root 

I had tried that, but then I got the same error message as above, but with "(using password: NO)". I did enter a root password when prompted in the setup process of mysql-server-5.0

Anyway, I just found out what's wrong. I always do AFTER I've posted here, and it always makes it look like I haven't done my homework before posting, which I did, I swear.

I'm still a little confused, but it seems that the installation of mysql-server-5.0 just **didn't create a root user in the first place**.

I roughly followed [This Guide]("http://www.cyberciti.biz/tips/recover-mysql-root-password.html"). [This here]("http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html") also helped.
```

/etc/init.d/mysql stop
```
```
mysqld_safe --skip-grant-tables &
```
```
mysql -u root
```
```
use mysql;
```

Now I went to check out the user table:

```
select user, host from user;
```

which got me the following:

```
+------------------+-----------+
| user             | host      |
+------------------+-----------+
| debian-sys-maint | localhost |
+------------------+-----------+
1 row in set (0.00 sec)
```

So there's no root user, see? So I went to create one. First it seemed necessary to do this:

```
flush privileges;
```
```
GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' IDENTIFIED BY '<my password>'; 
```

```
quit
```
```
 /etc/init.d/mysql stop
```
```
 /etc/init.d/mysql start
```

And voilà, it's working, I can log in. I don't really understand every step of what I did, but I can move on now :)

Is this a bug of some sort? How can I end up without a root user after doing a clean install of mysql-server-5.0 (and after even having been prompted to choose a password for root in the process?).

---

### Post by tlcoffee on 2008-01-30
lol, looks like you beat me to it ;-)

Nice work

---

### Post by lodp on 2008-01-30
it's the intention that counts, so thanks :)

i still think this is totally nuts. gonna file a bug as soon as i got some time on my hands.

---


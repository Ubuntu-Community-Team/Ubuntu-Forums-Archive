---
title: "Can't access MySQL with root"
date: 2010-12-11
forum: Server Platforms
---

### Post by flamegrilled on 2010-12-11
Hey everyone.

I'm running an Ubuntu 9.04 Minimal server and trying to get MySQL to work correctly. But when I try to access MySQL with the root user it doesn't want to.

```

mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```And I'm using the correct password. I've looked around for solutions and tried every method I found to reset the root password, but it didn't work. 

Maybe there's something I'm missing... any help?

thank you

---

### Post by Vegan on 2010-12-11
check your caplocks and if needed, try another keyboard

---

### Post by rajeevisonline on 2010-12-11
please check if a firewall is not blocking your server...

more often than not this is an issue involving security so since you tried resetting root password..try making changes in your security policy...changing ports firewall

---

### Post by theDaveTheRave on 2010-12-13
Flamegrilled,

what exactly is the procedure you where doing?

was it simply a case of securing the MySQL server post install?

If you are attempting the first initial connection to Mysql you should be able to connect using
```

mysql -u root

```
you do not need the '-p' switch as the passwords immediately post install are blank.

If however you have already done this, that is different.

You may also need to log in using sudo
```

sudo mysql -u root

```
otherwise you may not be able to write the changes to the file - this is particularly the case if you are using the mysql supplied GUI tools, If you are using php-myadmin you may have a similar issue - don't know I've never used, I've always done my user admin via the CLI or the MySQL gui.

David

---

### Post by rubylaser on 2010-12-14
If you already secured mysql by putting in a password, and it's not working, you'll need to reset the password.

Log in as root and stop the mysql daemon. Now lets start up the mysql daemon and skip the grant tables which store the passwords.
```
sudo -i
```
```
/etc/init.d/mysql stop
```
```
mysqld_safe --skip-grant-tables
```

You should see mysql start up successfully.  Now you should be able to connect to mysql without a password. Open a new terminal tab, then do the rest of these...

```
sudo -i
```
```
mysql --user=root mysql
```
```
update user set Password=PASSWORD('new-password') where user='root';
flush privileges;
exit;
```

Now, ctrl+c out of the msyqd_safe, and restart mysql.

```
/etc/init.d/mysql start
```

---


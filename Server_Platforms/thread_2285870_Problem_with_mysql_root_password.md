---
title: "Problem with mysql root password"
date: 2015-07-08
forum: Server Platforms
---

### Post by erok2 on 2015-07-08
Get this when i try to set mysql password for localhost, what shall I try to do instead?

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

---

### Post by nerdtron on 2015-07-08
Did you already setup a password for mysql root user? Usually you are asked to provide the mysql root password when you install mysql.

To login as mysql root if you haven't setup a password yet.
```
mysql -uroot
```

To login as mysql and then input the root password.
```
mysql -uroot -p 
```

To RESET the forgotten root password, run the following sequences.
> How to reset the root password for mysql:
###Stop mysql
1. sudo service mysqld stop

### Be sure that mysqld is stopped
1.1 sudo service mysqld status

###Do not proceed on the next step if it says myslqd is running. 
###Run mysql on safe mode
2. sudo mysqld_safe --skip-grant-tables &

###Login as root to mysql safe mode (no password needed here)
3. mysql -u root

###On mysql prompt, run the commands inside mysql to reset the password
4. mysql> use mysql;
mysql> update user set password=PASSWORD("***NEW-ROOT-PASSWORD***") where User='root';
mysql> flush privileges;
mysql> quit

###Stop mysql safe mode
5. sudo service mysqld stop

###Start mysql on normal mode
6. sudo service mysqld start

###Login to mysql as root using the new password
7. mysql -u root -p


---

### Post by erok2 on 2015-07-09
Thanks, I tried, but this came up, i have messed up something in the mysql system, nothing i try don't work!!
what shall I try to do, to fix this big problem, I have with mysql???

I have even uninstalled the whole mysql - from scratch, I can not set mysql root password at all, the system deny this when I try to installing it again!!

```

erok@eriks-dator:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
erok@eriks-dator:~$ 

```


```
erok@eriks-dator:~$ service mysql stop
stop: Unknown job: mysql
erok@eriks-dator:~$
```

```

erok@eriks-dator:~$ mysqld_safe --skip-grant-tables &
[1] 7357
erok@eriks-dator:~$ 150709 08:10:33 mysqld_safe Can't log to error log and syslog at the same time.  Remove all --log-error configuration options for --syslog to take effect.
150709 08:10:33 mysqld_safe Logging to '/var/log/mysql/error.log'.
cat: /var/run/mysqld/mysqld.pid: Permission denied
rm: cannot remove &#8216;/var/run/mysqld/mysqld.pid&#8217;: Permission denied
150709 08:10:33 mysqld_safe Fatal error: Can't remove the pid file:
/var/run/mysqld/mysqld.pid
Please remove it manually and start /usr/bin/mysqld_safe again;
mysqld daemon not started
/usr/bin/mysqld_safe: 126: /usr/bin/mysqld_safe: cannot create /var/log/mysql/error.log: Permission denied
mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
[1]+  Exit 1                  mysqld_safe --skip-grant-tables
erok@eriks-dator:~$ 

```

---

### Post by nerdtron on 2015-07-09
You'll need to reset the mysqld root password. I've update my previous. Try to start from Step 1, and don't proceed on step 2 until you are sure that mysqld is not running.

Any error or problem you encountered on the steps, post back here.

---

### Post by erok2 on 2015-07-15
I has reset password, but when I tried this for wordpress :

```
http://localhost/wordpress/wp-admin/setup-config.php
```

****************************

I get this

> [h=1]Forbidden[/h] You don't have permission to access /wordpress/wp-admin/setup-config.php on this server.
 [HR][/HR] Apache/2.4.7 (Ubuntu) Server at localhost Port 80


What can I try to solve the problem?

---

### Post by QIII on 2015-07-15
Hello!

You have moved on to a different subject than your initial post.  It is best to create one thread for one subject to avoid confusion.   With your original title, you are going to get people trying to help with mysql, which is not your current problem.

I would suggest starting a new thread with regard to this new question.

By the way, if you are trying to reach that url from your browser, I should very much hope you are getting a 403 Forbidden error!

---


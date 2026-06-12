---
title: "can't set mysql password -- it stays blank?"
date: 2009-04-29
forum: Server Platforms
---

### Post by shadowfirebird on 2009-04-29
I have a mysql user ampadmin which I set up in phpmyadmin to have a password.  That doesn't seem to have worked, however:

```
sfbd@cally:~$ mysql -uampadmin -pfred
ERROR 1045 (28000): Access denied for user 'ampadmin'@'localhost' (using password: YES)
sfbd@cally:~$
sfbd@cally:~$ mysql -uampadmin
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 224
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> set password for ampadmin@cally = password('fred');
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'mysql'
mysql> \r mysql
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'mysql'
mysql> Aborted
```

So, it looks as if when I try to log in as ampadmin I get a login with a blank username?  Or is something else going on here?  

Whatever, I certainly can't login using the password I set.

Any suggestions greatfully received.

---

### Post by terazen on 2009-04-29
Have you tried logging in as root and resetting the password?

mysql -u root -p
<enter password here>
use mysql;
update user set password=PASSWORD("newpassword") where User='ampadmin';
flush privileges;
quit;

---

### Post by shadowfirebird on 2009-04-29
I'm afraid so.

```
sfbd@cally:~$ mysql -uroot -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 237
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> update mysql.user set password=password('fred') where user='ampadmin';
Query OK, 0 rows affected (0.03 sec)
Rows matched: 1  Changed: 0  Warnings: 0

mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)

mysql> \q
Bye
sfbd@cally:~$ mysql -uampadmin
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 238
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>
```

---

### Post by terazen on 2009-04-29
Can you not change the passwords for any other users, or is it just the ampadmin?

---

### Post by shadowfirebird on 2009-04-29
Good question.  Unfortunately the only existing users in this database are the debian ones (which I'm loath to screw with because I don't know what they're for) the mythtv user (which if I screw with no-one gets to watch TV!) and the root user (which I'm just not going anywhere near right now).

However if I add a new user, it shows exactly the same behaviour:

```
sfbd@cally:~$ mysql -uroot -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 252
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> use mysql
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> create user test identified by 'fred';
Query OK, 0 rows affected (0.02 sec)

mysql> \q
Bye
sfbd@cally:~$
sfbd@cally:~$ mysql -utest -pfred
ERROR 1045 (28000): Access denied for user 'test'@'localhost' (using password: YES)
sfbd@cally:~$
sfbd@cally:~$ mysql -utest
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 254
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>
```

On the other hand, it shows the same behaviour with user names that are complete nonsense! 

```
sfbd@cally:~$ mysql -uzsdkjghsdg
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 255
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>
```

Is there a way I can log in as a user from within the mysql UI?  That might be interesting.

---

### Post by terazen on 2009-04-29
Mysql isn't in safe mode?  If it's ran with the --skip-grant-tables then that will happen.  Not sure what else could do it.

> mysqld_safe --skip-grant-tables

---

### Post by shadowfirebird on 2009-04-29
I've been asleep these long millenia, and know nothing of this safe mode of which you speak.  :)

I'm googling like crazy and I'm not finding much.  Does safe mode have any effect other than applying the options in the sql_safe group in the config file?  

Do I take it from the way you phrased your question that I *should* be in safe mode?

I think I am:

```
sfbd@cally:/etc/mysql$ ps -ef |grep mysql
root     13441     1  0 12:33 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql    13480 13441  0 12:33 ?        00:01:50 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root     13482 13441  0 12:33 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
sfbd     25650 17482  0 19:51 pts/0    00:00:00 grep mysql
sfbd@cally:/etc/mysql$
```

---

### Post by terazen on 2009-04-29
You shouldn't be using the skip grant tables I meant.  Safe mode is normal.

---

### Post by shadowfirebird on 2009-04-29
No, I'm definitely not using -skip-grant.  I can log in as anything, but I can't access the database.  And I can't log in using the correct username and password.

---

### Post by shadowfirebird on 2009-04-29
The plot thickens.

Everything works as expected if I use mysql remotely from my Ubuntu 8.04 box.   It only screws up if I try to use the mysql command locally on my 8.10 box.

(Just to be clear, "as expected" means that I should be able to log in using the username and password I set for the user, and, ideally, not otherwise.)

mysql version for 8.04 box: 14.12 distrib 5.0.51a
mysql version for 8.10 box: 14.12 distrib 5.0.67

Unfortunately what I'm trying to do here is set up a web application, so it's the local access that I need.

I guess it's time to try and find known bugs that match, unless you have any suggestions...

---

### Post by shadowfirebird on 2009-04-29
I think I have the answer.

When I log in locally I specify -h localhost or give no -h.

When I log in remotely I specify -h cally.

I've just tried -h cally on the local machine and for some reason it worked.  I don't understand why, and I'm not sure it will help me install my web app (Ampache) but that seems to be what's going on.

I suspect that the two entries on the user table with blank user names are what is fasciliating this odd feature that allows me to log in with any user name, but I suppose that's unimportant.

Thanks for all your help, Terazen.

---

### Post by dasbooter on 2009-04-30
I am clearly in over my head here but I thought I would drop this in here as it might be helpful.

I had the same problem with password when I used phpmyadmin to try and create a new user for ampache. I created the user with a password @ %. The "%" sign I suppose means any. I could not log in to phpmyadmin with this new user or password even with all the privildges granted etc. It wasnt until I set the user up using the command line that it worked using ```
mysql -u root
``` to login and then using a command to establish accounts at each of @ locahost, 127,0,0,1, and "my computers host name" and %. 
Being able to log in from other locations for you seems to smack of something similiar?... but maybe not.. anyways I am all new to this and was just trying to set up ampache :P

---

### Post by shadowfirebird on 2009-05-01
Yup, that's what happenned to me.  

I solved it by adding a new user by hand (with %) and then making sure I specified the host name rather than leaving it out or saying localhost.  

I don't know why I had to do that, but it worked.

I'm left with not being terribly impressed with MySQL, myphpadmin or even Ampache (since it seems to be quite weak at actually playing music, sort of important).

---


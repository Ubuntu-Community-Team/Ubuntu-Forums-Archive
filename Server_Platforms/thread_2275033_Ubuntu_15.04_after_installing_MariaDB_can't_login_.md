---
title: "Ubuntu 15.04 after installing MariaDB can't login with password.."
date: 2015-04-23
forum: Server Platforms
---

### Post by gijs007 on 2015-04-23
I've just installed Ubuntu server 15.04 64 bit.
After running: apt-get install mariadb-server mariadb-client

I run sudo /usr/bin/mysql_secure_installation
I configure a root password and use the recommended options (yes on all)

I then try to login with: mysql -u root -p
After typing the password I receive the following message: ERROR 1698 (28000): Access denied for user 'root'@'localhost'


I'm not sure what's causing this, I've made sure the password was typed correctly both at installation and at login (at first I used copy paste, trough SSH) but later I decided to do a reinstall and type the passwords  manually but this error still comes up.

---

### Post by gijs007 on 2015-04-23
I've found that when logging in with sudo mysql -u root -p
And then entering the password, that everything works fine.

I tried disabling this requirement by commenting:
#plugin-load-add         = auth_socket.so

But then I receive the following error: ERROR 1524 (HY000): Plugin 'unix_socket' is not loaded

---

### Post by georg-0 on 2015-04-24
Hello gijs007

I have exactly the same problem! Did you find a solution already? I can login when I call ```
sudo mysql -uroot -p
```, but not without the sudo command.

---

### Post by georg-0 on 2015-04-24
Solution didn't work....

---

### Post by gijs007 on 2015-04-24
No, I haven't found a solution yet.
Maybe creating a new mysql user will work? I'll try this in a bit.

---

### Post by gijs007 on 2015-04-24
No, I haven't found a solution yet.
Maybe creating a new mysql user will work? I'll try this in a bit.

Update: this works
> CREATE USER 'root2'@'localhost' IDENTIFIED BY 'some_pass';

GRANT ALL PRIVILEGES ON *.* TO 'root2'@'localhost'
WITH GRANT OPTION;
This new user is able to login without sudo and has the same permissions as root.
Source: [http://stackoverflow.com/questions/16747035/mysql-creating-a-user-with-root-privilages](http://stackoverflow.com/questions/16747035/mysql-creating-a-user-with-root-privilages)

---

### Post by sergerod on 2015-04-25
shell$ sudo mysql -u root

[mysql] use mysql;
[mysql] update user set plugin='' where User='root';
[mysql] flush privileges;
[mysql] \q

---

### Post by nerdtron on 2015-04-25
Mariadb is a drop-in replacement for mysql so i guess all commands will work right? Here are the steps to reset the "root" account password for mysql:

How to reset the root password for mysql:
Stop mysql:
1. service mysql stop

Run mysql with skip grants to be able to login without any password
2. mysqld_safe --skip-grant-tables &

Login as root
3. mysql -u root

4. mysql commands:
mysql> use mysql;
mysql> update user set password=PASSWORD("NEW-ROOT-PASSWORD-HERE") where User='root';
mysql> flush privileges;
mysql> quit

Stop mysql
5. service mysql stop

Start mysql normally:
6. service mysql start

Try to login using your new password:
7. mysql -u root -p

---

### Post by darkod on 2015-04-25
I am no expert with mysql or mariadb, but could the issue have happened because you ran the mysql_secure_installation with sudo? So after that it doesn't accept the mysql root except with sudo. This is just an assumption...

It might explain why newly created root2 works fine but the original root only with sudo.

---

### Post by sergerod on 2015-04-25
Mysql tries to authenticate root using plugin, not password. You need [just disable plugin usage for root]("http://ubuntuforums.org/showthread.php?t=2275033&p=13272227#post13272227")

---

### Post by gijs007 on 2015-04-26
Sergod is correct. Just wondering, is the ability to login as sudo into mysql a security risk?

---

### Post by zhxq on 2015-04-27
Thanks for [[COLOR=#000000]sergerod[/COLOR]]("http://ubuntuforums.org/member.php?u=1980440")[COLOR=#000000]  & [/COLOR][COLOR=#000000][B]nerdtron
[/B][/COLOR]I had fixed my problem.
What I did is to combine their commands.
Do nerdron's answer first.

Here's what I did and saved my MariaDB.
Stop mysql:
1. **/etc/init.d/mysql stop** and **killall -9 mysqld**
Make sure no mysqld is exist.
Run mysql with skip grants to be able to login without any password
2. **mysqld_safe --skip-grant-tables &**
Login as root
3. **mysql -u root**
then is sergerod's.
[mysql] **use mysql;**
[mysql] **update user set plugin='' where User='root';**
[mysql] **flush privileges;**
[mysql] **\q or exit**
and then:
**/etc/init.d/mysql stop **(or **service mysql stop**) and **killall -9 mysqld**
and start the mysql thru
**service mysql start** or **/etc/init.d/mysql restart**
and all is done!

Also I **made a script**, please go to [B][http://zhxq.io/?p=99](http://zhxq.io/?p=99)

[/B]and I tested my script, it is functional.

It's hard to stop mysqld by the script...... so the script sometimes doesn't work (rarely).

All in all, thanks dude!

---

### Post by alfkh2 on 2015-04-27
no, it didn't work.. i still get;
alvinh@lenovog470:~/Documents/G470Test/mysql$ mysql -u root -p
Enter password: 
ERROR 1698 (28000): Access denied for user 'root'@'localhost'

The thing is, in 14.10, mariadb 10.0 did ask me for a root password. What happened now?

---

### Post by zhxq on 2015-04-27
> **alfkh2 said:**
> no, it didn't work.. i still get;
alvinh@lenovog470:~/Documents/G470Test/mysql$ mysql -u root -p
Enter password: 
ERROR 1698 (28000): Access denied for user 'root'@'localhost'

The thing is, in 14.10, mariadb 10.0 did ask me for a root password. What happened now?

Seems that you changed your password somehow.

The problem is about plugin unix socket is not loaded, but you got a password problem.

---

### Post by alfkh2 on 2015-04-27
i did a reinstall, then something i read from a boo;
mysqladmin -u root password 'my-password';

still it didn't work, but i did whatever [**[COLOR=#000000]sergerod[/COLOR]**]("http://ubuntuforums.org/member.php?u=1980440") said to do, 
sudo mysql -u root -p

keyed in the password that i set earlier & hey-presto, i was in! 
I quickly did the follow up from his thread ie 
shell$ sudo mysql -u root

[mysql] use mysql;
[mysql] update user set plugin='' where User='root';
[mysql] flush privileges;
[mysql] \q

Now i can "mysql" without doing sudo. thanks chaps!

---

### Post by zhxq on 2015-04-27
> **alfkh2 said:**
> i did a reinstall, then something i read from a boo;
mysqladmin -u root password 'my-password';

still it didn't work, but i did whatever [**[COLOR=#000000]sergerod[/COLOR]**]("http://ubuntuforums.org/member.php?u=1980440") said to do, 
sudo mysql -u root -p

keyed in the password that i set earlier & hey-presto, i was in! 
I quickly did the follow up from his thread ie 
shell$ sudo mysql -u root

[mysql] use mysql;
[mysql] update user set plugin='' where User='root';
[mysql] flush privileges;
[mysql] \q

Now i can "mysql" without doing sudo. thanks chaps!

He really saved us!

---

### Post by alfkh2 on 2015-05-01
[**[COLOR=#000000]sergerod[/COLOR]**]("http://ubuntuforums.org/member.php?u=1980440") did most of the work.. the book i borrowed from the library with mysqladmin command is "MySQL the complete reference" by vikram vaswani published by Osborne-Mcgraw hill. Hope that helps. As you can c, i'm a real newbie.. still reading books on mysql!

---

### Post by talkingnews on 2015-05-30
> **zhxq said:**
> [mysql] **update user set plugin='' where User='root';**


DO NOT DO THIS! I had hours of problems after this. For example, I could not access my stored procedures, I could not use **service mysql restart **and so on

The correct solution is to make another user with the same permissions as root.

If you need to repair the damage, do the following (found [here]("https://www.mail-archive.com/search?l=maria-developers@lists.launchpad.net&q=subject:%22%5BMaria-developers%5D+auth_socket%2Funix_socket+auth+plugin+naming+incompatibility+with+Percona+Server%22&o=newest&f=1"))

[FONT=arial]pkill everything to do with mysql
[/FONT]
```
[FONT=arial]killall -9 mysqld[/FONT]
[FONT=arial]mysqld_safe --skip-grant-tables&[/FONT]
[FONT=arial]mysql -uroot -p[/FONT]
```

[FONT=arial](enter password)[/FONT]

```
[FONT=arial][mysql]   update mysql.user set plugin='unix_socket' where plugin='auth_socket';[/FONT]
[FONT=arial][mysql]  [/FONT][FONT=arial]\q[/FONT]
```

```
[FONT=arial]nano /etc/mysql/mariadb.conf.d/mysqld.cnf[/FONT]
```

[FONT=arial]at the end, change whatever is there to[/FONT]

> [FONT=arial]plugin-load=unix_socket=auth_socket.so[/FONT]

For some reason, I found the only way to permanently get this to "stick" was to do a

```
sudo shutdown -r now
```

and let the whole vps reboot. After that, everything is returned to normal, and I just use the new user with root privileges.

---

### Post by Klintrup on 2015-06-12
This error occurs because the unix_socket plugin module is not loaded by default in MariaDB.

The easy fix is to run the following SQL statement as a user with the SUPER privilege
```
INSTALL PLUGIN unix_socket SONAME 'auth_socket';
```

No other changes are needed to the installation and the plugin configuration persists over reloads/reboots

More information on the plugin [here]("https://mariadb.com/kb/en/mariadb/unix_socket-authentication-plugin/")

---

### Post by David_Leonardo on 2015-06-15
Check this file:

/etc/mysql/mariadb.conf.d $ nano mysqld.cnf

verify if exist this line:

plugin-load-add = auth_socket.so

then go to MariaDB

sudo mysql -u root

and make this:

MariaDB [(none)]>use mysql;
MariaDB [(none)]>update user set plugin=' ' where User='root';
MariaDB [(none)]>flush privileges;
MariaDB [(none)]>exit

try this solution... I hadn't acces to mysqlworkbench, but then this solution... everything run well...

[http://www.versatilewebsolutions.com/blog/2015/05/dealing-with-mariadb-plugin-unixsocket-is-not-loaded.html](http://www.versatilewebsolutions.com/blog/2015/05/dealing-with-mariadb-plugin-unixsocket-is-not-loaded.html)

---

### Post by David_Leonardo on 2015-06-15
error connection

check this file:

/etc/mysql/mariadb.conf.d $ nano mysqld.cnf

verify if exist this line:

plugin-load-add = auth_socket.so

then go to MariaDB

sudo mysql -u root

and make this:

MariaDB [(none)]>use mysql;
MariaDB [(none)]>update user set plugin=' ' where User='root';
MariaDB [(none)]>flush privileges;
MariaDB [(none)]>exit

try this solution... I hadn't acces to mysqlworkbench, but then this solution... everything run well...

---

### Post by andymnc on 2015-07-15
> **sergerod said:**
> shell$ sudo mysql -u root

[mysql] use mysql;
[mysql] update user set plugin='' where User='root';
[mysql] flush privileges;
[mysql] \q

this one will solve.
also, it will be useful after yesterday's mariadb update (about 14th july 2015)

---

### Post by Lideln on 2015-09-25
> **sergerod said:**
> shell$ sudo mysql -u root

[mysql] use mysql;
[mysql] update user set plugin='' where User='root';
[mysql] flush privileges;
[mysql] \q

Works like a charm! Finally!!!! Thank you!! (and far easier than other methods I could find)

---

### Post by Jorge_Reyes on 2016-01-08
Thanks zhxq for the instructions. They were enormously helpful.

---

### Post by KahSiak_W on 2016-05-02
Thank you georg-0! I did login using sudo mysql -uroot -p. So far, I still don't know what was the reason why '' sudo mysql -u root -p '' couldn't access.

---

### Post by Bucky Ball on 2016-05-02
Thanks for sharing. This thread is now getting old, the three posts before yours looks like they are bean-mining and add nothing relevant, 15.04 is no longer supported, so thanks for sharing but thread closed.

If you have issues please post a new thread with a descriptive title in the appropriate forum area. Thanks and good luck.

---


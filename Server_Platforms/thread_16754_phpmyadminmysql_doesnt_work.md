---
title: "phpmyadmin/mysql doesnt work"
date: 2005-02-23
forum: Server Platforms
---

### Post by Lift0 on 2005-02-23
I Have installled mysql-server och phpmyadmin...

But now, since i do not have root in this ubuntu rellease (sudo?)...
I set mysql user lift0 to a password and then put same login/pass in config.inc.php and then trying to login? but i wont....
and since i dont have root i can't adduser mysql in root or can i ? 
Don't know how to do this ?!

---

### Post by macewan on 2005-02-23
[QUOTE=Lift0]I Have installled mysql-server och phpmyadmin...

But now, since i do not have root in this ubuntu rellease (sudo?)...
I set mysql user lift0 to a password and then put same login/pass in config.inc.php and then trying to login? but i wont....
and since i dont have root i can't adduser mysql in root or can i ? 
Don't know how to do this ?![/QUOTE]

root on mysql is a different root than on the o.s. itself

---

### Post by Lift0 on 2005-02-23
[QUOTE=macewan]root on mysql is a different root than on the o.s. itself[/QUOTE]
 hm....yeah ofcourse, can u show me how I should do it? first adding a user in mysql then fixing it with phpmyadmin ?

---

### Post by machiner on 2005-02-23
Not having a "root" account on your Ubuntu has nothing to do with setting a "root" password for your mysql.

After installing mysql 
 you simply open a terminal and type the following: (NOT as sudo, regular user)

mysqladmin -u root password <password>  hit enter
(example: mysqladmin -u root password r5jkff8Ydb )

you'll see your prompt and you have just made a root password for your mysql install.

To change the uname from root to <whatever> do this:

type mysql -u root -p to enter MySQL as the root user.

At the MySQL prompt (mysql>) type the following:

update user set user="sqladmin" where user="root";  hit enter (include the semi-colon)
flush privileges;  hit enter

set user="sqladmin" is root's new username. Pick your own and remember it. You will have to modify all of your fancy-schmancy php scripts (and programs like Drupal (can I have an AZZ one time) or videoDB and the like)

If you would like to compile your own LAMP see this page, it works, I've used these instructions umpteen times with success:

[http://www.lamphowto.com/lamp.htm](http://www.lamphowto.com/lamp.htm)

also - you might find this useful:
download, and install Webmin - 

[http://prdownloads.sourceforge.net/webadmin/webmin-1.180.tar.gz](http://prdownloads.sourceforge.net/webadmin/webmin-1.180.tar.gz)
to install:  extract it, go into its directory, open a terminal, 
type: sudo sh setup.sh /usr/local/webmin     hit enter...
I use defaults except for the uname/password and port. Also, it's probably not that great an idea to have Webmin run from boot. 
To start Webmin: $ sudo /etc/webmin/start

---

### Post by Lift0 on 2005-02-23
> **machiner]Not having a "root" account on your Ubuntu has nothing to do with setting a "root" password for your mysql.

After installing mysql 
 you simply open a terminal and type the following: (NOT as sudo, regular user)

mysqladmin -u root password <password>  hit enter
(example: mysqladmin -u root password r5jkff8Ydb )

you'll see your prompt and you have just made a root password for your mysql install.

To change the uname from root to <whatever> do this:

type mysql -u root -p to enter MySQL as the root user.

At the MySQL prompt (mysql>) type the following:

update user set user="sqladmin" where user="root" said:**
> http://www.lamphowto.com/lamp.htm[/url]

also - you might find this useful:
download, and install Webmin - 

[http://prdownloads.sourceforge.net/webadmin/webmin-1.180.tar.gz](http://prdownloads.sourceforge.net/webadmin/webmin-1.180.tar.gz)
to install:  extract it, go into its directory, open a terminal, 
type: sudo sh setup.sh /usr/local/webmin     hit enter...
I use defaults except for the uname/password and port. Also, it's probably not that great an idea to have Webmin run from boot. 
To start Webmin: $ sudo /etc/webmin/start
 mysql -u root password doh1234
mysql -u root -p
password: doh1234
ACCESS DENIED 1045 for user root@localhost (Using password: YES)
?

---

### Post by machiner on 2005-02-23
[QUOTE=Lift0]mysql -u root password doh1234
mysql -u root -p
password: doh1234
ACCESS DENIED 1045 for user root@localhost (Using password: YES)
?[/QUOTE]


the syntax is:

mysqladmin  not mysql

do this from a terminal:

mysqladmin -u root password doh1234


then the rest.

---

### Post by Lift0 on 2005-02-24
[QUOTE=machiner]the syntax is:

mysqladmin  not mysql

do this from a terminal:

mysqladmin -u root password doh1234


then the rest.[/QUOTE]
 
mysqladmin -u root password doh1234
mysqladmin:unable to change password; error; 'Acces denied for user '@localhost' to database mysql

---

### Post by Lift0 on 2005-02-24
someone?

---

### Post by macewan on 2005-02-24
**caution: gui ahead** :-)

sudo apt-get install mysql-admin [enter]

mysql-admin [enter]

[IMG]http://www.macewan.org/images/mysql1.jpg[/IMG]

Server Hostname: **localhost**
Username: **root**

now hit the [connect] button

[IMG]http://www.macewan.org/images/mysql2.jpg[/IMG]

See **User Administration**? It's three down from the currently highlighted choice. Click it and you'll see:

[IMG]http://www.macewan.org/images/mysql3.jpg[/IMG]

See the new window below (**User Accounts**)? Select **root** and now you'll see the window to the left will give you a chance to enter a root password.

---

### Post by Lift0 on 2005-02-25
ysqladmin -u root password 'doh1234'
mysqladmin: unable to change password; error: 'Access denied for user: '@localhost' to database 'mysql'' 


mysql -u root
Welcome to the MySQL monitor. Commands end with ; or \g.
Your MySQL connection id is 11 to server version: 4.0.20-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> UPDATE mysql.user SET Password=PASSWORD('doh1234') WHERE User='root';
ERROR 1044: Access denied for user: '@localhost' to database 'mysql'


mysql -u root
Welcome to the MySQL monitor. Commands end with ; or \g.
Your MySQL connection id is 25 to server version: 4.0.20-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> password ********
-> use mysql
-> UPDATE user SET password="********" WHERE User="root" AND host="localhost";
ERROR 1064: You have an error in your SQL syntax. Check the manual that corresponds to your MySQL server version for the right syntax to use near 'password ********
use mysql
UPDATE user SET password="********"

mysql> use mysql
ERROR 1044: Access denied for user: '@localhost' to database 'mysql'

mysql> use test
Database changed


????

---

### Post by hantsy on 2005-03-02
Many linux distrobute disabled mysql network access by default...
Enter mysql cmd console as root in your termina:
#msyql -u root -h <host>
Run the following command l:
mysql>grant all on <yourdbname>.* to root@'%' identified by '<yourpassword>';
msyql>flush privileges;

*NOTE*: Do not forget replace the  "<XXX>" to your own parameter ...

Others ,check your mysql configure file ,if exist a line like this:

skip-network

Comment this pls

Phpmyadmin requires the latest php4 ,DO NOT use php5 which is not compatible with php4 completely...
You must modify the config file to alter the "host" "username" "password" etc...

---


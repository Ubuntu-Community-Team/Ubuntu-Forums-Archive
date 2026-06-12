---
title: "bash: mysql: command not found (after install)"
date: 2006-03-20
forum: Server Platforms
---

### Post by echo $USER on 2006-03-20
Hi, I installed apache2 and php4 works perfectly when i test with <?phpinfo;()?>, but I then installed mysql while following [this guide]("http://ubuntuguide.org/#installmysqlapache").  Now when I try to set the root passwd for my default account by "mysql -u root", I get the message that mysql command not found (I also get it when i just run "mysql" and I have tried it to with sudo mysql -u root).  When i run "whereis mysql" I get only /etc/mysql.  Can anyne help me?  Am I missing anything?  Thanks for the help!

---

### Post by Zelut on 2006-03-20
did you install 'mysql-server' package?

---

### Post by dermotti on 2006-03-20
evenetually you will need to install **php4-mysql **too

---

### Post by echo $USER on 2006-03-21
Here is a list of everything I installed in the order I installed them:

apache2
php4
libapache2-mod-auth-mysql
php4-mysql

Apache restarts fine.  PHP is working when i test 127.0.0.1/testphp.php w/ 
<?phpinfo();?>.  But when i try to connect to mysql account through the terminal, it says that mysql is not found.  "whereis mysql" only returns /etc/mysql.  Thanks again!

---

### Post by gmclachl on 2006-03-21
Did you install the mysql-client?

George

---

### Post by echo $USER on 2006-03-21
I did not.  Can you give me the name of the apt package for the mysql client?  Thanks a lot George!

---

### Post by gmclachl on 2006-03-21
Hmmm, I can't remember off the top of my head. Pretty sure it's just mysql-client

 so 
sudo apt-get install mysql-client 

George

---

### Post by Zelut on 2006-03-21
I've always just installed the mysql-server package & that has always been all that I've needed..

---

### Post by echo $USER on 2006-03-21
Thanks to everyone for the help.  I'll install mysql-client when i get home on my lunch break and see if all goes well. Thanks again!

---

### Post by echo $USER on 2006-03-21
I installed mysql-client.  Here is the error message I recieve when I try to connect:

admin@ubuntu:~$ mysql -u root
ERROR 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
admin@ubuntu:~$ mysql
ERROR 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
admin@ubuntu:~$ sudo mysql -u root
ERROR 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
admin@ubuntu:~$ whereis mysql
mysql: /usr/bin/mysql /etc/mysql /usr/bin/X11/mysql /usr/share/man/man1/mysql.1.gz


Thanks to anyone that can help me out!

---

### Post by gmclachl on 2006-03-21
What packages have you installed so far?
 
 George

---

### Post by echo $USER on 2006-03-21
apache2
php4
libapache2-mod-auth-mysql
php4-mysql
mysql-client

Im thinking this might have to do with an ownership permissions?  Thanks for the help.

---

### Post by gmclachl on 2006-03-21
By default MySQL is set to run under the mysql user. Try 

 ls -la /var/run/mysqld

 you should see 
srwxrwxrwx  1 mysql mysql   0 2006-03-22 01:21 mysqld.sock
 
if mysqld.sock is owned by another user or different group then thats probably the issue

 if so 
  sudo chown mysql /var/run/mysqld/mysql.sock
  sudo chgrp mysql /var/run/mysqld/mysql.sock

George

---

### Post by echo $USER on 2006-03-22
I dont have a mysql entry in the /var/run directory.  Mysql is only found in mysql: /usr/bin/mysql /etc/mysql /usr/bin/X11/mysql /usr/share/man/man1/mysql.1.gz
I tried to chown mysql:mysql /usr/bin/mysql and it said I didn't have a mysql user.

---

### Post by gmclachl on 2006-03-22
You know, I have installed MySQL so many times now I do it on auto-pilot and never give it any thought, so I can't remember all the packages you need. It is strange how there is no mysql user. 

I would try removing the mysql packages and installing them all again. Off the top of my head
mysql-common, mysql-server, mysql-client, libmysqlclient14 [sic]

George

---

### Post by echo $USER on 2006-03-22
Thanks for the help George.  I'll uninstall all the mysql packages when i get home and start over.  It's really not that important.  I just need it for development purposes anyway, so I can learn php and mysql.  Thanks again for all the help.

---

### Post by echo $USER on 2006-03-22
Installing mysql-server solved my problem; its always the most obvious things. Thanks for the help.

---


---
title: "MySQL Help ... No Access ..."
date: 2006-09-13
forum: Server Platforms
---

### Post by atraeyu on 2006-09-13
I'm new to MySQL administration. I just installed MySQL.
I need to know how to create a MySQL user, create a new Database, and give that user access to the database.

Before I even get to that though, I think I'm missing something basic.
sudo mysqladmin <command> yeilds :
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

Not quite sure how to proceed. Any help would be much appreciated. Thanks.

---

### Post by mwob on 2006-09-14
Hi,

I'm having similar problems... I installed by following the instructions here: [http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

It installed OK, and the information in that guide points you to a page on the mysql site that tells you what you need to do "post installation" for unix. Basically, you need to run the mysql_install_db command, as explained here: [http://dev.mysql.com/doc/refman/5.0/en/unix-post-installation.html](http://dev.mysql.com/doc/refman/5.0/en/unix-post-installation.html)

I managed to run the command, but I had to run it as the root user:

"sudo mysql_install_db --user=mysql"

That seems to run the script OK, but then I can't get much further than that... the rest of the information gives you other commands to try and check that the database is running, and I get lots of access denied erorrs. I'm going to try a few more things, and I'll let you know what happens if you're interested....

---

### Post by atraeyu on 2006-09-14
Alright, here is exactly what is going on:

mysql
> 
atraeyu@akira:~$ mysql
ERROR 1045 (28000): Access denied for user 'atraeyu'@'localhost' (using password: NO)

my user account denied access on localhost ...

mysql -p
> 
atraeyu@akira:~$ mysql -p
Enter password:
ERROR 1045 (28000): Access denied for user 'atraeyu'@'localhost' (using password: YES)

The password prompt is the mysql password prompt instead of the typical shell password prompt ...

sudo mysql -p
> 
atraeyu@akira:~$ sudo mysql -p
Enter password:
Welcome to the MySQL monitor ...

Actually lets me in ...But I assume I've got something configured wrong here and that my scripts are going to get the hell denied out of them.

**Similarly, when trying to use mysqladmin:**

mysqladmin flush-privileges
> 
atraeyu@akira:~$ mysqladmin flush-privileges
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'atraeyu'@'localhost' (using password: NO)'

my user account denied access on localhost ...

sudo mysqladmin flush-privileges
> 
atraeyu@akira:~$ sudo mysqladmin flush-privileges
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

root denied access on localhost ...

sudo mysqladmin -p flush privileges
> 
atraeyu@akira:~$ sudo mysqladmin -p flush-privileges
Enter password:
atraeyu@akira:~$

It actually worked ...

So, I guess what I'm looking for is someone to help me understand exactly what is going on here, and whether it is working correctly.

It seems to me like if I type sudo mysql it should let me in.  It doesn't though.  I can't do ANYTHING with mysql or mysqladmin without using the -p argument.  How come?

There should be a way to make it so I can simply connect to the mysql user without using "sudo" - perhaps by creating a mysql user with my system username and the same password?

The end goal is to learn to create a mysql user, a mysql database, grant that user access to modify the database, and set where that user can access the server from (localhost vs remote ip addresses).

... I know that's a lot, but thanks!

---

### Post by atraeyu on 2006-09-14
I just learned:
mysqladmin is NOT THE SAME as mysql-admin

sudo apt-get install mysql-admin
mysql-admin

---

### Post by az on 2006-09-14
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by mwob on 2006-09-14
Thats exactly the same issues I have. I assume you did the "mysql_install_db" stuff? 

It should be possible to run mysql without the SUDO... perhaps its related to the root user owning all the files and permissions, and they need to be assigned to the mysql user? Just guessing there though.

---

### Post by mwob on 2006-09-14
azz - thanks for the info, I will try again :)

---

### Post by atraeyu on 2006-09-14
My mysql-admin actually locks up on me too.
If I try to kill the server, I get permission denied, if I try to access the user administration tab, it just hangs on me and I have to force quit the application.

...

---

### Post by atraeyu on 2006-09-14
I've been referencing the guide you mentioned azz:
I've done a few things from that I had not done previously:

> 
nano /etc/mysql/my.cnf
and change the line:
bind-address           = localhost
to your own internal ip address e.g. 192.168.1.20
bind-address           = 192.168.1.20

However - my configuration file actually read:
> bind-address           = 127.0.0.1

According to that guide:
> 
Since the mysql root password is now set, if you need to use mysql again (as the mysql root), you will need to use:
**mysql -u root -p**
and then enter the password at the prompt. 

Which does work for me.  So I guess it's working then ... thanks!

---


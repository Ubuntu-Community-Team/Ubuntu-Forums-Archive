---
title: "[MySQL] simply won't work"
date: 2005-03-09
forum: Server Platforms
---

### Post by deBaas on 2005-03-09
> 
$ sudo apt-get install mysql-server
$ sudo /usr/bin/mysqladmin -u root password your_db_user_password

MySQL install fine.
But accessing it?
2nd line gives me:
> 
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'

Fresh ubuntu install, fresh MySQL install.


If you have to recompile your kernel to get SATA working and even the commands @ ubuntuguide.org don't work; I can hardly imagine ubuntu becomming a main distro.

---

### Post by alastair on 2005-03-09
This is a Debian thing perhaps.

Did you have a look at the docs? Make a habit of looking at docs installed under :

/usr/share/doc/<program>

e.g.

/usr/share/doc/mysql-server/README.Debian

---

### Post by deBaas on 2005-03-09
[QUOTE=alastair]/usr/share/doc/mysql-server/README.Debian[/QUOTE]
says:
/usr/bin/mysqladmin -u root password 'yourpassword'

wich doesn't help much....

---

### Post by alastair on 2005-03-09
OK, maybe things have changed.

Mine mentions :

* MYSQL WON'T START OR STOP?:
=============================
You may never ever delete the special mysql user "debian-sys-maint". This user
together with the credentials in /etc/mysql/debian.cnf are used by the
init scripts to stop the server as they would require knowledge of the
mysql root users password else.
So in most of the times you can fix the situation by making sure that
the debian.cnf file contains the right password, e.g. by setting a new
one (remember to do a "flush privileges" then).


This one got me at first - never seen this. There's a special user called "debian-sys-maint" - and see "/etc/mysql/debian.cnf" for a password. I hope this is the same for you. I changed this passowrd and restarted mysql-server - then added the "root" user, then myself.

Hope that helps.

---

### Post by nate on 2005-03-11
deBaas,

By default the root user shouldn't have a password in MySQL as far as I know. If you're using a password to try and login for the first time, try with no password.

If you've used MySQL on other distributions then the procedures to set it up should be similar or identical on Ubuntu once you've gotten past the installation phase.

---

### Post by az on 2005-03-11
"error: 'Access denied for user: 'root@localhost' (Using password: NO)"

You have to use the -p argument in your sql commands.  The above error says that there is a password for you to use and you are not using it.  It is the password you set yourself.



"By default the root user shouldn't have a password in MySQL as far as I know"

That is correct, but you have to set one to use mysql.

---

### Post by machiner on 2005-03-12
$ sudo /usr/bin/mysqladmin -u root password your_db_user_password

That was a mistake. You add a root password as a normal user from the terminal.

$ mysqladmin -u root password <password>

---

### Post by Permafrost91 on 2005-11-21
I deleted /etc/mysql ](*,) .... how can I get all those files in it back?

.... never mind, I just copied the folder over from another installation and then
# apt-get remove --purge mysql-server
# apt-get install mysql-server

did the trick

---

### Post by engine on 2005-11-25
[QUOTE=azz]"error: 'Access denied for user: 'root@localhost' (Using password: NO)"

You have to use the -p argument in your sql commands.  The above error says that there is a password for you to use and you are not using it... That is correct, but you have to set one to use mysql.[/QUOTE]

OK, but how should I set the password? I don't mind if the answer is RTFM,as long as you can point me in the direction of a clear answer <g> It seems a pity that installation doesn't set up an automatic MySQL user with the same name and password as the Ubuntu user who ran the install.

---

### Post by Permafrost91 on 2005-11-27
right after you first instally mysql-server you should run
```
$ mysqladmin -u root password 'your new root password here'
```

to set up a root account for your MySQL db ... there's a debian-sys-maint user already set up but I don't know if that's the same as the default user's password after the installation (I never used this account so I don't know ... I create the root user account for MySQL and then set up other users from that).

---

### Post by cvmostert on 2005-12-13
[QUOTE=alastair]OK, maybe things have changed.

Mine mentions :

* MYSQL WON'T START OR STOP?:
=============================
You may never ever delete the special mysql user "debian-sys-maint". This user
together with the credentials in /etc/mysql/debian.cnf are used by the
init scripts to stop the server as they would require knowledge of the
mysql root users password else.
So in most of the times you can fix the situation by making sure that
the debian.cnf file contains the right password, e.g. by setting a new
one (remember to do a "flush privileges" then).


This one got me at first - never seen this. There's a special user called "debian-sys-maint" - and see "/etc/mysql/debian.cnf" for a password. I hope this is the same for you. I changed this passowrd and restarted mysql-server - then added the "root" user, then myself.

Hope that helps.[/QUOTE]


the debian-sys-maint worked for me.. now i just want to edit the user info... will figure it out.. thanx

---

### Post by ruakuu on 2008-04-16
This worked for me:

First get debian-sys-maint user pass from /etc/mysql/debian.cnf
Example:
debian-sys-maint
YTERYgkjhbsfk87ce

Then:

$mysql -u debian-sys-maint -p
password: (put YTERYgkjhbsfk87ce here)
mysql> UPDATE mysql.user SET Password=PASSWORD('my_new_password') WHERE User='root';
mysql> flush privileges;
mysql> quit

$mysqladmin -u root password my_new_password (I didn't use this one since I don't like remote root access)
$mysqladmin -p -u root -h localhost password my_new_password

Hope it helps ^^

---

### Post by lsutiger on 2008-07-05
> ruakuu  	
Re: [MySQL] simply won't work
This worked for me:

First get debian-sys-maint user pass from /etc/mysql/debian.cnf
Example:
debian-sys-maint
YTERYgkjhbsfk87ce

Then:

$mysql -u debian-sys-maint -p
password: (put YTERYgkjhbsfk87ce here)
mysql> UPDATE mysql.user SET Password=PASSWORD('my_new_password') WHERE User='root';
mysql> flush privileges;
mysql> quit

$mysqladmin -u root password my_new_password (I didn't use this one since I don't like remote root access)
$mysqladmin -p -u root -h localhost password my_new_password

I used this and still am having problems.

I even ran a select * from mysql.user and saw the correct password sitting there. This is really frustrating, as there are a LOT of post all over the net about this but no clear answers.

THESE PRETZELS ARE MAKING ME THIRSTY!!!

---


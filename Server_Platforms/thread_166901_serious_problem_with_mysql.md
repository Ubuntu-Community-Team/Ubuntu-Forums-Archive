---
title: "serious problem with mysql"
date: 2006-04-27
forum: Server Platforms
---

### Post by ukasz20 on 2006-04-27
root@skynet:/home/ukasz# mysqladmin -u root password newrootsqlpassword
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'


this is the error wchich makes me :evil: 

i want to configure my mysql as it is in [http://doc.ubuntu.com/ubuntu/serverguide/C/databases.html](http://doc.ubuntu.com/ubuntu/serverguide/C/databases.html)


](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) 

please help

---

### Post by mjm115 on 2006-04-27
It looks like you forgot to put 'sudo' before you entered your command.  Try it logged on as you with the sudo command.  By default, sudo should give you the priveleges you need.  You shouldn't try it as root.

---

### Post by ukasz20 on 2006-04-27
same error

it drives me crazy

when i first installed it it was working but i had to uninstall it and now it doesn,t work

---

### Post by mjm115 on 2006-04-27
When you uninstalled it, did you:

> 
sudo apt-get remove --purge mysql


The reason I ask is that some of your settings may still be on your system and your old password may have been retained.  Try using your old password.  Does that help?

---

### Post by ukasz20 on 2006-04-29
yes i did it with purge and installed again and same thing

---

### Post by wsanders on 2006-04-29
You need to include the -p option in the mysqladmin command for it to ask for your password; without it, it does not pass any password through to the server.

---

### Post by TreetopClimber on 2006-04-30
Try this in Terminal

The first for accessing the database by console you need to type:

```
sudo mysql -u root
```

At the mysql console type:

```
mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');
```

For creating a new user at mysql prompt type:

```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'yourusername'@'localhost' IDENTIFIED BY 'yourpassword' WITH GRANT OPTION;
``` 

This will set you up in the database with all privileges
Also the first time you login to your database you should use screen name: (root) and password: (yourpassword)
then once in you can create a new user with all privileges

---

### Post by aylwyn on 2006-04-30
[QUOTE=ukasz20]root@skynet:/home/ukasz# mysqladmin -u root password newrootsqlpassword
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'
[/QUOTE]

like wsanders says, once you have given a root password using the command

mysqladmin -u root password newrootsqlpassword

you need to use the -p flag to then log in:
mysql -u root -p

sudo should not be necessary.

Yes this is an error/misleading bit in the server guide. We should send feedback!

---

### Post by ukasz20 on 2006-05-01
GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' INDENTIFIED BY 'obiwan' WITH GRANT OPTION;
ERROR 1064: You have an error in your SQL syntax.  Check the manual that corresponds to your MySQL server version for the right syntax to use near 'INDENTIFIED BY 'obiwan' WITH GRANT OPTION' at line 1


now i have this error

---

### Post by ukasz20 on 2006-05-01
and still can not create any database with:
mysqladmin create torrentflux < torrentflux.sql

it gives me error that i cannot login

---

### Post by ixus_123 on 2006-05-03
I'm having the same problem & can't seem to resolve it - can anyone help me?

I have tried all the steps listed & still can't gain access.

I have also installed phpmyadmin & that reports the same error

```
#1045 - Access denied for user 'root'@'localhost'  (using password: NO)
```

removed mysql & purged it to start again this time using the gui in phpmyadmin but as soon as I use that to set a root password it locks me out with the same error message.

The most annoying this is I have managed to get this up & running before but didn't remember this frustrating problem when I decided to do a fresh install / upgrade :(

---

### Post by ixus_123 on 2006-05-03
Seemed to have got things working by downgrading phpmyadmin 2.8.0.3 to 2.7.0 from the ubuntu repos

from there there was a log in screen - log in with "root" password - leave balnk

once in, there is an option to change password half way down the screen - simple as that!

Not sure why I couldn't get it done with the command line or phpmyadmin latest version though

---


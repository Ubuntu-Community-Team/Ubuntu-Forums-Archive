---
title: "phpmyadmin installation"
date: 2005-09-16
forum: Server Platforms
---

### Post by Rollo Tamasi on 2005-09-16
Hi lads, i'm hitting a brick wall with my installation of phpmyadmin and it hurts!

When i type in my my.ip.address/phpmyadmin/index.php i get asked for my username & password however it comes back with "#1045 - Access denied for user: 'cormac@localhost' (Using password: YES)" error message.

I have chmod777 the /var/www/phpmyadmin/ folder and altered the config.inc.php in order to setup a username and password. I have also attempted to log in as root with a blank password but i got the same type of error message on both occasions.

I have restard apache and sql but no luck....any forthcoming advise on how to solve this problem would be most appricated.

---

### Post by wallaceb on 2005-09-17
Obvious question: cormac@localhost IS a MySQL user, no?

---

### Post by Rollo Tamasi on 2005-09-17
[QUOTE=wallaceb]Obvious question: cormac@localhost IS a MySQL user, no?[/QUOTE]

cormac is the user account that i setup with sql, yes.

---

### Post by crmanski on 2005-09-17
Does it make a difference (I know logically it shouldn't) it you change the config file in phpmyadmin to user cormac@127.0.0.1?

---

### Post by venzen on 2005-09-17
On the MySQL client can you log in using:

mysql -u cormac -p

Obviously you are accessing phpmyadmin from the same host right?

---

### Post by venzen on 2005-09-17
OK, Rollo, assuming you can login to MySQL as root, do this:

```
SELECT from user, host, password FROM mysql.user;
```

this should output a table listing your sql users and where they may login from. Should you want to add or delete users with different login permissions do this:

```
GRANT ALL ON *.* TO cormac@localhost IDENTIFIED BY 'yourpassword';
```

```
DELETE FROM mysql.user WHERE user = 'cormac' AND password = 'oldpassword';
```

I have installed phpmyadmin many times and it has always worked out the box - my current installation is owned by root with mode 777 and it works fine.

I'll check this thread later tonight.

---

### Post by Rollo Tamasi on 2005-09-17
thanks for your help venzen, i'll look into your suggestions later on this evening.

When you say mysql client, do you mean within the actual mysqlCC interface or just the box that has mysql & phpmyadmin installed? This is my first attempt to get mysql and phpmyadmin up and running....

to your earlier question venze...yeah, i'm trying to access the phpmyadmin from the local machine.

---

### Post by Rollo Tamasi on 2005-09-18
mmm, i've just installed phpmyadmin on another machine and i'm getting the same problems again...(this could, probably is a stupid question but ......Is there a way thru the terminal screen using sudo that i can create a username and password for phpmyadmin? Or is it only thru altering that config file?

---

### Post by deuce868 on 2005-09-19
[QUOTE=Rollo Tamasi]mmm, i've just installed phpmyadmin on another machine and i'm getting the same problems again...(this could, probably is a stupid question but ......Is there a way thru the terminal screen using sudo that i can create a username and password for phpmyadmin? Or is it only thru altering that config file?[/QUOTE]

phpmyadmin authenticates to your mysql installation. Your problem is going to be in your mysql tables not in phpmyadmin. You have to create the user in mysql before you can use it in phpmyadmin. 

Have you created any accout in mysql? Have you setup privelages for any additional users? Have you reset the default mysql root user password from blank?

---

### Post by Rollo Tamasi on 2005-09-19
[QUOTE=deuce868]phpmyadmin authenticates to your mysql installation. Your problem is going to be in your mysql tables not in phpmyadmin. You have to create the user in mysql before you can use it in phpmyadmin. 

Have you created any accout in mysql? Have you setup privelages for any additional users? Have you reset the default mysql root user password from blank?[/QUOTE]

hi deuce, all i've done is install mysql. How would i go about creating an sql account, and assinging privelages?

I presume its all done from the terminal?

---

### Post by deuce868 on 2005-09-19
By default there should be a root user with no password. Try that in phpmyadmin. Once you're in there is a link in the middle of the page called "Privelages". Once in there you see a list of your users. Edit the two root users in there and make sure you create passwords for them.

---

### Post by venzen on 2005-09-20
Ok Rollo, you're getting good advice from deuce868... you say that you only installed MySQL so far, so you have a bit more configuration to do before it becomes useful:

at the commandline type:

```
mysql -u root
```

this should give you a command prompt like this:

```
venzen@thabanchu:~$ mysql -u root
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 6 to server version: 4.0.23_Debian-3ubuntu2.1-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>
```

Now go to my previous post and try the SQL commands I suggested. This is all commandline stuff that you should become familiar with. Of course, you can log straight into PHPMyAdmin as user 'root' and with an empty password - as deuce868 suggested. But my suggestion is that you research a bit more, see Section 3 of the [MySQL Refernce Manual](http://dev.mysql.com/doc/mysql/en/index.html) .

Please post your progress!

---

### Post by LordHunter317 on 2005-09-20
[QUOTE=venzen]OK, Rollo, assuming you can login to MySQL as root, do this:

```
SELECT from user, host, password FROM mysql.user;
```

this should output a table listing your sql users and where they may login from. Should you want to add or delete users with different login permissions do this:

```
GRANT ALL ON *.* TO cormac@localhost IDENTIFIED BY 'yourpassword';
```

```
DELETE FROM mysql.user WHERE user = 'cormac' AND password = 'oldpassword';
```

I have installed phpmyadmin many times and it has always worked out the box - my current installation is owned by root with mode 777 and it works fine.

I'll check this thread later tonight.[/QUOTE]All of these suggestions are very, very dangerous if you don't know what you're doing.

Having 777 permissions on just about anything is begging to be hacked, and phpmyadmin is a definite case of that.  Just don't do it.  If you're ever even thinking about chmod'ing anything 777, just stop and ask for help first, as it means you went wrong several steps ago.

---


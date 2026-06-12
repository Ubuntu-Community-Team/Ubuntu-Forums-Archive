---
title: "File shering"
date: 2009-02-15
forum: Server Platforms
---

### Post by gretarsson on 2009-02-15
Hi all.
I have ubuntu 8.10 and I install mysql, php5,apache2,phpmyadmin and samba and I I follow this video [http://www.lullabot.com/files/ubuntuLocalhost.mp4](http://www.lullabot.com/files/ubuntuLocalhost.mp4) 
but I am not get it right because if I try to put up Dropal6.9 I can not get it to work, another thing what is the best way to get Samba to share file global ?
I have never put up server before but I like to share files to my sons how live in another part of me country.
Thanks

---

### Post by utnubuuser on 2009-02-15
What are you not getting right?

Are you changing the ownership of /www? 

I've installed the lamp stack through repositories plenty of times with no issues.

Usually >>  Apache2, then mysql,(server and client), then php5, then phpmyadmin.

All at the same time.

Are you getting php5-gd? What about libapache-mod-php, etc.

The only "issue" I've ever had was forgetting to chown /www.

Be more specific about what is not working properly.

---

### Post by gretarsson on 2009-02-16
> **utnubuuser said:**
> What are you not getting right?

Are you changing the ownership of /www? 

I've installed the lamp stack through repositories plenty of times with no issues.

Usually >>  Apache2, then mysql,(server and client), then php5, then phpmyadmin.

All at the same time.

Are you getting php5-gd? What about libapache-mod-php, etc.

The only "issue" I've ever had was forgetting to chown /www.

Be more specific about what is not working properly.

Hi and thanks for reply
I look on my marks and see that php5 was missing, but first of all if I use phpmyadmin and create user name and password but I dont know what more I can fill out in phpmyadmin but if I try to go in Dropal 6.9 and create user area there and they ask for user and password from my MySQL database server, (I use same as I create in phpmyadmin) but Dropal say it is rong user and password. I dont know how I use phpmyadmin to make it right, any idea

---

### Post by cariboo on 2009-02-16
Can you access the mysql console from a terminal?

```
sudo mysql  -u root -p
```

use the password you created when you installed mysql. IF that works exit and try the user you created with phpmyadmin.

Jim

---

### Post by linux_tech on 2009-02-16
if you are looking for a linux content management system, joomla is another one to check out

---

### Post by gretarsson on 2009-02-17
> **cariboo907 said:**
> Can you access the mysql console from a terminal?

```
sudo mysql  -u root -p
```

use the password you created when you installed mysql. IF that works exit and try the user you created with phpmyadmin.

Jim
Thanks for reply, here is what I got out of my terminal

jon@jon:~$ sudo mysql  -u root -p
[sudo] password for jon: 
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 151
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 
----------------------------------------------------------------
I have never put up server before so I need some help to understand this 
what softwear do you thimk is best to use in my case?

---

### Post by cariboo on 2009-02-17
From the output mysql is working properly, so I would suggest creating a database called drupal and when setting up drupal use that database and use the username and password you used to create the database. eg:

```
mysqladmin create <databasename> -u root -p
```

Jim

---

### Post by gretarsson on 2009-02-18
> **cariboo907 said:**
> From the output mysql is working properly, so I would suggest creating a database called drupal and when setting up drupal use that database and use the username and password you used to create the database. eg:

```
mysqladmin create <databasename> -u root -p
```

Jim
Hi again I have been trying to use Dropal but I can not login, I think my user name is wrong or something take a look at this.

jon@jon:~$ mysqladmin create <jon> -u root -p
bash: jon: No such file or directory
jon@jon:~$ mysqladmin create <> -u root -p
Enter password: 
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'jon'@'localhost' (using password: YES)'
jon@jon:~$ sudo mysql  -u root -p
[sudo] password for jon: 
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 161
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 

Do you know how to change user name in myqsl?

---

### Post by cariboo on 2009-02-19
You don't need to change your user name, when creating a database don't use the <> around the database name. I installed Drupal the other day just to check how easy it is. I followed the documentation from the [Drupal]("http:///drupal.org/getting-started") documentation page.

I installed Drupal remotely as it isn't convenient for me to physically go to my server. The installation instructions are well written, in most cases all you have to do is copy and paste the instructions in a terminal.

Jim

Edit:  I tried to pm you but you aren't excepting messages

---


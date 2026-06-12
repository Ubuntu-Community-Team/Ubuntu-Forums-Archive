---
title: "Trouble following instructions for installing LAMP."
date: 2008-12-07
forum: Server Platforms
---

### Post by flukeairwalker on 2008-12-07
Hi, I'm a new user of Linux and I'm looking to turn an old desktop PC into a home server. Just this week I installed the latest Ubuntu and have been impressed by it so far. I'm not looking for anything fancy, just something I can put stuff on to share with my family and access from anywhere. I've been following the instructions posted [here]("http://www.howtoforge.com/ubuntu_lamp_for_newbies") and got as far as "Install MySQL" step 3 until I got the following error:

ERROR 1045: Access denied for user: 'root@localhost' (Using 
password: YES)

I then followed the instructions on [this page]("https://help.ubuntu.com/community/MysqlPasswordReset") but I only got as far as step 2 when I got the following error:

bash: /usr/bin/mysqld: No such file or directory

Following the optional instructions bolded below that, I got this error (Duessa is PC's name):

081207 18:28:46 [Warning] Can't create test file /var/lib/mysql/Duessa.lower-test
081207 18:28:46 [Warning] Can't create test file /var/lib/mysql/Duessa.lower-test
081207 18:28:46 [Warning] One can only use the --user switch if running as root

081207 18:28:46  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.

So then I tried the other option titled "Another way, purge" at the bottom of the page, and everything went fine, except that I couldn't log back in, getting this error:

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

Typing mysql -u root gets me:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

So, what can I do? I'm new to Linux so I don't know anything about the command line yet other than what instructions tell me, though I'm willing to learn.

---

### Post by troyready on 2008-12-08
Have you tried mysql -u root -p

This should bring up the password prompt.

---

### Post by Mattventura on 2008-12-08
Did you install from the desktop or server CD? If you installed from the server CD and selected to install LAMP, it should have let you select a password and automatically configured everything. If you installed from the desktop CD, you might just want to reinstall from the server CD and install any desktop packages you need if you are going to be using it as a desktop.

---

### Post by bmathis on 2008-12-08
Try these [instructions]("http://www.cyberciti.biz/tips/recover-mysql-root-password.html") to reset your root password for mysql. 

On another note, you can always do a

> sudo tasksel

and pick LAMP server to automatically install everything for you.

---

### Post by flukeairwalker on 2008-12-08
@ troyready: Typing what you suggested and typing in the password returns the error:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

@ Mattventura: I didn't install LAMP from a CD. I downloaded them through the command prompt. It did allow me to select a password when I installed it, but when I type it in, it doesn't work.

@ bmathis: Those were about the same instructions I had followed to reset the password. See my OP for details. Although if nothing else works, I will have to try what you suggested, and have the LAMP server do everything for me. I'm trying to learn though, so I'd like to exhaust this option first.

Thank you all for your help so far.

---

### Post by lykwydchykyn on 2008-12-08
Give this a try:
```

aptitude purge mysql-server
aptitude install mysql-server

```

Paste the output here, it may be informative.

---

### Post by flukeairwalker on 2008-12-08
@ lykwydchykyn: I wrote the first line in, typed the password and it was accepted. Typed the second line in, installed without a problem. Then I typed:

mysql -u root -p

To bring up the password prompt, and after typing in the password I got:

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

---

### Post by lykwydchykyn on 2008-12-08
Did you get prompted for a password during install?  If not I'd expect there is currently no password.  Try just:
```

mysql -u root

```

---

### Post by flukeairwalker on 2008-12-08
@ lykwydchykyn: Typing what you suggested gives the following error:

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

---

### Post by flukeairwalker on 2008-12-10
Is there anybody else out there who'd like a crack at this problem. If there's not response by lunch, I'm going to type sudo tasksel as suggested above though I don't know what will happen exactly when I do.

---

### Post by lykwydchykyn on 2008-12-10
Tasksel is just another front end to the package management, that allows you to choose package groups to install.  It usually runs at the end of an install so you can quickly set up certain "preset" configurations.  It's a convenience, I don't know that it will do anything for you, but it won't hurt a thing to try.

---

### Post by guitsy on 2009-07-11
hi friend.
the solution which worked for me
 
install webmin. to install webmin

Preparing Your System

You need to install the following packages

sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

Download latest webmin using the following command

wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.340_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.340_all.deb)

Now we have webmin_1.340_all.deb package you need to install using the following command

sudo dpkg -i webmin_1.340_all.deb

If your server complains that there is some library things does not find. Just run the following command

sudo apt- get install -f

You should now be able to login to Webmin at the URL [https://localhost:10000/](https://localhost:10000/)

go to webmin login
click on mysql
click change password option,put ur new password.....now on terminal type.

mysql -uroot  -p ..........bingoo......

---


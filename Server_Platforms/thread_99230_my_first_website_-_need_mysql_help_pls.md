---
title: "my first website - need mysql help pls"
date: 2005-12-05
forum: Server Platforms
---

### Post by ixus_123 on 2005-12-05
Hello.  I've been using Ubuntu now for quite some time & am lucky enough to have a fixed IP address from my ISP & terms & conditions that will let me host my own website from my computer (not may ISPs allow this in the UK or didn't when I was shopping around).

I recently upgraded to Breezy so that I could use Kmymoney2 & along with that, using the Automatix script app & ubuntuguide.org

I installed apache2, PHP, mysql all as per ubuntuguide

At first I only intended to run Gallery so friends could share photos - especially holiday photos.

So I figured I need some content management system.  I chose Joomla but fail at step 1 of the web install - incorrrect username & password for mysql

I have no idea what these could be.  I googled mysql docs & it said it has no password by defualt  & that they need to be set but I can't seem to figure out how to that

any ideas?

---

### Post by nemik on 2005-12-05
easiest way i can think of would be to install phpmyadmin and then add/change users in there with a nice GUI. after install, it should be in [http://localhost/phpmyadmin](http://localhost/phpmyadmin), load that on your browser.

then login with 'root' and no password, just blank. in there you can change users, so make sure to change that root user password from blank to something else.

next i would suggest adding another user to use in your php scripts that doesn't have all of the priveleges, just in case. also unless you need to access the mysql server directly from another IP, it is probably best to change both the root and the new user you made to access only from localhost.

once that's done try making an sqltest.php in your www directory and put this in it (making sure to change the variables on top to your new user):
<?php
    $dbhost = "localhost";
    $dbuser = "nemik";
    $dbpassword = "whatever";
    $db = "nemik";

    mysql_connect($dbhost, $dbuser, $dbpassword) or die();
    if(mysql_select_db($db))
    {
        echo "success";
    }
?>

open [http://localhost/sqltest.php](http://localhost/sqltest.php) and it should read success or at least give you an error you can fix.

good luck!

---

### Post by pasmith on 2005-12-05
Hi, I'm having a similar problem.

When I try to log in as root I get:
ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)

Is there some way to "reset" mysql so I can start over again? Its possible I messed with it as some point in the past and screwed up...

---

### Post by cactus on 2005-12-05
here is the first link google returned.
[http://news.postnuke.com/Article1273.html](http://news.postnuke.com/Article1273.html)

looks reasonable.

---

### Post by pasmith on 2005-12-05
Actually I found the default user (debian-sys-maint) in 

/etc/mysql/debian.cnf 

Logging in with this user looks to give me full access... the password isn't encrypted.

Once I got in, I saw there were 2 root users:

root@localhost with a password set (no idea what it was)
root@machinename with no password set.

I might have done this in my messing around, but it seems like something that could cause problems.

---

### Post by chipmonk010 on 2005-12-05
You can set the root password for mysql using the following command:

mysqladmin -uroot password *****

cheers 
chris

---

### Post by penguinman007 on 2005-12-06
[QUOTE=cactus]here is the first link google returned.
[http://news.postnuke.com/Article1273.html](http://news.postnuke.com/Article1273.html)

looks reasonable.[/QUOTE]

The first step of that minhowto does not work for me.

I need to log on to MySql and create a database.

However I am referred to cryptic install scripts all of which return usingpassword : NO
and some other rubbish.

Does anyone know whee there is a nice gui configured database that will work on linux ?

I would like to use that.
Because I don;t have time for your stupid linux scripts.

---

### Post by penguinman007 on 2005-12-06
[QUOTE=pasmith]Actually I found the default user (debian-sys-maint) in 

/etc/mysql/debian.cnf 

Logging in with this user looks to give me full access... the password isn't encrypted.

Once I got in, I saw there were 2 root users:

root@localhost with a password set (no idea what it was)
root@machinename with no password set.

I might have done this in my messing around, but it seems like something that could cause problems.[/QUOTE]

I too have that file on my system.
But I can't edit it or look at it because I'm not root.
I'm sure there is a file browser that has root access, I guess I should spend a few precious days of my life looking for it.

---


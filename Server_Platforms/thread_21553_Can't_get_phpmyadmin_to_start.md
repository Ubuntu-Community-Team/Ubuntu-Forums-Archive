---
title: "Can't get phpmyadmin to start"
date: 2005-03-22
forum: Server Platforms
---

### Post by obelix on 2005-03-22
I've downloaded the phpmyadmin_2.5.7-1_all.deb and I have installed it via dpkg -i 

I've restarted apache, and I first tried to login with the username "root" and the password blank. It then just reloads the page but does not produce any error messages. I then set my username and password via: 

mysqladmin -u root password "mypassword"

I then restarted apache again. I haven't restarted mysql though. I try logging in again and it still loads the login page again. I then went and edited my /etc/phpmyadmin/config.inc.php file and uncommented the following lines:

$cfg['Servers'][$i]['host']          = 'localhost'; // MySQL hostname or IP address
$cfg['Servers'][$i]['user']          = 'root';      // MySQL user
$cfg['Servers'][$i]['password']      = 'mypassword';          // MySQL password (only needed

I restart apache again and still it just reloads the page. As far as I can tell it seems to authenticate and the mysqld is running so I don't know whats going on. Any ideas guys?

---

### Post by oracledarren on 2005-03-22
I think that you might have to restart mysql.

This sounds odd though cause I did exactly the same and it works.

If you are still having problems try downloads xampp from [www.apachefriends.org](www.apachefriends.org) this is a combo package of mysql, apache and php

do read the command though that you will have to start with /opt/lampp/lampp security if you take this route  :o

---

### Post by obelix on 2005-03-22
I just restarted mysql... no luck there either. I've also tried making it load the "config" instead of the "cookie" but that just makes a blank page and I can't do anything... I can't even log in. So I'm at a total loss now.

---

### Post by oracledarren on 2005-03-22
Try xampp you get it working first time then  :-P

---

### Post by BloGTK on 2005-03-24
Well, you're not the only one with this problem. Since upgrading to Hoary, I'm getting the same thing.

If I had to guess, I'd say that php+mysql authentication is currently broken on Hoary. Anything that pulls authentication information from a database isn't doing anything right now. phpMyAdmin and WordPress are both broken on my machine. However, it isn't a general authentication problem - my Movable Type test install works just fine.

I'd imagine that this is a current bug in Hoary, and you'd better believe that it's something that needs to be fixed before the final release.

---

### Post by deuce868 on 2005-03-25
Hoary uses newer packages of MySQL that have a newer authentication method. I've run into this problem with phpmyadmin because it won't use the new method. You need to tell mysql to use the old authentication method.

Check out the following link. 
[http://dev.mysql.com/doc/mysql/en/old-client.html](http://dev.mysql.com/doc/mysql/en/old-client.html)

You should be able to set old passwords in mysql, change the password of the user, and then log in with phpmyadmin ok.

---


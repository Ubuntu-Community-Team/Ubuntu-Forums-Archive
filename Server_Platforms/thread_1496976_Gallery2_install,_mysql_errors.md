---
title: "Gallery2 install, mysql errors"
date: 2010-05-29
forum: Server Platforms
---

### Post by constellanation on 2010-05-29
I'm stuck at step 5 of gallery2 install"database setup"

I can get mysql started by typing: mysql -u root -p 
and putting in my password.

Then I typed the following.  (actually I've typed it a few times and a bunch of different ways)

$ mysqladmin -uroot create gallery2
$ mysql gallery2 -uroot -e"GRANT ALL ON gallery2.* TO username@localhost IDENTIFIED BY 'password'"

When I try to save the database setup i get an error (always it seems a slightly different one from "Warning: mysqli_real_connect(): (HY000/2005): Unknown MySQL server host 'hostname' (1) in /usr/share/php/adodb/drivers/adodb-mysqli.inc.php on line 109 Could't connect : 
hostname: Unknown MySQL server host 'hostname' (1)" to others depending on what combination of 
db hostname, username and password I try. (and I've tried every combination I can think of)  

This is my first time ever even using mysql, so some hand holding would be much appreciated.  and this point I'm wondering if there is anyway to erase everything I may or may not have created (including passwords,usernames and hostnames) and just try a new reinstall of mysql....

Any guidance would be very much appreciated, thank you.

---

### Post by krodrigue on 2010-05-30
> **constellanation said:**
> I'm stuck at step 5 of gallery2 install"database setup"

I can get mysql started by typing: mysql -u root -p 
and putting in my password.

Then I typed the following.  (actually I've typed it a few times and a bunch of different ways)

$ mysqladmin -uroot create gallery2
$ mysql gallery2 -uroot -e"GRANT ALL ON gallery2.* TO username@localhost IDENTIFIED BY 'password'"

When I try to save the database setup i get an error (always it seems a slightly different one from "Warning: mysqli_real_connect(): (HY000/2005): Unknown MySQL server host 'hostname' (1) in /usr/share/php/adodb/drivers/adodb-mysqli.inc.php on line 109 Could't connect : 
hostname: Unknown MySQL server host 'hostname' (1)" to others depending on what combination of 
db hostname, username and password I try. (and I've tried every combination I can think of)  

This is my first time ever even using mysql, so some hand holding would be much appreciated.  and this point I'm wondering if there is anyway to erase everything I may or may not have created (including passwords,usernames and hostnames) and just try a new reinstall of mysql....

Any guidance would be very much appreciated, thank you.

Why don't you install phpmyadmin - apt-get install phpmyadmin

I use it to connect to my data base and to create them, you will need to no you passwd for the mysql data base...it's what you used while installing mysql.

to connect [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

### Post by constellanation on 2010-05-30
I do have that installed.  However I don't know how to make anything with it (i'm very new to servers.)
how would i do the equivalent of the commands:

$ mysqladmin -uroot create gallery2
$ mysql gallery2 -uroot -e"GRANT ALL ON gallery2.* TO username@localhost IDENTIFIED BY 'password'"
  
in phpmyadmin?

---

### Post by constellanation on 2010-05-31
no one here has any advice? i've spent the last three days after work trying to find an answer and have gotten nowhere...

---

### Post by constellanation on 2010-05-31
if it helps for anyone willing to help... this latest error.

Warning: mysqli_real_connect(): (HY000/2003): Can't connect to MySQL server on '192.168.1.100' (111) in /usr/share/php/adodb/drivers/adodb-mysqli.inc.php on line 109 Could't connect : 
192.168.1.100: Can't connect to MySQL server on '192.168.1.100' (111)

---

### Post by constellanation on 2010-05-31
not sure how to mark this as solved, but i figured it out.  rather simple was not using the right username.  i guess it assigned  a username(root) and I thought i had assigned my own.

---

### Post by bemenaker on 2010-06-01
I used gadmin to setup my database, since I did a desktop install and have gnome available.  Are you passing the username and password in your login to mysql?

Also, you may need to do some more configuration of apache before you are ready. In your httpd.conf file for apache did you add the line:
Servername localhost
?
[http://mohamedaslam.com/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu/](http://mohamedaslam.com/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu/)

If you are trying to connect by a dns name, is that name in your dns server, or in your host file?

---

### Post by constellanation on 2010-06-01
Thank you for replying Bemenaker! however I got it figured out last night (it helps having a father who is a system admin)  I was using the wrong log in information.

---


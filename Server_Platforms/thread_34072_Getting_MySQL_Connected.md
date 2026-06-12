---
title: "Getting MySQL Connected"
date: 2005-05-13
forum: Server Platforms
---

### Post by skicam07 on 2005-05-13
Ok, I'm a first time Linux user, so bear with me.
I've tinkered with Apache, Mysql, and php on windows, but now I want to set up LAMP.  I'm running Hoary on a PIII if that makes any difference.

Apache is working great (I get the welcome screen when I point my browser to localhost), and I think PHP is ok too.  I downloaded all the MySQL administration GUIs I could find. (MySQL CC, MySQL Admin, MySQL Navigator), launched MySQL CC, and set up the server.  I said Access Denied.  I had
Name: chetserver
Hostname: localhost
Username: chet
Password: *******

I tried a bunch of things and none worked.  The MySQL Admin tool couldn't connect either.  I thought the server hadn't been started, so I went to terminal and did something like:
/usr/bin/mysqld_safe --user=mysql which my LAMP book said to do.  That gave a fatal error and said I needed to delete a pid file in /var/somewhere/.  I didn't have permission to delete the pid file (I am the administrator, so I can probably delete through root, right?), so I searched for something else that might work.

then I tried.
/etc/init.d/mysql start (I may not have the spelling right because I'm away from the computer).  It said the server was already running.

My question is, is the server running or not, and do I need to delete that .pid file to get my server working if it isn't?

Any other tips on getting MySQL running would be great.  Once I get that set up I should be good.  Thanks in advance.

---

### Post by Gandalf on 2005-05-13
[QUOTE=skicam07]Ok, I'm a first time Linux user, so bear with me.
I've tinkered with Apache, Mysql, and php on windows, but now I want to set up LAMP.  I'm running Hoary on a PIII if that makes any difference.

Apache is working great (I get the welcome screen when I point my browser to localhost), and I think PHP is ok too.  I downloaded all the MySQL administration GUIs I could find. (MySQL CC, MySQL Admin, MySQL Navigator), launched MySQL CC, and set up the server.  I said Access Denied.  I had
Name: chetserver
Hostname: localhost
Username: chet
Password: *******

I tried a bunch of things and none worked.  The MySQL Admin tool couldn't connect either.  I thought the server hadn't been started, so I went to terminal and did something like:
/usr/bin/mysqld_safe --user=mysql which my LAMP book said to do.  That gave a fatal error and said I needed to delete a pid file in /var/somewhere/.  I didn't have permission to delete the pid file (I am the administrator, so I can probably delete through root, right?), so I searched for something else that might work.

then I tried.
/etc/init.d/mysql start (I may not have the spelling right because I'm away from the computer).  It said the server was already running.

My question is, is the server running or not, and do I need to delete that .pid file to get my server working if it isn't?

Any other tips on getting MySQL running would be great.  Once I get that set up I should be good.  Thanks in advance.[/QUOTE]
 try
mysql -u root -p

it will ask for root password enter it, if none just press enter, will it connect?

---

### Post by skicam07 on 2005-05-13
Yes, thank you!  It connected with no password.

---

### Post by Gandalf on 2005-05-13
[QUOTE=skicam07]Yes, thank you!  It connected with no password.[/QUOTE]
 no problem
type mysqladmin -u root -p password "new password" if you want to change it

---


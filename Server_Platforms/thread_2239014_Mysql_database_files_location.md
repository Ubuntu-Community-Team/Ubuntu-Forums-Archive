---
title: "Mysql database files location"
date: 2014-08-11
forum: Server Platforms
---

### Post by r4zv4n on 2014-08-11
Hi. I am unable to find my files that i have uploaded through owncloud. Owncloud used to be conected to a certain database . Is there a way to find them?

---

### Post by JetStorm on 2014-08-11
I'm not familiar with owncloud but MySQL data files in Ubuntu and Debian are stored by default in /var/lib/mysql

---

### Post by r4zv4n on 2014-08-11
The weird thing is that after updating OwnCloud to the newest version everything changed for ex: I cannot login to phpmyadmin , no password is recognized anymore.
All my files that I have updated through OwnCloud are nowhere to find.There is a way of resetting phpmyadmin so that will recognize my passwords after?

---

### Post by nerdtron on 2014-08-11
Seems to me that you are just following a tutorial and blindly following commands? Be careful when installing software on your servers, and read thoroughly on each command so that you'll know what it does on your system and how it affects the services already installed.
Anyway, try resetting the password: [http://www.cyberciti.biz/tips/recover-mysql-root-password.html](http://www.cyberciti.biz/tips/recover-mysql-root-password.html) 
After that, your owncloud config might need to be updated for the new password.

---


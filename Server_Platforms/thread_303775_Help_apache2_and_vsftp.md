---
title: "Help apache2 and vsftp"
date: 2006-11-20
forum: Server Platforms
---

### Post by jbtito03 on 2006-11-20
Oi...

installed Ubuntu LAMP server... played around... and now **** :D

Actually i messed up PHP5 with the installation of egroupware or something that installed php4 and now, when i uninstalled it... PHP does not work... 

It has to do something with the libapache2-mod-php5 as it is installed but apt-get says that it is disabled ot not installed...


How to fix this one..


and


I am behind a firewall so i had to open up some ports on the router....

When trying to access the ftp acc... i get this message

Error:	Transfer channel can't be opened. Reason: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.
Error:	Could not retrieve directory listing

In my local network everithing is fine and yes, in the conf file i included passive mode and the ports for listening (data and cfg).

What to do?

Thax for any help

JB

---

### Post by adamkane on 2006-11-20
Sometimes a re-install works, but most like you need to re-install Ubuntu to get it all working again. Sorry :( For some reason, LAMP doesn't uninstall completely.

Here's what you need to try a re-install:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

-----------------------------------------------------------------------------

Apache2/PHP-latest/MySQL-latest, install XAMPP:
[http://www.ubuntuforums.org/showthread.php?t=223410](http://www.ubuntuforums.org/showthread.php?t=223410)

---

### Post by jbtito03 on 2006-11-21
Okey did this and it does not work as before. But there has to be something else than re-installation of the whole LAMP. 


also

Anyone with a solution about vsftpd?

Come on... thx

JB

---

### Post by jsowell on 2007-11-13
I have trouble establishing apache2 all together. Any help will be appreciated. Also, how can i switch between using apache and samba?

---


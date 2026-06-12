---
title: "enabling MySql functions in PHP"
date: 2006-02-11
forum: Server Platforms
---

### Post by luna6 on 2006-02-11
I am having a difficult time getting MySQL functions in PHP to work on my server. I do have php4-mysql installed from apt-get...but I am guessing I have to edit a configuration file to get it working correctly. When I go to the directory I have vbulletin installed ...forum/install/install.php I get this error message on my browser  "reuqires MySQL functionis in PHP be available. Please ask your host to enable this," and for wordpress when i go  to .../blog I get this error message on my browser "Your PHP installation appears to be missing the MySQL which is required for WordPress".  Any help would be greatly appreciated..


I have installed php4-mysql 4:4.4.0-3, php4 & php4-common 4:4.4.0-3, libapache-mod-php4 4:4.0.0-3, libapache2-mod-php4 4:4.0.0-3, 
mysql-server & mysql-common & mysql-client 4.0.24-10ubuntu2, 
apache 1.3.33-8, apache2-common 2.0.54-ubuntu4, apache-common 1.3.33-8, libapache-mod-acct-mysql 0.5-15, libapache-mod-php4 4:4.4.0-3, libapache2-mod-auth-mysql 4.3.9-2ubuntu1, libapache2-mod-php4 (not sure why apache 1.3 and apache2 were both installed, but when installing gallery through apt-get it installed both)....

---

### Post by Horndog on 2006-02-12
All I can suggest is to fist look on your system monitor and see If MySQL is running. If not then look for your error log for some clues. I remember I had one error that had something to do with a PID file missing and would not stay running.

---

### Post by bastya_elvtars on 2006-02-12
Go to php.ini and check if the mysql module is loaded. Oh, and why do you have 2 apaches installed?

---

### Post by squirrelyosis on 2006-02-12
bastya's probably right.  Here is the link on the right way to setup a LAMP server.  I couldn't get things working until I edited the php.ini file to load the mysql module.

[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---


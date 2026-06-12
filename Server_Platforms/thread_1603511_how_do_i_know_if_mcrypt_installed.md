---
title: "how do i know if mcrypt installed"
date: 2010-10-22
forum: Server Platforms
---

### Post by feelexit on 2010-10-22
I am using ubuntu 10.04 server.  after i installed nginx, php and myslq, i found out  that mcrypt module is missing.

so i installed mcrypt  using this command "apt-get install -y mcrypt"

then I check the module in phpinfo() page. coudln't find it.

i can see mcrypt.ini file in "/etc/php5/conf.d". so mcrypt.ini should be installed.

btw, I go to phpmyadmin page, i saw this message "Cannot load mcrypt extension. Please check your PHP configuration.".

---

### Post by BkkBonanza on 2010-10-23
You also need to install the **php5-mcrypt** package and be sure to restart the web server (or php itself, if not running php as an apache module).

A useful command for cases like this is **aptitude search mcrypt**. It will show you what packages have mcrypt in the name and are related to it. For example, you see libmcrypt-dev which you would need if you were compiling a program against mcrypt and needed the headers (not needed for php).

---

### Post by feelexit on 2010-10-23
BkkBonanza, you are rite.  I already have php5-mcrypt  installed.

the problem is I only restart my nginx server. I didnt know php5-fpm needs to be restarted at well.  now problem solved. 

thank you.

---


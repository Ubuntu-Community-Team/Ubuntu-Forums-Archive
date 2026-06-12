---
title: "cacti problem solved"
date: 2005-02-17
forum: Server Platforms
---

### Post by radeon on 2005-02-17
Hello I want it for bugzilla but I !@$%#$ for another pass/login 
so for cacti deb developer ...

to work cacti as it should ... add in /etc/php4/cgi/php.ini
line "extension=mysql.so" or uncomment it 

Bye

---

### Post by ola on 2005-05-28
I had some other problems with cacti.. The output when I ran the cmd.php file was something like this

> 
/usr/share/cacti/cmd.php
Mysql module not loaded!
Please (re-)run: "dpkg-reconfigure php4-mysql" or modify your php4 configruation manually


the problem was solved using > dpkg-reconfigure php4-mysql and enabling everything...

---


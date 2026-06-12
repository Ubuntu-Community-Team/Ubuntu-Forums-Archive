---
title: "Problem with php @ command line"
date: 2007-01-24
forum: Server Platforms
---

### Post by Syirrus on 2007-01-24
I know this is probably an easy fix.  I have installed the server version on Ubuntu and everything is going well.  Apache2 and php 5.x and mysql run perfectly.  However, when I try and run a script from the command line get a:

Call to undefined function mysql_connect() in /var/www/web/includes/function.php on line 15

unless I run the script from the /etc/php5/apache2/ directory which it executes successfully.  Is there a way I can make it so I can run the cmd from any directory?  I have setup cron, but I get the above error b/c of the directory issue. 

Syirrus

---

### Post by JamieC on 2007-01-24
What is the output of the following:
```

php -m

```

---

### Post by Syirrus on 2007-01-24
[PHP Modules]
bcmath
bz2
calendar
ctype
curl
date
dba
dom
exif
filepro
ftp
gd
gettext
hash
iconv
libxml
mbstring
mcrypt
mime_magic
mysql
mysqli
ncurses
openssl
pcntl
pcre
posix
Reflection
session
shmop
SimpleXML
soap
sockets
SPL
standard
sysvmsg
sysvsem
sysvshm
tokenizer
wddx
xml
xmlreader
xmlwriter
zlib

[Zend Modules]

---

### Post by JamieC on 2007-01-24
Copy the file to the directory where it works and a directory where it doesn't, then run both through a terminal and paste the results and commands here.

---

### Post by Syirrus on 2007-01-24
Directory where it works 

[PHP]


Warning: include(/etc/php5/apache2/../sms/includes/sms_data.php): failed to open stream: No such file or directory in /etc/php5/apache2/group_process.php on line 6

Warning: include(): Failed opening '/etc/php5/apache2/../sms/includes/sms_data.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /etc/php5/apache2/group_process.php on line 6

Warning: include(/etc/php5/apache2/../sms/includes/sms_function.php): failed to open stream: No such file or directory in /etc/php5/apache2/group_process.php on line 7

Warning: include(): Failed opening '/etc/php5/apache2/../sms/includes/sms_function.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /etc/php5/apache2/group_process.php on line 7

Fatal error: Call to undefined function sql_connect() in /etc/php5/apache2/group_process.php on line 9


[/PHP]

Is this what you mean?

---

### Post by JamieC on 2007-01-24
And the directory where it doesn't work? Don't forget to post both commands you used too.

---

### Post by Syirrus on 2007-01-24
This is what it gives from the directory where it doesn't work:

Fatal error: Call to undefined function mysql_connect() in /var/www/web/includes/sms_function.php on line 15

---

### Post by smartbei on 2007-03-10
Had the same problem. Goto:
/etc/php5/cli and edit php.ini so the line ';extension=mysql.so' is 'extension=mysql.so' - remove the semicolon.

---


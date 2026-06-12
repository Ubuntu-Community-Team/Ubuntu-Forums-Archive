---
title: "PHP MySQL Question"
date: 2005-05-04
forum: Server Platforms
---

### Post by firefly2442 on 2005-05-04
Is there a difference between "libapache2-mod-php4" and "php4"?  Because when I try to install php4 and then php4-mysql it installs the libapache one instead and then mysql doesn't seem to be compiled in the options of php.  Mysql is running and everything but php just doens't seem to recognize it....

Thanks for the help. :)

---

### Post by bnutting on 2005-05-04
I believe ( I could be wrong ) that one is the apache module and the other is the php binary. I believe that the php4 binary is not compiled with mysql support, but the php4-cgi binary is. The php4 binary ( that you can use in a shell script ) does not support mysql but the php4-cgi ( which can also be used in a shell script ) does have mysql support.

Not sure if this helps. You will also see a package for php4-cli which is the command line interpreter.

---

### Post by dewey on 2005-05-07
php4 should have native mysql support.
php5 is the one that removed mysql by default, and you have to specify for it at compile.
```
./configure --with-mysql
```

---

### Post by LordHunter317 on 2005-05-07
Nope. 

PHP4 isn't compiled with MySQL support.  You have to install it via php4-mysql.

The "php4" package is just a metapackage, it doesn't contain a thing. You have to install 'libapache2-mod-php4' for DSO support for PHP4 in Apache2, or php4-cgi for the PHP4 cgi script (not recommended unless you know what you're doing, and if you did, you wouldn't be asking this question).

What may have happened depending on how you installed things is the ini file for the PHP4 loaded into Apache2 may not have mysql support being loaded. To do this, add the line:```
extension=mysql.so
``` to /etc/php4/apache2/php4.ini, then restart Apache. This will have the support.

The same applies to any other form of PHP you install. You need to edit the .ini file to install support for that PHP module. It should happen automatically, but it doesn't always. There is a different ini file for each for of PHP (e.g., CGI, CLI, Apache1 DSO, Apache2 DSO).

---

### Post by firefly2442 on 2005-05-07
Thanks for the help.  I got it working. :)

---


---
title: "Wrong permissions on configuration file, should not be world writable!"
date: 2010-03-16
forum: Server Platforms
---

### Post by minicaso on 2010-03-16
Wrong permissions on configuration file, should not be world writable!

I encountered a problem when I am trying  to access my phpmyadmin… the error came up:
 Wrong permissions on configuration file,  should not be world writable!


help plz

---

### Post by volkswagner on 2010-03-16
What config file?  Is it for PhpMyadmin itself?  Often when installing programs manually, config files are installed with loose permissions making configuration easy.  Usually the instructions tell you to chmod the files as soon as config is complete.  Some even have you move the file.

---

### Post by minicaso on 2010-03-16
/var/www/phpmyadmin/config.inc.php

---

### Post by dudumomo on 2010-03-16
I guess you /var/www is 777.
You should do a chmod 755.

---

### Post by minicaso on 2010-03-16
it works now .....10000 thanks

---

### Post by KB1JWQ on 2010-03-16
This should have been mentioned in the phpmyadmin documentation.  Please either let them know so they can update it, or kick yourself for not reading it. :-)

---

### Post by haafmaad on 2010-10-01
Anyway In ubuntu 10.04(Lucid lynx) I didnt found any /var/www directory.


Instead in your lampp installation directory, In my case:

/opt/lampp/htdocs/xampp/mysql.php

I found the line mysql_connect("localhost");

edit that line, add the username,password: mysql_connect("localhost"."mysql_username","password");

and then chmod the file to 0755.

That works for me

---

### Post by vaibhav.sidapara on 2012-08-23
> **haafmaad said:**
> Anyway In ubuntu 10.04(Lucid lynx) I didnt found any /var/www directory.


Instead in your lampp installation directory, In my case:

/opt/lampp/htdocs/xampp/mysql.php

I found the line mysql_connect("localhost");

edit that line, add the username,password: mysql_connect("localhost"."mysql_username","password");

and then chmod the file to 0755.

That works for me
thanks.. it worked for me!!

---


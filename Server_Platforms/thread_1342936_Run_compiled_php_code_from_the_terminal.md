---
title: "Run compiled php code from the terminal"
date: 2009-12-01
forum: Server Platforms
---

### Post by darkksyde on 2009-12-01
Hey guys,
 
What im trying to do is execute php code i compiled with bcompiler from the terminal.
If i execute the non compiled code from the terminal, it will run fine, but when i compile it with bcompiler it will just output unknown symbols. Also it will work fine if i go to localhost/test_compiled.php. Does anyone know what i am doing wrong?
 
Any help would be great,
Thanks

---

### Post by darkksyde on 2009-12-02
bump

---

### Post by alephiej on 2009-12-05
I'm not sure about bcompiler, but if it is like zend, then you probably would need to add a line to /etc/php5/cli/php.ini
Just execute 
php -i |grep php.ini

and see if it is the same as php.ini location returned from apache php module phpinfo(); command

Hope this will help you.

---


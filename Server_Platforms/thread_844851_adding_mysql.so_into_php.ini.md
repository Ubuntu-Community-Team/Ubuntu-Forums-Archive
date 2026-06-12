---
title: "adding mysql.so into php.ini"
date: 2008-06-30
forum: Server Platforms
---

### Post by jwxie on 2008-06-30
Another issue was making mysql run with php5
First install these packages:
> sudo apt-get install php5-mysql mysql-client

then edit php.ini and add to it this line : ” extensions=mysql.so” if it isnt already there
> sudo gedit /etc/php5/apache2/php.ini

my question is
when i use gedit to edit php.ini
where do i add the line?

and is it  extension instead of extensions?

---

### Post by windependence on 2008-06-30
This must me switched on in your PHP.ini file. The entry can be found in EXTENSIONS section. Just remove the semi-colon in front of it.

-Tim

---


---
title: "Phpmyadmin work fine after install, but then…"
date: 2009-07-06
forum: Server Platforms
---

### Post by bigden on 2009-07-06
Hi every1
 
On a clean and freshly install Ubuntu Server 9.04, with a lamp stack running and phpmyadmin running fine and accessing the databases.
 
But when I make the following changes to /etc/apache2/envvars
export APACHE_RUN_USER=webdev
export APACHE_RUN_GROUP=webdev
and then when I tried to log into phpmyadmin from [http://localhost/phpmyadmin](http://localhost/phpmyadmin),
I get a white page. I think it has to do with changing the user and group from www-data to webdev
 
Help anybody!

---

### Post by bigden on 2009-07-06
Problem is solved, I added weddev to the www-data group, and voila!
 
Have a nice day

---


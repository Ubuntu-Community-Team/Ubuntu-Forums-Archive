---
title: "easy way to do php/phpmyadmin/mysql"
date: 2007-05-30
forum: The Cafe
---

### Post by ELD on 2007-05-30
Basically i wish to test php scripts i have made on my ubuntu install, is there an easy way to have php/phpmyadmin and all that?

Thanks guys.

---

### Post by mech7 on 2007-05-30
[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

---

### Post by ELD on 2007-05-30
Sorted, thanks a lot!

---

### Post by ticopelp on 2007-05-30
sudo apt-get install apache
sudo apt-get install mysql-server

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_MYSQL_Database_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_MYSQL_Database_Server)

Much more elegant and reliable than Xampp in my opinion.

---

### Post by tehbeermang on 2007-05-30
Applications -> add/remove programs -> search for "Apache", click the box next to the package you need, select "mark for installation" on the resulting menu. It will say "you also need these libraries" and might warn you about packages that do not fall under the GPL.

Repeat for MySQL, PHP, and phpmyadmin. 

I had it up and running in an hour, and I'm pretty green in terms of Linux experience.

---


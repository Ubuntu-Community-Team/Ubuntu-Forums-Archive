---
title: "how to run php webservice in ubuntu 10.04"
date: 2010-05-31
forum: Server Platforms
---

### Post by sangtech on 2010-05-31
Hi everyone ! I'm a new bie. I've just install LAMP system on ubuntu 10.04 using a lot of command , such as : apt-get install apache2, sudo apt-get install php5 libapache2-mod-php5, sudo apt-get install mysql-server. And my web server work well with php and MySQL.
I need to run php web service in my system, but it show a blank page when i run it.

how can i run php webservice in my LAMP system (ubuntu 10.04)?:(
-Thanks-

---

### Post by Ryan Dwyer on 2010-05-31
It could be caused by many things.

Did you restart the apache service after installing libapache2-mod-php5?
If you view the source, can you see the <?php tag?
Could your script have a parse error in it?

---

### Post by sangtech on 2010-06-01
I can solve that problem! :) I've just read this topic : [http://mpathirage.com/getting-started-with-web-services-in-php-with-ubuntu-804-4/](http://mpathirage.com/getting-started-with-web-services-in-php-with-ubuntu-804-4/)

---


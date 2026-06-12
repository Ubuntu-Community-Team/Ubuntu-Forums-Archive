---
title: "Apache2/php/mysql/ Wordpress images and css not showing"
date: 2011-10-24
forum: Server Platforms
---

### Post by 1885 on 2011-10-24
Solved:  chmod 777 -R wp-contents/

Wordpress images and css not showing from clients but I can see a normal workdpress page from the server using firefox.

?  Any ideas?

> Just installed Ubuntu 11.04 on a Dell sc1425.
Apache2, php5, mysql, bind9 and ect. . .

> I also installed wordpress 3.2.1
set up database ect.

> Put wordpress in /home/user/html/
> #chown user -R /home/user/html/*
> #chmod 755 -R /home/user/html/
>  #chmod 755 -R /home/user/html/*

---

### Post by 1885 on 2011-11-05
Solved:

I changed permission of wp-contents to 777

---


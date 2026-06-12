---
title: "Xubuntu all set up just a few questions?"
date: 2006-10-18
forum: Server Platforms
---

### Post by ade234uk on 2006-10-18
I have installed Xubuntu with LAMP. 
It all appears to be working as when I goto [http://localhost](http://localhost) the default apache page appears.

I have also tested the php configuration by adding a <? phpinfo(); ?> file to the default apache folder and everything appears to be installed when I access it from [http://localhost/apache2-default/phpinfo.php](http://localhost/apache2-default/phpinfo.php)

1) How do I start / stop / restart apache from the command line?
2) How do I start / stop  mysql from the command line?

I am going to be using XUbuntu as a testing server. One of the scripts I use requires that Zend should be installed with ION Cube. 

3) Where do i get Ion Cude for PHP5.x
4) How would I install it so it binds with PHP and Zend?

---

### Post by bluefrog on 2006-10-18
sudo /etc/init.d/apache2 start
sudo /etc/init.d/mysql start

don't know for the rest...

James

---

### Post by tomBorgia on 2006-10-18
"1) How do I start / stop / restart apache from the command line?"

sudo apache2 -k restart

"2) How do I start / stop mysql from the command line?"

sudo mysqld_safe &

"3) Where do i get Ion Cude for PHP5.x"

I seems there is a download from thier website that has 4 / 5 support.. 

"4) How would I install it so it binds with PHP and Zend?"

Sorry bud, no idea!

---

### Post by ade234uk on 2006-10-18
3/4 answered excellent. Thank you very very much. Will let you know how I get on istalling ION Cube to php

---


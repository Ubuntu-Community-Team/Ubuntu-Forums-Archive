---
title: "New 8.04 server install, php5 not working?"
date: 2008-11-05
forum: Server Platforms
---

### Post by blkmax on 2008-11-05
Hi, I just built a new server with 8.04 using the L.A.M.P. option during install. 

Problem is that after the install, I tested it by creating a new test.php file in /var/www/ with < ?php phpinfo(); ?> in it. when I open firefox and point it to [http://localhost/test.php](http://localhost/test.php), it only displays < ?php phpinfo(); ?> instead of runing it.

I get the following when I run a2enmod.

root@1365:~# a2enmod php5
This module is already enabled!

I am assuming that instaling the Ubuntu LAMP install on a Ubuntu server should have the config files set to the proper file locations. If not, what do I need to do with my config files.

Marc

---

### Post by blkmax on 2008-11-05
after a while, I noticed that the info I copied to paste into the document had a space afte the <  

so it was:   < ?php phpinfo(); ?>
instead of : <?php phpinfo(); ?>


PHP is working properly.


Marc

---


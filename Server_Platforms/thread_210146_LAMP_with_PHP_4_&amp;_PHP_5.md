---
title: "LAMP with PHP 4 &amp; PHP 5"
date: 2006-07-06
forum: Server Platforms
---

### Post by TheApe on 2006-07-06
Hi all!
I have a LAMP server running Apache 2 + PHP 4 + Mysql 4.1
But now, I have some tests to be done with PHP 5, I'd like to know how to setup  Apache to  run both with PHP 4 and PHP5 ... This is the priority

Besides, I'd like to know if is it possible to install both Mysql 4 and 5 on the same server...

Thanks!!
:rolleyes:

---

### Post by Randomskk on 2006-07-06
You can set up Apache so that, say, .php4 files are run as PHP4 and .php are run as PHP5, but the norm is to just have one version of PHP running at a time.

The easiest way to do this is probably to install PHP5:
sudo apt-get install php5 php5-mysql
This will enable PHP5, and then once you restart Apache you should see the new PHP:
sudo apache2ctl restart

The easiest way to check what version of PHP you are on is by putting this in a .php file:
<?php phpinfo() ?>
Then when you open the file, the PHP version number is at the top.

To disable PHP5:
sudo a2dismod php5

To re-enable PHP5:
sudo a2enmod php5

To enable PHP4:
sudo a2enmod php4

To disable PHP4:
sudo a2dismod php4

That should all work, although I can't test it right now, let me know how you get on.

**edit**: You can install both versions of MySQL on the same server I *think*, but you can't have both running.
The best bet is to just keep one version installed, if you must swap just remove that and install the other version.

---

### Post by TheApe on 2006-07-06
Thanks, Randomskk!
I'll give a try...
But I wanted both running 'cause I have to test several things... on both.. php 4 and 5. And mysql's as well.
I'd like to do something like having [http://localhost/](http://localhost/) for php 4 and [http://localhost:Someport](http://localhost:Someport) for php 5.

The same for mysql, running on a diferent port....
Would it be possible?
Thanks again!
;-)

---

### Post by Randomskk on 2006-07-06
Using a different port, you'd pretty much have to have two different Apaches running, which isn't very feasible, and each would need to be configured differently.
Using .php4, .php[5] may be easier, or just swapping the PHP modules.

Using MySQL like that would also need two copies of MySQL - again, pretty hard to set up. You'd be best just using one at a time.

---

### Post by az on 2006-07-06
I don't think the same instalce of apache ca nrun the php4 and the php5 module at the same time without a lot of judo.

It would probably be easier to run two instances of apache, each listening on different ports.

[http://lwn.net/Articles/173733/:](http://lwn.net/Articles/173733/:)
"This tutorial shows how to install and configure Apache2 with PHP5 and PHP4 enabled at the same time. Because it is not possible to run both PHP5 and PHP4 as Apache modules, we must run one of them as CGI, the other one as Apache module."

and:

[http://wiki.coggeshall.org/37.html](http://wiki.coggeshall.org/37.html)

" To solve this problem, I used Apache's mod_proxy module and two apache servers... My primary server runs PHP 5 as an Apache module and a second apache server runs PHP 4.3.5 as a module. My configuration requires that you can setup multiple virtual servers and run Apache to listen on localhost on port 8080. Here's what I did:"

---

### Post by arix on 2006-07-12
You can run PHP4 and PHP5 at the same time very simple, for ex. run php4 as cgi and php5 as module.Falko writes an excelent how to [http://www.howtoforge.com/apache2_with_php5_and_php4]("http://www.howtoforge.com/apache2_with_php5_and_php4")

---

### Post by az on 2006-07-12
> **arix said:**
> You can run PHP4 and PHP5 at the same time very simple, for ex. run php4 as cgi and php5 as module.Falko writes an excelent how to [http://www.howtoforge.com/apache2_with_php5_and_php4]("http://www.howtoforge.com/apache2_with_php5_and_php4")

How do you get a web application to use php4 instead of php5?

---


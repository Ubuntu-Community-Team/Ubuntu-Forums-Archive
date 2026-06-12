---
title: "phpmyadmin not appearing"
date: 2007-09-11
forum: Server Platforms
---

### Post by bps4484 on 2007-09-11
Hello,

I'm a complete linux/ubuntu newbie trying to set up LAMP, and I'm almost there but phpmyadmin is not appearing.  From what I understand, when I go to [http://localhost/phpMyAdmin](http://localhost/phpMyAdmin) it should give me a db gui.  Instead it just gives me:

> The requested URL /phpMyAdmin was not found on this server.

I'm following the directions found here:

[https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28apache%29](https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28apache%29)

which worked wonderfully up to this point. (I've checked that apache, php, and mysql all work, and php can access mysql)

I've already made sure to enable the universe and multiverse repositories, and have edited /etc/apache2/apache2.conf to have the line:

Include /etc/phpmyadmin/apache.conf

None of this has solved my problem.  some details of what I'm running:

ubuntu 7.04 fiesty fawn
apache 2
php 5.1.2
mysql 5.0.38
phpmyadmin 2.9.1.1

Thanks for the help.

---


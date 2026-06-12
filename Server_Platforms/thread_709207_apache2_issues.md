---
title: "apache2 issues"
date: 2008-02-27
forum: Server Platforms
---

### Post by gjj391 on 2008-02-27
i have installed apache2 successfully and other componets, but when i try and run my test php script, my browser is prompted to open the file rather than run it.

packages i installed and others prompted to install during apache2 and php

apache2-mpm-worker apache2-utils apache2.2-common libapr1 libaprutil1 libpq5 apache2-doc
php5 libapache2-mod-php5 apache2-mpm-prefork

---

### Post by PmDematagoda on 2008-02-27
This thread has been moved to the Server Platforms section.

---

### Post by azadpanchi on 2008-02-27
May sound stupid but have you restarted apache?

Also were all these packages added through apt-get / package manager?
Just for giggles try to rename the script index.php and go to it as [http://localhost](http://localhost)

I would first try to remove libapache2-mod-php5 and then reinstall the package.  If that doesn't work uninstall all those packages and reinstall them, if you don't want to do that  then you need to go through httpd.conf to see where the problem maybe.  I would look to follow directions in this article:
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

---

### Post by faulkes on 2008-02-27
Also see the following thread:

[http://ubuntuforums.org/showthread.php?t=708721](http://ubuntuforums.org/showthread.php?t=708721)

That user appears to be having similar problems to yours (and have been
at least partially solved so far).

Faulkes

---

### Post by djsky on 2008-02-27
> **gjj391 said:**
> i have installed apache2 successfully and other componets, but when i try and run my test php script, my browser is prompted to open the file rather than run it.

packages i installed and others prompted to install during apache2 and php

apache2-mpm-worker apache2-utils apache2.2-common libapr1 libaprutil1 libpq5 apache2-doc
php5 libapache2-mod-php5 apache2-mpm-prefork


I ran into the same problem a while ago.  I followed the tutorial at:

[http://www.howtoforge.com/perfect_server_ubuntu7.10_p6]("http://www.howtoforge.com/perfect_server_ubuntu7.10_p6") 

I used it to install apache2 and php5.  It worked for me and solved the php files opening problem.  Hope this helps.

---

### Post by az on 2008-02-27
> **gjj391 said:**
> i have installed apache2 successfully and other componets, but when i try and run my test php script, my browser is prompted to open the file rather than run it.

packages i installed and others prompted to install during apache2 and php

apache2-mpm-worker apache2-utils apache2.2-common libapr1 libaprutil1 libpq5 apache2-doc
php5 libapache2-mod-php5 apache2-mpm-prefork

I think you need to use apache2-mpm-prefork instead of apache2-mpm-worker.

As well, clear your browser cache to see if the problem is actually fixed.  You can have fixed the problem, but continue to experience the issue, because your browser will keep the non-working result in its cache.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


tasksel --task-packages lamp-server
apache2
mysql-client-5.0
libapache2-mod-php5
apache2.2-common
apache2-utils
php5-common
libaprutil1
php5-mysql
libmysqlclient15off
libdbi-perl
mysql-server
libplrpc-perl
mysql-server-5.0
libdbd-mysql-perl
libnet-daemon-perl
libapr1
libxml2
libpcre3
libpq5
apache2-mpm-prefork
mysql-common

---


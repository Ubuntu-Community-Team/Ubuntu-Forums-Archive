---
title: "phpmyadmin access not granted."
date: 2011-07-03
forum: Server Platforms
---

### Post by kiran_viswm on 2011-07-03
i set up a localhost in my system. but am not getting access to the phpmyadmin by entering the user name and password i entered at the time of set up.
the /etc/phpmyadmin/config-db.php file is shown below.

<?php
##
## database access settings in php format
## automatically generated from /etc/dbconfig-common/phpmyadmin.conf
## by /usr/sbin/dbconfig-generate-include
## Sun, 03 Jul 2011 10:19:02 +0530
##
## by default this file is managed via ucf, so you shouldn't have to
## worry about manual changes being silently discarded.  *however*,
## you'll probably also want to edit the configuration file mentioned
## above too.
##
$dbuser='user';
$dbpass='password';
$basepath='';
$dbname='phpmyadmin';
$dbserver='';
$dbport='';
$dbtype='mysql';

when i access [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) , the login screen appears but entering the username and password as in the file gives the error
#1405 cannot log into mysql server.
please help..

---

### Post by Dangertux on 2011-07-03
> **kiran_viswm said:**
> i set up a localhost in my system. but am not getting access to the phpmyadmin by entering the user name and password i entered at the time of set up.
the /etc/phpmyadmin/config-db.php file is shown below.

<?php
##
## database access settings in php format
## automatically generated from /etc/dbconfig-common/phpmyadmin.conf
## by /usr/sbin/dbconfig-generate-include
## Sun, 03 Jul 2011 10:19:02 +0530
##
## by default this file is managed via ucf, so you shouldn't have to
## worry about manual changes being silently discarded.  *however*,
## you'll probably also want to edit the configuration file mentioned
## above too.
##
$dbuser='user';
$dbpass='password';
$basepath='';
$dbname='phpmyadmin';
$dbserver='';
$dbport='';
$dbtype='mysql';

when i access [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) , the login screen appears but entering the username and password as in the file gives the error
#1405 cannot log into mysql server.
please help..

Is the database for phpmyadmin created?

Is the user created? Does the user have proper permissions? Is the password correct?

Is the MySQL server installed, properly configured? Listening on the default port? Bound to localhost?

That should give you some options to try, I am pretty sure it is one of those.

---

### Post by kiran_viswm on 2011-07-03
how to confirm whether we have to permission ?
mysql-server is installed. i reconfigured the phpmyadmin. how to re configure mysql?

---

### Post by kiran_viswm on 2011-07-03
sometimes i get the error....

"Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly."

please suggest what to do..

---


---
title: "Lost connection to MySQL"
date: 2007-03-06
forum: Server Platforms
---

### Post by superjaws on 2007-03-06
Recently restarted my server and a previously working php script now gives me the error:

```
Warning: mysql_connect() [function.mysql-connect]: Lost connection to MySQL server during query in /var/www/includes/getcss.inc.php on line 8
Lost connection to MySQL server during query
```

This is the script up to line 9:

[PHP]<?php
#database info, or include a config.php file
$db_host = '********'; #change to your host
$db_user = '*******'; #change to your user name
$db_password = '*******'; #change to your password
$db_name = '*************'; #change to your db name

mysql_connect($db_host,$db_user,$db_password) or die(mysql_error()); 
mysql_select_db($db_name) or die(mysql_error()); [/PHP]

---

### Post by invalid on 2007-03-06
Are you able to have a working mysql session using any other method (ie. mysql via terminal)?

---

### Post by superjaws on 2007-03-06
yes i can ssh into my server and then run mysql and run queries.

---

### Post by conjur3r on 2007-03-07
Do you have phpmyadmin or any other php applications which works off a mysql database to check?  We're just trying to isolate the problem to see if it is only that script or it affects all.

---

### Post by superjaws on 2007-03-07
PHPMyAdmin is working. An error in my scripts doesn't make sense because my scripts worked before i reset my server. Is there something that I may have changed in the MySQL settings that may have changed the way I'm supposed to access it that took effect when I reset the server?  In my scripts I am currently using 127.0.0.1 for the variable $db_host and root for $db_user and I know I'm using the correct password cause I just used it to access MySQL in the terminal.

---

### Post by superjaws on 2007-03-07
:) i changed the bind-host in the config file and that was the first time i had restarted since then. oops sorry to bother ya'll

---


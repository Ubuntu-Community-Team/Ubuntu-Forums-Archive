---
title: "DB.php file using PEAR with PHP5"
date: 2008-09-20
forum: Server Platforms
---

### Post by kmeth187 on 2008-09-20
**I am running apache2 and php5 on ubuntu. I installed the PEAR module for php using the synaptic packet manager. When trying to connect to mySQL with php I put the following code:** 

[I]include('db_login.php');
require_once('DB.php');
$connection = DB::connect("mysql://$db_username:$db_password@$db_host/$db_database");[/I]

**when I try to load the page in a browser I get the following error:**

Warning: include(db_login.php) [function.include]: failed to open stream: No such file or directory in /var/www/search.php on line 3

Warning: include() [function.include]: Failed opening 'db_login.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/search.php on line 3

Warning: require_once(DB.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/search.php on line 4

Fatal error: require_once() [function.require]: Failed opening required 'DB.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/search.php on line 4

Were is the DB.php file located and were should it be installed by default. If anyone knows I would appreciate some help thanks alot.

---

### Post by axis43 on 2008-10-06
DB.php is located in /usr/share/php

hope this helps

---


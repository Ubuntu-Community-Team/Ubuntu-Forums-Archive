---
title: "PHPBB3 Database Question"
date: 2008-05-18
forum: The Cafe
---

### Post by Black Mage on 2008-05-18
For PHPBB3, if I move the database to another location, how do I change that in PHPBB3 so it then goes to that database?

---

### Post by az on 2008-05-18
You edit config.php

You change the following variables to whatever you need:

$dbms = 'mysql';

$dbhost = 'localhost';
$dbname = 'database_name';
$dbuser = 'database_username';
$dbpasswd = 'database_password';

If your database is no longer being hosted on the same machine, then you would change dhhost to the name of the new host...

---

### Post by Black Mage on 2008-05-18
Thanks, that was easy.

---


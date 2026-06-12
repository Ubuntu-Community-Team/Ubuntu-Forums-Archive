---
title: "Cronjob to repair &amp; optimize database?"
date: 2009-03-16
forum: Server Platforms
---

### Post by wattaman on 2009-03-16
Hi!
_I'm looking for a cronjob to repair and optimize one particular mysql database_

I have a database that once a few days locks 2 tables and until now I was repairing them in phpmyadmin, but I suppose a croonjob that does this every morning will be better.
Please mind that I don't want to optimize ALL databases, I already found this cron command googleing... I just can't find the cron for only one database :(
Also, I don't fully understand the check, repair and optimize processes... if, for example, the repair also optimizes the database tables (or otherwise), please tell me, is good to know.
Thank you!

---

### Post by wattaman on 2009-03-17
Bump

---

### Post by wattaman on 2009-03-23
Bump again
Please let me know if it isn't possible so I'll delete this?
Thx

---

### Post by wattaman on 2009-03-26
Well, I insist :)
Anyway, I've found a script that optimizes all teh databases which belongs to one particular user. Is better then nothing, but hopefully some of you might be able to modify it and optimize only one database.
Here it is:
> #!/usr/bin/php
<?php
$server = "localhost";
$user = "mysql-user";
$pwd = "password";
 
$link = mysql_connect($server, $user, $pwd);
if (!$link) {
  die('Could not connect: ' . mysql_error());
}
 
$q= mysql_query("SHOW DATABASES") or die(mysql_error());
 while ($dbName = mysql_fetch_array($q)) {
   if ($dbName[0] != "information_schema") {
     echo " + Selecting " . $dbName[0] . "\n";
     $db_selected = mysql_select_db($dbName[0], $link);
        if (!$db_selected) {
        die ('Can\'t use $dbName[0] : ' . mysql_error());
     }
 
     $alltables = mysql_query("SHOW TABLES") or die(mysql_error());
 
     while ($tableName = mysql_fetch_array($alltables)) {
        echo "   - Optimizing " . $tableName[0] . "\n";
        mysql_query("OPTIMIZE TABLE `".$tableName[0]."`") or die(mysql_error());
     }
   } else {
      echo " + Skipping " . $dbName[0] . "\n";
   }
}
 
mysql_close($link);
 
?>
- and here's my curent hero: [kirya.net]("http://www.kirya.net/tips/optimize-mysql-tables/")
Again, _please_, if you know how to do it, modify this so it will optimize only one database, not all.
Thank you!

---


---
title: "[MySQL] Where to create a new Table"
date: 2011-07-13
forum: Server Platforms
---

### Post by ki4jgt on 2011-07-13
I've started a webserver at 127.0.0.1:**** I want to be able to use a database for this server. Which schema do I use to add a new table to? Do I create a new Schema altogether?

---

### Post by Bachstelze on 2011-07-13
Yes, you should create a new schema (i.e. a new database) and create your table in it. It is also a good idea to create a new user who will only have access to this database, and use that user instead of root. With phpMyAdmin, when you create a user, you have the option of also creating a new database with the same name and grant the user all privileges to it.

---

### Post by brighty22 on 2011-07-13
If you go down the phpMyAdmin route, be sure to set up the phpmyadmin database and user, so you can save settings etc. It normally screams at you until they are in place.

---

### Post by ki4jgt on 2011-07-14
I have a new problem
```

<?php
//opens connection to MySQL Server
$dbc = mysql_connect("127.0.0.1", "user", "password")
if (!$dbc) {
	die("Site Error");
	}
//Selects DB
$dbs = mysql_select_db("game", "$dbc")
if (!$dbs)
{
	die("MySQL ERROR);
}
?>

```

returns the page is unavailable. Furthermore, how would I select a specific schemata that the table is under?

---

### Post by brighty22 on 2011-07-14
I can see 2 semicolons missing. Use Dreamweaver or an alternate IDE with syntax checking. Also make sure you have the php5-mysql package, and that php error reporting set to -1 for development - php itself can warn you about parse errors. You 'select' a table in MySQL queries themselves. I'd suggest reading the w3 schools pages on MySQL from the beginning.

---

### Post by brighty22 on 2011-07-14
Try this:

[PHP]
<?php
//show all errors
error_reporting(-1);

//create mysql connection
$dbc = mysql_connect('127.0.0.1', 'user', 'password') or die('Connection error.');

//select database
$dbs = mysql_select_db('game', $dbc) or die('Database does not exist.');

//run queries.....
?>[/PHP]

Use single quotes (*'* not *"*) when you do not need to parse the contents of the string - it's quicker to execute. Read [this]("http://php.net/manual/en/language.types.string.php").

---


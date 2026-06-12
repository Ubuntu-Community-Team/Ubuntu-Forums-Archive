---
title: "php myadmin script error"
date: 2007-12-06
forum: Server Platforms
---

### Post by J@mes on 2007-12-06
I'm using the apaches friends and having a problem with my PHP script (i'm using php myadmin) 

the error message: 

Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'James'@'localhost' (using password: NO) in C:\xampp\htdocs\phpstuff\checklogin.php on line 10
cannot connect

this is the code i'm am using to create a login page

<?php
ob_start();
$host="localhost"; // Host name
$username="James"; // Mysql username
$password=""; // Mysql password
$db_name="test"; // Database name
$tbl_name="members"; // Table name

// Connect to server and select databse.
**mysql_connect("$host", "$username", "$password")or die("cannot connect");**
mysql_select_db("$db_name")or die("cannot select DB");

(I have place line 10 in bold)

How can i resolve this?

---


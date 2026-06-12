---
title: "Apache2 PHP5, cannot connect to multiple databases."
date: 2012-03-01
forum: Server Platforms
---

### Post by the1joker on 2012-03-01
Hello,
I run a webserver and im trying to use multiple DB connections but somehow it wont accept the prior connection, it automatically drops it and you can't use the connection.
 
I tried old style and PHP5 style, both with the same result, which makes me think its a server setting, this same code does work on my hosting providers server.
 
Here's my PHP code:
$db1 = mysql_connect("localhost", "root", "***") or die('Error connecting to mysql');
$db2 = mysql_connect("localhost", "root", "***") or die('Error connecting to mysql');
mysql_select_db("hpm", $db1); 
mysql_select_db("hunique", $db2); 
 
 
OR
 
try {   
 $db1 = new PDO('mysql:dbname=hunique;host=127.0.0.1', 'root', '***');   
 $db2 = new PDO('mysql:dbname=hpm;host=127.0.0.1', 'root', '***'); 
} 
catch (PDOException $ex) {   
 echo 'Connection failed: ' . $ex->getMessage(); 
} 

 
 
Oh and i don't get any connection errors only flag errors from php from the queries that are trying to connect to the $db1 cconnection

---

### Post by Azdour on 2012-03-01
Hi,

You might need to set the fourth parameter in mysql_connect to true, see:

[http://uk3.php.net/mysql_connect](http://uk3.php.net/mysql_connect)

---

### Post by the1joker on 2012-03-02
Okay thx, i think that should do it!!

---


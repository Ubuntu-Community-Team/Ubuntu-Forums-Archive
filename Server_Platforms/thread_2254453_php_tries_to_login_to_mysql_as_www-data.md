---
title: "php tries to login to mysql as www-data"
date: 2014-11-27
forum: Server Platforms
---

### Post by ubupaul2 on 2014-11-27
Running server 14.04.1 lamp. Seems that php tries to use the www-data  user to log in to mysql. To me it seems really strange because the same  webpage runs other scripts that fetch data fine from the same  database with the login details from dbconnect.php. Maybe i am missing  something simple? 

This is the error log:
```
[Wed Nov 26 22:37:01.603116 2014] [:error] [pid 1396] [client 192.168.2.141:49265] PHP Warning:  mysql_real_escape_string(): Access denied for user  'www-data'@'localhost' (using password: NO) in  /var/www/page/php/addclan.php on line 16, referer:  [https://192.168.2.131/index.php/clans](https://192.168.2.131/index.php/clans)
[Wed Nov 26 22:37:01.603151 2014] [:error] [pid 1396] [client 192.168.2.141:49265] PHP Warning:  mysql_real_escape_string(): A link to the server could not be  established in /var/www/page/php/addclan.php on line 16, referer:  [https://192.168.2.131/index.php/clans](https://192.168.2.131/index.php/clans)

```

This is the addclan.php script that give the error:
```
<?php
//#Include the connect.php file
include('../../php/dbconnect.php');

//connect to db
$conn = mysqli_connect($hostname, $username, $password, $database);

// Check connection
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

//if insert key is pressed then do insertion
if($_POST['action'] == 'insert'){

    $name  = mysql_real_escape_string($_POST['name']);

    $sql   = "insert into db.clans (name) values ('$name')";
    $result = $conn->query($sql);

    if($result){
        echo "Clan added!";
    }
    else {
        echo "Clan could not be added!";
    }
}
?>
```

---

### Post by Lars Noodén on 2014-11-27
What is the actual value of $username in this line?

```

$conn = mysqli_connect($hostname, $username, $password, $database);

```

Try inserting a print statement on the line before to see for sure.

---

### Post by ubupaul2 on 2014-11-27
Changing the line to

```
$conn = mysqli_connect("localhost", "user", "mypassword", "db");
```

gives the same result. Login attempt by www-data denied.

Might be worth mentioning that a record actually gets added to the db table, but only with null values (happens in both cases).

---

### Post by ubupaul2 on 2014-11-27
Actually the script does connect. Tried typing a value directly instead  of the $name in the sql statement, and it got inserted. Must be an issue  with the javascript calling addclan.php. Still does not explain the  www-data login attempt (still happens), but pretty sure i can get the script to fill  data in the db.

---


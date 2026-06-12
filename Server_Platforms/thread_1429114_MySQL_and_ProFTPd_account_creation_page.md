---
title: "MySQL and ProFTPd account creation page?"
date: 2010-03-13
forum: Server Platforms
---

### Post by ipng on 2010-03-13
Hello :KS

Right now i am running ProFTPd, which is integrated with MySQL. I can edit my ProFTPd users in PhpMyAdmin (via MySQL), but i was wondering, if i could make an account creation page?
This is also a question of coding HTML and/or PHP, but that's not a problem, as long as w3schools.com and my HTML/PHP editor is still working ;)

Thanks in advance :D

---

### Post by Xeora on 2010-08-10
yes, you could do it, here's a rough outline of the need to happens.

in PHP you'll have to connect to your MySQL Database (several ways to do it, I use the oldest way)

If you want you can have this as a seperate file or in the page itself, just depends your style and needs.
```

<?php
//Connect to MySQL DB
  $LOCATION = "localhost"; //if your connecting to the box the WebServer runs on
  $USER = "root" //change this to your settings
  $PASSWORD = "password" //ditto
  $DBNAME = "ftp" //inital DB you want to connect to, feel free to change

  $link = mysql_connect("$LOCATION","$USER","$PASSWORD");
  if(!$link){
    die('Could not connect: '.mysql_error());
  }
  mysql_selectdb("$DBNAME");
?>

```

Then you need something like the following in another - or same PHP page

```

<?php
if(!empty($_POST['username'])){
 if(strcmp($_POST['password'],$_POST['conPW']) == 0){
  //do the adding of the user to the mysql DB... I'll leave that part to you... few extra line :P
 } else {
  echo "Passwords do not Match";
 }
}
?>

<form method="post" action="<?php echo $_SERVER['PHP_SELF']; ?>">
 <label>Username: </label><input type="text" name="username" />
 <label>Password: </label><input type="password" name="password" />
 <label>Confirm PW: </label><input type="password" name="conPW" />
</form>

```

---


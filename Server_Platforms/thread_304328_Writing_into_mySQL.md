---
title: "Writing into mySQL"
date: 2006-11-21
forum: Server Platforms
---

### Post by Jozef on 2006-11-21
I've been running the desktop version of Ubuntu 6.06 for a while, including a basic server I used primarily for file storage, and currently I'm in the process of setting up mySQL 5 and PHP 5.

When testing, I was able to access mySQL via phpMyAdmin and create a test table and populate it.  Over the Internet, I'm able to use PHP scripts to read from the tables without a problem, but I'm not able to use a PHP script to write into the tables.

I tested the scripts I used on my hosted server (set up by people much smarter than me), without a problem.  Given that I can read from the database and write into it using phpMyAdmin, I don't have the faintest idea where to start looking to enable writing into the database from my www folder.  Any help would be greatly appreciated.

---

### Post by adamkane on 2006-11-21
Sounds like a user/permissions issue.

I learned about proper permissions by installing open-source CMS like osCommerce, which guides you through the process.
[http://www.opensourcecms.com/](http://www.opensourcecms.com/)

You probably need to add a user:group called apache:apache, and you need enable read/write/execute access for that user.

---

### Post by tturrisi on 2006-11-21
1. run phpmyadmin
2. click on Privledges
3. add a user w/ the name & password used in this part of your scripts:
```
// db connection info

$username="username"; 

$password="password"; 

$database="name-of-database";



//database connect error message

$db_error= "Unable to connect to database. Please report the exact time, place, form & event, including the actions you undertook that resulted in this error.";



// connect to db

mysql_connect(localhost,$username,$password); 

@mysql_select_db($database) or die( $db_error);
```
4. then grant desired privledges to that user for that database

What sql message is displayed on the browser when trying to execute a script that tries to write to the database (INSERT INTO table VALUES foo)?

---

### Post by Jozef on 2006-11-21
Many thanks for the tips.

Adamkane: Thanks; I also considered this to be a permissions issue.  I'll check the site out.  One thing that's confounding me is that when I added full permissions to everyone I was able to read from the database (actually, chmopd 755 was enough for that), but not write into the database.

tturrisi: I did that, and it connects successfully to the database.  I'm able to pull data from the database without a problem.  In fact, it's beginning to look like a PHP problem.  I did some additional testing and found that I can't retain any variables I created.  For example, I created a simple form with only one text field and instructed it to load another page where the contents of the field would be displayed.  The next page came out empty.  For this reason, I was able to insert new rows in a table after I removed the usual "if(submit){ }" part, but the rows had all fields empty.

---

### Post by adamkane on 2006-11-22
Starting from scratch, I always come across this kind of issue. Even if you don't want to install a CMS, there may also be some smaller projects with example connect and write pages that you can copy.

Sorry for not being very helpful.

---

### Post by tturrisi on 2006-11-22
> **Jozef said:**
> 
tturrisi: I did that, and it connects successfully to the database.  I'm able to pull data from the database without a problem.  In fact, it's beginning to look like a PHP problem.  I did some additional testing and found that I can't retain any variables I created.  For example, I created a simple form with only one text field and instructed it to load another page where the contents of the field would be displayed.  The next page came out empty.  For this reason, I was able to insert new rows in a table after I removed the usual "if(submit){ }" part, but the rows had all fields empty.
post a script that "doesn't work". (w/out username & passwords)

---

### Post by Jozef on 2006-11-22
Page named "test1.php":

```
<html>
<head>
</head>

<body>

  <form method="post" action="test2.php">
  <table border="1" valign="top" align="left">
  	<tr><td>First:</td><td><input type="text" name="first"></td></tr>
	<tr><td>Last:</td><td><input type="text" name="last"></td></tr>
	<tr><td colspan="2"><input type="submit" name="submit" value="submit"></td></tr>
	</table>
	</form>

</body>

</html>
```

Page named test2.php, which appears after filling out the form and clicking on "submit":

```
<html>
<head></head>

<body>

<?php

print("$first, $last");

include("db.php");

$sql= "INSERT INTO test (first,last) VALUES ('$first','$last')";

  $result = mysql_query($sql);

  print("Thank you, information entered.<p>");


?>

</body>
```

The output I get is a new line in the table with all fields empty, and in the browser I get 
>  , Thank you, information entered.
(Note the comma at the beginning - it should be between the text of the two fields I entered, which didn't display.  Also, the login to the database is in db.php.  That part works fine; I'm able to use the same file to pull data from the table.)

---

### Post by tturrisi on 2006-11-22
Tryb this.  It will work IF your test database is setup properly:
(for some reason the code function here butchers code & adds empty lines)
```
<?php
if ($_POST['submit'] == TRUE) { //if submit button pressed
$first= $_POST['first'];

$last= $_POST['last'];
// connect to db
include ("db.php");
// insert data into db
$query = "INSERT INTO test (first,last) VALUES ('$first','$last)";

mysql_query($query);
// display last db entry
$query = "SELECT * FROM test ORDER BY last DESC LIMIT 1";

$result = mysql_query($query);

mysql_close();
while($r=mysql_fetch_array($result))

{
echo "$r[first]&nbsp;$r[last]<br>\n";
echo "was inserted into the test database.";
} //end while

} //end if submit true
else { //display the form
?>
<html>
<head>
</head>
<body>
<form method="post" action="test2.php">
<table border="1" valign="top" align="left">
<tr><td>First:</td><td><input type="text" name="first" value=""></td></tr>
<tr><td>Last:</td><td><input type="text" name="last" value=""></td></tr>
<tr><td colspan="2"><input type="submit" name="submit" value="submit"></td></tr>
</table>
</form>
</body>
</html>
<?php 
} //end else
?>

```

---


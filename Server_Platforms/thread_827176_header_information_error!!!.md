---
title: "header information error!!!"
date: 2008-06-12
forum: Server Platforms
---

### Post by shotos on 2008-06-12
Hi 
i am trying to login to my database with a php script but i keep getting this error message.

[COLOR="DarkRed"]Warning: Cannot modify header information - headers already sent by (output started at /home/kwasi/public_html/login.php:4) in /home/kwasi/public_html/login.php on line 22[/COLOR]

below is the script........help will be appreciated
[php]
<html>

<body>
<?php
include("database.php");

$username = $_POST['username'];
$password = $_POST['password'];

if($username == ''){ unset($username); echo "No username submitted<br>";}
if($password == ''){ unset($password); echo "No password entered<br>";}

if (isset($username) && isset($password))
{
$ret = confirmUser($username, $password);
if(!$ret){
echo"Wrong username or password<br>";}

else{
/*session_register("username");
session_register("password");*/
header("location: login_success.php");}
} else
{
 header("location: login.html");
} 

function confirmUser($username, $password){
global $link;
$username = trim($username);
$password = trim($password);
$username = htmlspecialchars($username);
$password = htmlspecialchars($password);
$username = stripslashes($username);
$password = stripslashes($password);
$username = mysql_real_escape_string($username);
$password = mysql_real_escape_string($password);

$query = "select * from users where username='$username' and password='$password'"; 
$result = mysql_query($query, $link);
$count = mysql_num_rows($result);

if($count==1){
return true;}

else{
return false; }
}
?>
</body>
</html>
[/php]

---

### Post by molotov00 on 2008-06-12
header("location: login_success.php");}

needs to be BEFORE any output.

The VERY FIRST character of your script should be <? blah blah php here...

Right now you are sending <html> and other tags first.

Just move these lines below the header functions:
```
<html>

<body>
```

Alternatively, you could learn about output buffers, but that's beyond what i'm willing to explain here. Just Google "php output buffer".

Btw, this is not Ubuntu related. It's a classic error made by PHP beginners.

---

### Post by shotos on 2008-06-13
this is how i updated the code after learning abt output bufferring but
the function ob_start() and ob_flush() are inactive. any form of help is welcomed.

[php]
<?php
ob_start();// enabling output bufferring
include("database.php");//including the database connection
//verifying if inputs were supplied
$username = $_POST['username'];
$password = $_POST['password'];

if($username == ''){ unset($username); echo "No username submitted<br>";}
if($password == ''){ unset($password); echo "No password entered<br>";}

if (isset($username) && isset($password))
{
$ret = confirmUser($username, $password);
if(!$ret){
echo"Wrong username or password<br>";
//header("location: login.html");}//redirecting page
}
else{
echo "Login Successful.<a href=login_success.php>Click here to
continue</a>";
//header("location: login_success.php");
}
} else
{
 header("location: login.html");
} 

function confirmUser($username, $password){
global $link;
//checking user inputs
$username = trim($username);
$password = trim($password);
$username = htmlspecialchars($username);
$password = htmlspecialchars($password);
$username = stripslashes($username);
$password = stripslashes($password);
$username = mysql_real_escape_string($username);
$password = mysql_real_escape_string($password);

//selecting table and confirming username and password
$query = "select * from users where username='$username' and password='$password'"; 
$result = mysql_query($query, $link);
$count = mysql_num_rows($result);//real validation with rows affected by query

if($count==1){
return true;}

else{
return false; }
}
ob_flush();//outputting the data in the buffer as heading
?>
<html>
<body>
</body>
</html>
[/php]

---


---
title: "[SOLVED] Can't connect to MYSQL Database"
date: 2008-06-19
forum: Server Platforms
---

### Post by Nodestar on 2008-06-19
I'm running Hardy Heron Desktop, Apache 2, PHP 5, MYSQL 5, PHPMyAdmin 2, all in a local testing environment.
I'm having my first go around with MYSQL and PHPMyAdmin. I can log into and access PHPMyAdmin fine. Both with Root and my own user name "justin". 
My problem arises when I try and open a simple web page to access the Database and show me a table within it. It's not a practical application I'm just trying to learn and get it to work.
The table within the Database holds images. It was created in PHPMYADMIN.
Here is the code for the web page.

```
<?php

include('../includes/conn_mysqli.inc.php');

// connect to MySQL

$conn = dbConnect('query');

// prepare the SQL query

$sql = 'SELECT * FROM images';

// submit the query and capture the result

$result = $conn->query($sql) or die(mysqli_error($conn));

// find out how many records were retrieved

$numRows = $result->num_rows;

?>

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml">

<head>

<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />

<title>Connecting with MySQLI extension</title>

</head>



<body>

<p>A total of <?php echo $numRows; ?> records were found.</p>

</body>

</html>
```

I'm having an access denied problem when I try and view the page in a browser.
Here are my error messages.

```
Warning: mysqli::mysqli() [function.mysqli-mysqli]: (28000/1045): Access denied for user 'justin'@'localhost' (using password: NO) in /home/justin/public_html/domain2.com/public/includes/conn_mysqli.inc.php on line 4

Warning: mysqli::query() [function.mysqli-query]: Couldn't fetch mysqli in /home/justin/public_html/domain2.com/public/mysql/mysql.php on line 8

Warning: mysqli_error() [function.mysqli-error]: Couldn't fetch mysqli in /home/justin/public_html/domain2.com/public/mysql/mysql.php on line 8

```

The main problem seems to be here. 
"(28000/1045): Access denied for user 'justin'@'localhost' (using password: NO)"
I'm new to PHP and MYSQL so I don't know what this problem is or how to go about fixing it. It might just be that I haven't given a Password. But I don't know where I would type one in. 

Any help would be great. I just don't have the experience to go any further. Nothing I tinker with seems to work.

---

### Post by mbeach on 2008-06-21
I'd suggest looking in the include file
conn_mysqli.inc.php
which likely has the credentials for username and password, with the password not set to anything.

---

### Post by windependence on 2008-06-21
Also, you will have to grant access to the user for the tables you want to access. I am no SQL expert by far, but to me it sounds like a permissions issue within MySQL.

-Tim

---

### Post by Barriehie on 2008-06-21
I'm running phpmyadmin 2.10.3 and once logged in see if you have a privelages link on the home page.  This will be the privelages that phpmyadmin loads from the mysql privelage table.  This might be a place to start.

Barrie

---

### Post by smo0th on 2008-06-21
make sure the user/password inside conn_mysqli.inc.php matches with your mysql user account, also use phpmyadmin to make sure the user you are logging has enough priviledges, this is done by browsing the 'Priviledges' page on your home phpmyadmin page, there should be something like:
```

<?php
$link = mysql_connect('localhost', 'mysql_user', 'mysql_password');
if (!$link) {
    die('Could not connect: ' . mysql_error());
}
echo 'Connected successfully';
mysql_close($link);
?>

```
(real basic example) inside your conn_mysqli.inc.php, make sure you put a valid user/password there, it this doesn't work post back.

---

### Post by Nodestar on 2008-06-21
OK. No luck so far. But heres some more info.
Within conn_mysqli.inc.php

```
<?php
function dbConnect($type) {

  $conn = new mysqli('localhost', $user, $pwd, 'phpsolutions') or die ('Cannot open database');
  return $conn;
}
?>
```

And within PHPMyAdmin. 
I log in.
Click on the Database I'm using.
Click on the "Privileges" tab.
Which brings up a table titled "Users having access to "Database"

My user. Which is justin is set up like this.

User = justin
Host = localhost
Type = global , database-specific
Privileges = All Privileges , All Privileges
Grant = Yes , Yes

Thats the way I had is set up earlier. I've tried changing some stuff around to no avail. Still looking for possible solutions. I'm sure it's something simple but just can't pin it down.

---

### Post by Nodestar on 2008-06-21
Ok. It's working. I didn't relize $user and $pwd were placeholders. I replaced them with my user name and password and it worked as it should. Thanks for all the help. Really appriate it. Never would of figured it out on my own.

---

### Post by smo0th on 2008-06-21
you need to check for your variables, this is an example on how the variables relate to your connection method(mysqli)
```

//variables
$server = 'localhost';
$login = 'user';
$password = 'yourpass';
$database = 'members';

//access
$connection = new mysqli($server, $login, $password, $database);

```
conn_mysqli.inc.php is being called from other php script, check for that script and look for $user and $pwd variables, which should be declared as global variables somewhere, or you could directly write them in your conn_mysqli.inc.php

---

### Post by smo0th on 2008-06-21
yay, good work, keep it up =)

---

### Post by Nodestar on 2008-06-21
Ok. I understand. I wrote them directly into conn_mysqli.inc.php for now. I'm guessing thats probably not good programming practice. I'm also guessing the variables are declared or can be declared or captured with a login form field? I'll look more into this as I'm learning more about PHP. Thanks again for the help getting it to work.

I'm looking for a way to edit the title of this thread with a [solved]. Can't seem to figure it out.

---

### Post by mbeach on 2008-06-21
[EDIT - I've become too slow a typer, you've got the answer already]

the "$pwd" is being set somewhere, likely a cfg file of some sort or somewhere in that same file..  You might try hard wiring the username and password in the file like:
```
$conn = new mysqli('localhost', 'justin', 'justinsMySQLPassword', 'phpsolutions') or die ('Cannot open database');
```

Its been awhile for me with php, but it looks like its using some global variables there in that function which are/should be set prior to that function being called.  If it works with the values typed directly into that mysqli call, find where they are supposed to be set and go from there.

---

### Post by Nodestar on 2008-06-21
Thanks for the info. I guess I need to make a login page to capture a session because the variables arn't being declared or included at all in my dummy site that calls the conn_mysqli.inc.php page. Now that it's working I can start to figure it all out.

---

### Post by smo0th on 2008-06-21
I don't remember it very well but my wild guess is that there's an option under 'Thread tools' to mark it as solved =)

about the $user and $pwd variables, there's a main script under your whole application which initiates all the variables and there you shall see $user and $pwd variables declared as global, you declare global variables so you can use them with all your functions, conn_mysqli.inc.php creates a dbConnect function 
```
<?php
function dbConnect($type) {

  $conn = new mysqli('localhost', $user, $pwd, 'phpsolutions') or die ('Cannot open database');
  return $conn;
}
?>
```
where $type is being supplied from the parent script and $user and $pwd must be global variables in that parent script, it is recommended that you look for that parent script and modify $user and $pwd variables there, there's a good chance you find them inside a config.php file somewhere.

---

### Post by Nodestar on 2008-06-21
I found this. Labeled connect.php

```
<?php
$hostname = 'localhost';
$select = 'psquery';
$admin = 'psadmin';
$selectPwd = 'fuji';
$adminPwd = 'kyoto';
?>
```

No $type or $user or $pwd.
I tried replacing some of the values with my own user name and password. No luck.
I also tried declaring the $user and $pwd values inside this script. They didn't overide where ever else their being declared. Not sure where that is.


[EDIT]
Ok looks like their never declared outright but they originate in a script having to do with login and authentication. Looks like I need to look more into that area and set up some logins. I'll probably just keep them hard coded into the conn_msqli.inc.php until I master whats going on in the login scripts. 

Thanks again for all the help.

---

### Post by smo0th on 2008-06-21
well, it works by directly replacing the variables with your user data, so no big deal there, just keep them in mind if at some point you find them ;)

---

### Post by Nodestar on 2008-06-21
Thanks for all the help smoOth. I edited my last post right above your last post with my final findings. I should be good to go.

Thanks again for all your help.

---


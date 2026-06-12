---
title: "PHP form name not available as variable?"
date: 2005-12-26
forum: Server Platforms
---

### Post by dwessell on 2005-12-26
Hi all..

I've been developing remotely on a Linux server for awhile. But now have setup LAMP on my local machine to work on some php files. I have Apache 2 installed, and PHP 4.

The issue is on html forms.. When I submit, and proceed to the next page. The form inputs are not available as variables to php, as they were on the remote server (Which I did not administrate).. Is there a setting in php that controls this?

Example below, $timezone would normally have been a variable on page2.php.

Thanks
David


<FORM METHOD="POST" ACTION="page2.php" NAME="form2">
<input type="radio" name="timezone" value="Eastern"> 
<INPUT TYPE="submit" name="submit1" value="Proceed">

---

### Post by mgor on 2005-12-26
the remote server had 
```
register_globals = On
```
in php.ini, this is not recommended as it's a security risk, that's way it's set as Off per default.

if you want to access the variable in your example you'll have to use $_POST, which is an array that contains all the variables in a POST query.
```
$_POST['timezone']
```

read up at
[http://www.php.net/register_globals](http://www.php.net/register_globals)
[http://www.php.net/reserved.variables](http://www.php.net/reserved.variables)

---


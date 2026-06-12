---
title: "Basic web-server security php login form"
date: 2007-10-08
forum: Server Platforms
---

### Post by kasperbs on 2007-10-08
I didn't really know how to title this post, but to clarify.

I have setup a small web-server running apache2. I have some applications installed like, webmin, jinzora, phpmyadmin, gallery2 etc.

all the apps are installed in the /var/www/ directory. Here I have got a lphp login form that looks like this:
```
<?php

// Add/remove username/password here.
// just replaces "USERNAME" with your desired username and do the same for "PASSWORD"
// You can add more users by adding a comma after the apostrophe after the password and adding a new line formated as the first
$LOGIN_INFORMATION = array(
  'username' => 'password'
);

define('USE_USERNAME', true);

define('LOGOUT_URL', '/');

define('TIMEOUT_MINUTES', 0);

define('TIMEOUT_CHECK_ACTIVITY', true);

if(isset($_GET['help'])) {
  die('Include following code into every page you would like to protect, at the very beginning (first line):<br>&lt;?php include("' . str_replace('\\','\\\\$
}


$timeout = (TIMEOUT_MINUTES == 0 ? 0 : time() + TIMEOUT_MINUTES * 60);


if(isset($_GET['logout'])) {
  setcookie("verify", '', $timeout, '/'); // clear password;
  header('Location: ' . LOGOUT_URL);
  exit();
}

if(!function_exists('showLoginPasswordProtect')) {

function showLoginPasswordProtect($error_msg) {
?>
<html>
<head>
  <title>Ubuntu Server Rudolf</title>
  <META HTTP-EQUIV="CACHE-CONTROL" CONTENT="NO-CACHE">
  <META HTTP-EQUIV="PRAGMA" CONTENT="NO-CACHE">
</head>
<body>
<center>
  <style>
    input { border: 1px solid black; }
  </style>
  <form method="post">
    <h3><font color="#242424">Enter password to access this page</font></h3>
    <font color="red"><?php echo $error_msg; ?></font><br />
<?php if (USE_USERNAME) echo '<font color="#242424">Username:</font><br /><input type="input" name="access_login" /><br /><font color="#242424">Password:</f$
    <input type="password" name="access_password" /><p></p><input type="submit" name="Submit" value="Submit" />
  </form>
  <br />
</center>
</body>
</html>

```
this file is included in my index.php file that is in the /var/www directory:
```
/var/www$ ls -lah
totalt 36K
drwxr-xr-x   5 root root 4,0K 2007-10-08 14:35 .
drwxr-xr-x  17 root root 4,0K 2007-10-07 20:28 ..
drwxr-xr-x   2 root root 4,0K 2007-10-06 13:06 apache2-default
lrwxrwxrwx   1 root root   19 2007-10-07 21:43 gallery2 -> /usr/share/gallery2
-rw-r--r--   1 root root 1,5K 2007-10-08 00:42 index.php
drwxrwxrwx  16 root root 4,0K 2007-10-07 17:49 jinzora2
-rw-r--r--   1 root root 2,9K 2007-10-06 13:25 password_protect.php
lrwxrwxrwx   1 root root   21 2007-10-06 13:24 phpmyadmin -> /usr/share/phpmyadmin
drwxr-xr-x 121 root bin   12K 2007-09-21 23:29 webmin-1.370

```
The login is fine apart from, when i for example go to [www.mywebsite.com/jinzora](www.mywebsite.com/jinzora) I'm allowed past the login even when I'm actually logged out.

Is there a way to make sure that everyone that come to [www.mywebsite.com](www.mywebsite.com) or any subdomains are forced to pass the password protection before being allowed into the site?

I have heard that .htaccess can do something like that?

---


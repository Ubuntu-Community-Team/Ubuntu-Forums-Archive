---
title: "Password Protecting Webserver"
date: 2006-11-30
forum: Server Platforms
---

### Post by mzracer360 on 2006-11-30
I would like to know how I can get a folder on my webserver password protected.  This way when you enter the URL with that folder into a web broswer (ex. "www.mywebsite.com/passsword/") it would prompt you for a username/password.

---

### Post by DWright on 2006-11-30
I assume you are using Apache, yes?
If so use a .htaccess file.
see: [http://httpd.apache.org/docs/1.3/howto/htaccess.html]("http://httpd.apache.org/docs/1.3/howto/htaccess.html")

---

### Post by tturrisi on 2006-12-01
htaccess works fine, but a php-mysql authentication script is more secure.  You can even use php-mysql combines w/ htaccess.

---

### Post by MJN on 2006-12-01
As far as I was aware htaccess/htpasswd is as secure as every other aspect of Apache - do you know otherwise? No point in using a sledgehammer to crack a nut.
 
(I'm not including sniffable passwords as a weakness as if this is of concern then htaccess with TLS and/or Digest Authentication would be used)
 
Mathew

---

### Post by tturrisi on 2006-12-01
[http://www.securityfocus.com/infocus/1368](http://www.securityfocus.com/infocus/1368)

---

### Post by MJN on 2006-12-01
And?

Nothing there describes a weakness in htaccess (aside from not using it with TLS as I already caveated), and certainly nothing that can't be sufficiently mitigated (that's the whole point of the article, although I suspect you haven't actually read it but rather just found it from a Google search... am I right or am I right? ;)).

If you're going to use weak passwords then that's your own fault - any brute force success is not a fundamental weakness of htaccess. The rest is purely DOS-based, a 'weakness' inherent in any form of client/server transactions.

htacess it the perfect solution to the OP's stated requirements so please don't cloud the issue and imply otherwise.

Mathew

---

### Post by chrisfay on 2006-12-01
> htacess it the perfect solution to the OP's stated requirements so please don't cloud the issue and imply otherwise.

Interesting, I would think it best to offer as many solutions as possible. A database 'auth' table would be extremely easy to impliment and is much more robust if you have the knowhow. I think its much safer to keep my users/passwords for even simple web auth forms in a database so there's no system access to a flat user file. Some simple PHP would do the trick:

First create a Mysql database (named whatever you want), a table called 'auth', a 'userid' field and a MD5 'password' field.

This would be the code to access the table and two fileds to retrieve the login info and move on into the web page.

```
<?php
  //MySql authentication created by Chris Fay 
// Enable output buffering (if sending headers further in file)
ob_start();

$servername = 'localhost';     //leave as localhost unless you use a remote db server
$mysqlusername = 'mysqlusername';       //enter the username to access your mysql database
$mysqlpasswd = 'seceret'; //enter the password to connect to your mysql database
$mysqldb = 'databasename';             //enter the name of the database you want to connect to


  //function for authentication
function authenticate_user() {
  header('WWW-Authenticate: Basic realm="Protected"');
  header("HTTP/1.0 401 Unauthorized");
  echo "<strong>You did not submit the correct credentials.</strong><br /> <a href=\"index.php\">Try again</a>";
  exit;
}

if (! isset($_SERVER['PHP_AUTH_USER'])) {
   authenticate_user();
} else {

  //connect to mysql database
  mysql_pconnect($servername,$mysqlusername,$mysqlpasswd)
  or die("Can't connect to databse server!");

  mysql_select_db($mysqldb)
  or die("Can't select database!");

  //Create and execute the selection query.
  $query = "SELECT userid, passwd FROM auth
   WHERE userid='$_SERVER[PHP_AUTH_USER]' AND
   passwd=MD5('$_SERVER[PHP_AUTH_PW]')";

  $result = mysql_query($query);
  // If nothing was found, reprompt the user for the login info
   if (mysql_num_rows($result) ==0) {
   authenticate_user();
  } else {

//Once authenticated with mysql, continue on into the web page

<!-- web page goes below -->



<!-- end web page -->

  }
}
?>

```
It takes a few more minutes than creating a .htaccess and .htpasswrd file but its worth it if you ever need anything a bit more manageable and secure.

---

### Post by tturrisi on 2006-12-01
> Interesting, I would think it best to offer as many solutions as possible
and that is exactly why I posted, thanks for the validation.

> although I suspect you haven't actually read it but rather just found it from a Google search... am I right or am I right? ).
Yes, I read the article prior to posting the link to it.
The original poster here did not state exactly what or why he wanted to do.  He stated that he wants to know how to password protect a www dir and make it accessable by entering a username & password into a form.  Thus, I gave alternatives to htaccess-htpasswd.  He may just follow ths thread and realize that htaccess is not suitable for naked pics of Rosey O'Donnel, or he may consider htaccess-htpasswd just fine for his private files.

As for the aticle, I consider it a major weakness when there exist many readily availabe security tools designed specifically to exploit htaccess.  It is much more difficult to crack a php-mysql secure login that uses md5.  I know of no utilities made to specifically crack that because php functions used and mysql tables and fields are not static things, they can differ from site to site, whereas apache is static, it's pretty much the same everywhere as to how apache-htaccess does what it does (the only real difference being the location of the htpasswd files on the servers).

The other weakness of htaccess is it can be used to crash a server or in dos attacks.

---

### Post by MJN on 2006-12-02
> **chrisfay said:**
> Interesting, I would think it best to offer as many solutions as possible.

Agreed, although when alternatives are offered with the supporting statement that they're 'more secure' this should be backed up and qualified otherwise it can imply that the 'less secure' method is insufficient.

I'm still not convinced that htaccess is insufficient in the general case, however I'm not going to die in a ditch about it!

Mathew

---

### Post by tturrisi on 2006-12-02
> **MJN said:**
> I'm still not convinced that htaccess is insufficient in the general case, however I'm not going to die in a ditch about it!
Mathew
I don't believe anyone has disputed that, I certainly didn't, and I agree w/ you that in general cases, htaccess is more than sufficient, certainly better than javascript authorization and other client side authorization methods, and certainly secure enough for the average home server.  I believe we do see eye to eye here.  Let's steer clear of the ditches!

---

### Post by MJN on 2006-12-02
Okay, perhaps I misunderstood what you were implying... :)

Mathew

---


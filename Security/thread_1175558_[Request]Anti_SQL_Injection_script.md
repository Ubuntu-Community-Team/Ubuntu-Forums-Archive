---
title: "[Request]Anti SQL Injection script"
date: 2009-06-01
forum: Security
---

### Post by kenweill on 2009-06-01
requesting for an anti-sql injection script that can be used both on windows(php and mssql) and in linux (php and mysql).

using xampp.

i have been told that anti sql scripts are inserted in the file config.php since all php request pass thru config.php

but, how do i secure this config.php? i've been using different anti sql scripts but still the same, getting hacked thru sql injection.

database wipe out, sql server shutdown. i encountered both.

currently, this is the contents of my config.php(under windows)

```

<?php

$ip = $_SERVER['REMOTE_ADDR'];
$time = date("l dS of F Y h:i:s A");
$script = $_SERVER[PATH_TRANSLATED];
$fp = fopen ("D:/RANSERVER/[WEB]SQL_Injection.txt", "a+");

$sql_inject_1 = array(";","'","%",'"'); #Whoth need replace
$sql_inject_2 = array("", "","","&quot;"); #To wont replace
$GET_KEY = array_keys($_GET); #array keys from $_GET
$POST_KEY = array_keys($_POST); #array keys from $_POST
$COOKIE_KEY = array_keys($_COOKIE); #array keys from $_COOKIE
/*begin clear $_GET */
for($i=0;$i<count($GET_KEY);$i++)
{
$real_get[$i] = $_GET[$GET_KEY[$i]];
$_GET[$GET_KEY[$i]] = str_replace($sql_inject_1, $sql_inject_2, HtmlSpecialChars($_GET[$GET_KEY[$i]]));
  if($real_get[$i] != $_GET[$GET_KEY[$i]])
  {
  fwrite ($fp, "IP: $ip\r\n");
  fwrite ($fp, "Method: GET\r\n");
  fwrite ($fp, "Value: $real_get[$i]\r\n");
  fwrite ($fp, "Script: $script\r\n");
  fwrite ($fp, "Time: $time\r\n");
  fwrite ($fp, "==================================\r\n");
  }
}
/*end clear $_GET */
/*begin clear $_POST */
for($i=0;$i<count($POST_KEY);$i++)
{
$real_post[$i] = $_POST[$POST_KEY[$i]];
$_POST[$POST_KEY[$i]] = str_replace($sql_inject_1, $sql_inject_2, HtmlSpecialChars($_POST[$POST_KEY[$i]]));
  if($real_post[$i] != $_POST[$POST_KEY[$i]])
  {
  fwrite ($fp, "IP: $ip\r\n");
  fwrite ($fp, "Method: POST\r\n");
  fwrite ($fp, "Value: $real_post[$i]\r\n");
  fwrite ($fp, "Script: $script\r\n");
  fwrite ($fp, "Time: $time\r\n");
  fwrite ($fp, "==================================\r\n");
  }
}
/*end clear $_POST */
/*begin clear $_COOKIE */
for($i=0;$i<count($COOKIE_KEY);$i++)
{
$real_cookie[$i] = $_COOKIE[$COOKIE_KEY[$i]];
$_COOKIE[$COOKIE_KEY[$i]] = str_replace($sql_inject_1, $sql_inject_2, HtmlSpecialChars($_COOKIE[$COOKIE_KEY[$i]]));
  if($real_cookie[$i] != $_COOKIE[$COOKIE_KEY[$i]])
  {
  fwrite ($fp, "IP: $ip\r\n");
  fwrite ($fp, "Method: COOKIE\r\n");
  fwrite ($fp, "Value: $real_cookie[$i]\r\n");
  fwrite ($fp, "Script: $script\r\n");
  fwrite ($fp, "Time: $time\r\n");
  fwrite ($fp, "==================================\r\n");
  }
}

/*end clear $_COOKIE */
fclose ($fp);

$CONFIG['servername'] = "MOdified";	//Web Name
$CONFIG['dbaddress'] = "Modified\SQLEXPRESS";		//DB IP
$CONFIG['dbuser'] = "*************";		//DB ID
$CONFIG['dbpass'] = "********************";		//DB PASS
$CONFIG['dbdbname'] = "RanUser";
$CONFIG['dbdbname1'] = "RanGame1";
$CONFIG['dbdbname2'] = "RanShop";
$CONFIG['registration'] = "1";
$CONFIG['maxaccounts'] = "0";
$CONFIG['maxemail'] = "1";
$CONFIG['email'] = "0";
$CONFIG['emailaddress'] = "";
$CONFIG['emailsmtp'] = "";
$CONFIG['emailuser'] = "";
$CONFIG['emailpass'] = "";
?>


```

others using this script also reported they're getting injected. same as mine, database wipeout, then sql server shutdown.

Need an improved anti sql injection script. or another way to avoid sql injection.

---

### Post by Barry Carroll on 2009-06-02
You should have a look at using prepared statements as they'll do the hard work for you.

[http://dev.mysql.com/tech-resources/articles/4.1/prepared-statements.html](http://dev.mysql.com/tech-resources/articles/4.1/prepared-statements.html)

---

### Post by bobince on 2009-06-03
> i have been told that anti sql scripts are inserted in the file config.php since all php request pass thru config.phpWhoever told you that is dangerously misinformed. To stop SQL injections&#8201;—&#8201;and HTML injections&#8201;—&#8201;you must *understand* what you are doing when you do a string concatenation to make SQL or HTML, and why it can be a problem. **There is no magic bullet**, no one script you can drop in to your setup to fix security holes in badly-written applications; instead, you must fix the application.

Trying to avoid the problem by filtering characters on the way into the script (like in your example code and any number of other equally-broken ‘anti-injection’ scripts) is *never* the right thing. The example code filters a seemingly-random selection of characters that are ‘special’ in completely different contexts, and doesn't perform any one escaping scheme fully. It is clear that the coder who wrote it has no understanding of what SQL-injection and HTML-injection actually are.

For example, with the above code, apostrophes are removed, with the seeming aim of stopping SQL injections. But if you are using MySQL or PostgreSQL, the backslash is also a special character: an attacker could put one at the end of a string, you'd concatenate it blindly into a string literal, escaping the final ' delimiter and making the following SQL part of the literal&#8201;—&#8201;and a later literal could become SQL and boom, you're hacked.

Meanwhile it's trying to HTML-escape prematurely, so you'll be storing rubbish like “&amp;amp;amp;amp;” in your database when people edit strings containing ampersands. And semicolons and percent signs are removed for no plausible reason at all. Someone who tries to put their name in as “O'Reilly” or talk about “100% cover” will find their name and conversations mauled.

Instead:

1. Keep all your strings in plain text form inside your scripts (and database storage) with no escaping applied. Now you can process them with simple string operations without having to worry about breaking a ‘&quot;’ or ‘&lt;’.

2. The only thing worth filtering incoming GET/POST input for is control characters, in fields where you don't want to allow them.

3. Any time you write a string to HTML, use htmlspecialchars:

```
<td>Name:</td><td><?= $name ?></td> <!-- WRONG, dangerous -->
<td>Name:</td><td><?php echo($name); ?></td> <!-- WRONG, dangerous -->
 <?php echo("<td>Name:</td><td>$name</td>"); ?> <!-- WRONG, dangerous -->
 
<td>Name:</td><td><?= htmlspecialchars($name) ?></td> <!-- OK -->
<?php function h($s) { echo(htmlspecialchars($s)); } ?>
<td>Name:</td><td><?php h($name) ?></td> <-- OK -->
```

4. Any time you write a string literal to SQL, use the appropriate escaping function for your database:

```
mysql_query("SELECT user WHERE username='$name'"); // WRONG, very dangerous
mysql_query("SELECT user WHERE username='".mysql_real_escape_string($name)."'"); // OK
```Alternatively, use a database access layer that will take care of this escaping for you, such as [prepare() in MySQLi]("http://de2.php.net/manual/en/mysqli-stmt.prepare.php").

---

### Post by kenweill on 2009-06-11
Thanks for your reply.

Though, I'm not a coder but I will share your thoughts and ideas to the real coders of the Control Panel Im using.

---

### Post by XanTrax on 2009-06-12
Just a heads up, as you ask for MSSQL and MySQL, the construction of SQL queries is different between MySQL and MSSQL.  Not too different but different enough to where you can close up a SQL injection in MSSQL but still have a separate one open in MySQL but you *think* you're closing both.

See what im getting at?

EDIT: And, if someone develops this, there is a lot of room for repeated regression (see above)

---


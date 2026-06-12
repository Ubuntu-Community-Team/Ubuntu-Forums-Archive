---
title: "trying to make a login for my site"
date: 2007-05-16
forum: Server Platforms
---

### Post by dfreer on 2007-05-16
Hey,

  so I am trying to create a login for my site, anyone know of a good guide or can spend a few minutes helping me out?

Here's what I'm trying to do:
[LIST]
[*]Create a login on my site that asks for username and password
[*]Create a cookie/session that keeps user logged in until they log out/close browser, and a "remember me" so that they are always logged in.
[*]Use SSL on all pages once logged in
[*]I want the login to use an http form to login/register, and use php and mysql to log user in and store user info
[*]The logged on users need to be able to access certain pages that normal users cannot view at all
[/LIST]

This is what I have done so far:
[LIST]
[*]Create my website with a http login form
[*]create a mysql database with tables and all fields setup to store user info
[*]create php test file and tested to make sure that php can open, query, and modify the mysql database
[*]installed SSL and have it completely working
[/LIST]

So basically, I just need to know how to get php to get the form information, check to see if the username password is valid, and log the user into the SSL webpage. I also need to prevent unauthorized users from seeing this webpage and using SSL. Anyone think they could help?

---

### Post by MJN on 2007-05-16
Surely you want SSL active *before* the user logs in, in order to protect their credentials from packet sniffers?

Mathew

---

### Post by huggy77 on 2007-05-16
i hope i am reading your question right, but you might be better off going to a php forum - they probably have  a couple of great security guys on there that will give you some snippets to throw in your pages.    I am just starting to lear SSL - not much help there...

i am guessing php is similar to coldfusion...  in cf you would post the data of the form to another page.  then query the db for a hit.  if you get a hit, you would create a session that would contain the user id from the db...  then you make sure that session exists at the top of every page your want to serve.

---

### Post by dfreer on 2007-05-16
> **MJN said:**
> Surely you want SSL active *before* the user logs in, in order to protect their credentials from packet sniffers?

Mathew

huh, never thought of that. Yeah, it sure looks like the login page for my bank uses SSL before I login, for some reason I assumed that SSL should activate after login. Well, that's easily fixable, but :( still gotta figure out how to use php to login. I'll see if I can find some sites that login with php and just examine their code. But if anyone else knows of a good guide in the meantime I'll use that.

EDIT: Yes, I've seen this link:
[http://www.devshed.com/c/a/PHP/Creating-a-Secure-PHP-Login-Script/](http://www.devshed.com/c/a/PHP/Creating-a-Secure-PHP-Login-Script/)
But I'm not quite sure how to implement it, it seems like the code for the login page itself is missing (or the author just assumes people should know how to make it).

> **huggy77 said:**
> i hope i am reading your question right, but you might be better off going to a php forum

i am guessing php is similar to coldfusion...  in cf you would post the data of the form to another page.  then query the db for a hit.  if you get a hit, you would create a session that would contain the user id from the db...  then you make sure that session exists at the top of every page your want to serve.

Any php forums you'd recommend?

Yeah, that is basically what I need to do. User enters login data > data is checked for validity in database > if valid cookies and session is set until user logs out or closes the window.

I'm just not sure on how to do the above process, and how to limit access to certain pages or folders from anyone not logged in, and certain pages or folders to only users of a special class (I have some values in my database that state whether a user has permission to access the 5 some areas I have defined (for example admin area, wiki, etc)).

---

### Post by Acksys on 2007-05-16
[http://devzone.zend.com/public/view/controller/public/action/view/tag/PHP101/module/default/page/2](http://devzone.zend.com/public/view/controller/public/action/view/tag/PHP101/module/default/page/2)

This is a great series for new PHP programmers. Last time I checked, SSL wasn't covered, but it'll give you a great introduction to PHP/MySQL and form interaction and basic security.

---

### Post by dfreer on 2007-05-16
> **Acksys said:**
> [http://devzone.zend.com/public/view/controller/public/action/view/tag/PHP101/module/default/page/2](http://devzone.zend.com/public/view/controller/public/action/view/tag/PHP101/module/default/page/2)

This is a great series for new PHP programmers. Last time I checked, SSL wasn't covered, but it'll give you a great introduction to PHP/MySQL and form interaction and basic security.

Thanks! Although it is a bit hard to find the info I needed, I did find a tutorial on this page:
[http://devzone.zend.com/node/view/id/646](http://devzone.zend.com/node/view/id/646)
It looks like this will solve most of my problems.
At the bottom of the page is a comment from an user discussing an security issue (I think he's discussing an SQL injection attack). Any thoughts, is this true (and are there any other security issues to worry about)?

Thanks again for the info so far guys!

---

### Post by dfreer on 2007-05-22
I'm really having problems with this guys, could use some help!

Basically, I have everything set up so far. I can enter my username/password into a html form, pass it to a manage-login.php page that handles authentication, and is *supposed* to redirect to the secure index.php page by using header(). First I tested every process, to make sure it is querying/connecting to the database and so forth, and then commented out the output lines so that header() will work, hopefully. 

Problem is, I *cannot* get header() to redirect!! it's driving me nuts!

I created a failsafe.php to see if it is a problem with header(), and it's not. I can even login this way by manually setting the $_SESSION variable, so I'm thinking it has to do with header() not wanting to proceed due to some output, but I cannot find the output that is causing it to **** up. 

Here's some of my files for you guys to look at, see if it makes any sense. If you see any security concerns feel free to point those out, I could use the help! Note that at the bottom of manage-login there is a if loop, in it I added some echo "pass"/"fail" to see if it makes it that far, it does.

failsafe.php (works!):
```
<?php
$_SESSION['member_id'] = '1';
header('Location: index.php');
?>
```

manage-login.php:
```
<?php
// Set Session
session_start();

// Include needed files
require_once('db_login.php');
require_once('manage-login.php');

// Uncomment for debugging
//echo "Connecting to mysql: ";

// Create a connection to mysql, die upon error
$connection = mysql_connect($db_host, $db_username, $db_password);
if (!$connection)
{
	// For security do not use mysql_error! Use one or the other!!
	//die ("ERROR! <br />". mysql_error());
	die ("ERROR! Could not connect to mysql! <br />");
}

// Uncomment for debugging
//echo "OK! <br />";
//echo "Connecting to Database: ";

// Select and use database, die upon error
$db_select = mysql_select_db($db_database);
if (!$db_select)
{
	// For security do not use mysql_error! Use one or the other!!
	//die ("ERROR! <br />". mysql_error());
	die ("ERROR! Could not connect to database! <br />");
}

// Uncomment for debugging
//echo "OK! <br />";

// Login Field
if(isset($_POST['submit'])) :

	// Username and password sent from signup form
	// First we remove all HTML-tags and PHP-tags, then we create a sha1-hash

	// Uncomment for debugging
	//echo "Here's the username you submitted: ".$_POST['username']."<br />";
	$username = strip_tags($_POST['username']);
	//echo "..And here is is after being striped: ".$username."<br />";
	
	// Uncomment for debugging
	//echo "Here's the password you submitted: ".$_POST['password']."<br />";
	$password = sha1(strip_tags($_POST['password']));
	//echo "..And here is is after being striped and then encrypted: ".$password."<br />";

	// setting variables for query
	$select = ' SELECT ';
	$column = ' * ';
	$from   = ' FROM ';
	$tables = ' `users` ';
	$where  = ' WHERE ';
	$first_cond = ' username = ';
	$and	= ' AND ';
	$second_cond = ' user_password = ';
	$end	= ';';
	$query  = $select.$column.$from.$tables.$where.$first_cond.
	"'".mysql_real_escape_string($username)."'".$and.$second_cond."'".mysql_real_escape_string($password)."'".$end;
	
	// Uncomment for debugging
	//echo "Here's the query string: <br />".$query."<br />";	
	//echo "Here's the result of mysql_escape_string: <br />"."'".mysql_real_escape_string($username)."'"."<br />"."'".mysql_real_escape_string($password)."'"."<br />";


	$query_result = mysql_query( $query );
	
	// Uncomment for debugging
	//echo "Here's the login info: <br />";

	// Uncomment for debugging
	//while ($row = mysql_fetch_array($query_result, MYSQL_BOTH))
	//{
	//	// Setting display variables
	//	//$db_user_id = $row["user_id"];
	//	//$db_username = $row["username"];
	//	//$db_password = $row["password"];
	//	$db_nickname = $row["nickname"];
	//	//$first_name = $row["first_name"];
	//	//$last_name = $row["last_name"];
	//	//$email = $row["email"];
	//	//$ssh_rsa_key = $row["ssh_rsa_key"];
	//
	//	echo "Here's your Nickname: ".$db_nickname."<br />";
	//}
	
	// Uncomment for debugging
	//echo "The result of mysql_num_rows: ".mysql_num_rows($query_result)."<br />";


	if(1 != mysql_num_rows($query_result)) :

		// MySQL returned zero rows (or there's something wrong with the query)
		// Uncomment for debugging
		//echo "You have failed the login screen!<br />";

		header('Location: login.php?msg=login_failed');

	else :
		// We found the row that we were looking for
		$row = mysql_fetch_assoc($query_result);

		//Uncomment for debugging
		//echo "You have passed the login screen!<br />";
		//echo "The row information: ".$row['user_id']."<br />";

		// Register the user ID for further use
		$_SESSION['member_id'] = $row['user_id'];
		header('Location: index.php');
	endif;
endif;

mysql_close($connection);
?>
```

Same thing as above but cleaned up (without so many comments, kinda unreadable before):
```
<?php
// Set Session
session_start();

// Include needed files
require_once('db_login.php');
require_once('manage-login.php');

// Create a connection to mysql, die upon error
$connection = mysql_connect($db_host, $db_username, $db_password);
if (!$connection)
{
	die ("ERROR! Could not connect to mysql! <br />");
}

// Select and use database, die upon error
$db_select = mysql_select_db($db_database);
if (!$db_select)
{
	die ("ERROR! Could not connect to database! <br />");
}

// Login Field
if(isset($_POST['submit'])) :

	// Username and password sent from signup form
	// First we remove all HTML-tags and PHP-tags, then we create a sha1-has
	$username = strip_tags($_POST['username']);
	$password = sha1(strip_tags($_POST['password']));


	// setting variables for query
	$select = ' SELECT ';
	$column = ' * ';
	$from   = ' FROM ';
	$tables = ' `users` ';
	$where  = ' WHERE ';
	$first_cond = ' username = ';
	$and	= ' AND ';
	$second_cond = ' user_password = ';
	$end	= ';';
	$query  = $select.$column.$from.$tables.$where.$first_cond.
	"'".mysql_real_escape_string($username)."'".$and.$second_cond."'".mysql_real_escape_string($password)."'".$end;
	
	$query_result = mysql_query( $query );
	
	if(1 != mysql_num_rows($query_result)) :

		// MySQL returned zero rows (or there's something wrong with the query)
		header('Location: login.php?msg=login_failed');

	else :
		// We found the row that we were looking for
		$row = mysql_fetch_assoc($query_result);
		$_SESSION['member_id'] = $row['user_id'];
		header('Location: index.php');
	endif;
endif;

mysql_close($connection);
?>
```

---


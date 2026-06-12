---
title: "Help ! writing into a database"
date: 2008-05-17
forum: Server Platforms
---

### Post by shotos on 2008-05-17
i am new to this server stuff and just succeeded in writing my first php script to allow a user towrite into a database i created. After filling out the form and clicking the submit button, the html form is shown again and the data is also not written into the database. Any help will be appreciated.
Below is the php script
<html>
<head>
<title>Listing 12.3 Adding user input to a database</title>
</head>
<body>
<?php
if (isset( $domain ) && isset( $sex ) && isset( $domain ))
	{
	//check user input here!
	$dberror = "";
	$ret = add_to_database($domain, $sex, $mail, $dberror);
	if (!$ret)
		print "Error: $dberror<BR>";
	else 
		print "Thank you very much";
	}
else {
	write_form();
	}

function add_to_database($domain, $sex, $mail, &$dberror )
	{
	$user = "kwasi";
	$pass =  "shotosnero";
	$db = "sample";
	$link = mysqql_pconnect("localhost", $user, $pass );
	if (! $link)
	     {
	      $dberror = "Couldn't connect to MySQL server";
	      return false;
	      }
	if (! mysql_select_db($db, $link))
		{
		$dberror = mysql_error();
		return false;
		}
$query = "INSERT INTO domains (domain, sex, mail)
	   values ('$domain','$sex', '$mail')";
	if(! mysql_query($query, $link))
	   {
		$dberror = mysql_error();
		return false;
	    }
	return true;
	}

function write_form()
	{
	global $PHP_SELF;
	print"<form action=\"$PHP_SELF\" method=\"POST\">\n";
	print"<input type=\"text\" name=\"domain\">";
	print"The domain you would like<p>\n";
	print"<input TYPE=\"text\" name=\"mail\">";
	print"Your mail address<p>\n";
	print"<select name=\"sex\">\n";
	print"\t<option value=\"F\"> Female\n";
	print"\t<option value=\"M\"> Male\n";
	print"</select>\n";
	print"<input type=\"submit\" value=\"submit!\">\n</form>\n";
	}
?>
</body>
</html>

---

### Post by hyper_ch on 2008-05-17
You will have to have register_globals enabled for that to work... this is not adviced....

I made a few corrections here but haven't tested it.... furthermore for posting also use [noparse][php][/php][/noparse] tags to make it more reader-friendly or attach the file as indented text file.



[php]
<html>
<head>
<title>Listing 12.3 Adding user input to a database</title>
</head>
<body>
<?php

$domain = $_POST['domain'];
$sex = $_POST['sex'];

if($domain = '') { unset($domain) };
if($sex = '') { unset($sex) };

if (isset( $domain ) && isset( $sex ))
{
	//check user input here!
	$dberror = "";
	$ret = add_to_database($domain, $sex, $mail, $dberror);
	if (!$ret)
	{
		print "Error: $dberror<BR>";
	} else
	{
		print "Thank you very much";
	}
} else
{
	write_form();
}

function add_to_database($domain, $sex, $mail, &$dberror )
{
	$user = "kwasi";
	$pass = "shotosnero";
	$db = "sample";
	$link = mysqql_pconnect("localhost", $user, $pass );
	if (! $link)
	{
		$dberror = "Couldn't connect to MySQL server";
		return false;
	}
	if (! mysql_select_db($db, $link))
	{
		$dberror = mysql_error();
		return false;
	}
	$query = "INSERT INTO domains (domain, sex, mail)
	values ('$domain','$sex', '$mail')";
	if(! mysql_query($query, $link))
	{
		$dberror = mysql_error();
		return false;
	}
	return true;
}

function write_form()
{
	global $PHP_SELF;
	print"<form action=\"$PHP_SELF\" method=\"POST\">\n";
	print"<input type=\"text\" name=\"domain\">";
	print"The domain you would like<p>\n";
	print"<input TYPE=\"text\" name=\"mail\">";
	print"Your mail address<p>\n";
	print"<select name=\"sex\">\n";
	print"\t<option value=\"F\"> Female\n";
	print"\t<option value=\"M\"> Male\n";
	print"</select>\n";
	print"<input type=\"submit\" value=\"submit!\">\n</form>\n";
}
?>
</body>
</html>
[/php]

---

### Post by shotos on 2008-05-17
Thanks hyper_ch, i copied ur code and ran it, the html forms wasn´t displayed but an entry into the database was made. Only the entry was blank spaces.

---

### Post by shotos on 2008-05-17
Thanks hyper_c again. i did some modifications to the code and it did work perfectly.
below is the new version.
[php]
<html>
<head>
<title>Listing 12.3 Adding user input to a database</title>
</head>
<body>
<?php

$domain = $_POST['domain'];
$sex = $_POST['sex'];
$mail = $_POST['mail'];
/*
if($domain = '') { unset($domain); }
if($sex = '') { unset($sex); }*/

if (isset( $domain ) && isset( $sex ) && isset($mail))
{
    //check user input here!
    $dberror = "";
    $ret = add_to_database($domain, $sex, $mail, $dberror);
    if (!$ret)
    {
        print "Error: $dberror<BR>";
    } else
    {
        print "Thank you very much";
    }
} else
{
    write_form();
}

function add_to_database($domain, $sex, $mail, &$dberror )
{
    $user = "kwasi";
    $pass = "shotosnero";
    $db = "sample";
    $link = mysql_pconnect("localhost", $user, $pass );
    if (! $link)
    {
        $dberror = "Couldn't connect to MySQL server";
        return false;
    }
    if (! mysql_select_db($db, $link))
    {
        $dberror = mysql_error();
        return false;
    }
    $query = "INSERT INTO domains (domain, sex, mail)
    values ('$domain','$sex', '$mail')";
    if(! mysql_query($query, $link))
    {
        $dberror = mysql_error();
        return false;
    }
    return true;
}

function write_form()
{
    global $PHP_SELF;
    print"<form action=\"$PHP_SELF\" method=\"POST\">\n";
    print"<input type=\"text\" name=\"domain\">";
    print"The domain you would like<p>\n";
    print"<input TYPE=\"text\" name=\"mail\">";
    print"Your mail address<p>\n";
    print"<select name=\"sex\">\n";
    print"\t<option value=\"F\"> Female\n";
    print"\t<option value=\"M\"> Male\n";
    print"</select>\n";
    print"<input type=\"submit\" value=\"submit!\">\n</form>\n";
}
?>
</body>
</html>
[php]

---

### Post by shotos on 2008-05-17
Thanks hyper_c again. i did some modifications to the code and it did work perfectly.
below is the new version.
[php]
<html>
<head>
<title>Listing 12.3 Adding user input to a database</title>
</head>
<body>
<?php

$domain = $_POST['domain'];
$sex = $_POST['sex'];
$mail = $_POST['mail'];
/*
if($domain = '') { unset($domain); }
if($sex = '') { unset($sex); }*/

if (isset( $domain ) && isset( $sex ) && isset($mail))
{
    //check user input here!
    $dberror = "";
    $ret = add_to_database($domain, $sex, $mail, $dberror);
    if (!$ret)
    {
        print "Error: $dberror<BR>";
    } else
    {
        print "Thank you very much";
    }
} else
{
    write_form();
}

function add_to_database($domain, $sex, $mail, &$dberror )
{
    $user = "kwasi";
    $pass = "shotosnero";
    $db = "sample";
    $link = mysql_pconnect("localhost", $user, $pass );
    if (! $link)
    {
        $dberror = "Couldn't connect to MySQL server";
        return false;
    }
    if (! mysql_select_db($db, $link))
    {
        $dberror = mysql_error();
        return false;
    }
    $query = "INSERT INTO domains (domain, sex, mail)
    values ('$domain','$sex', '$mail')";
    if(! mysql_query($query, $link))
    {
        $dberror = mysql_error();
        return false;
    }
    return true;
}

function write_form()
{
    global $PHP_SELF;
    print"<form action=\"$PHP_SELF\" method=\"POST\">\n";
    print"<input type=\"text\" name=\"domain\">";
    print"The domain you would like<p>\n";
    print"<input TYPE=\"text\" name=\"mail\">";
    print"Your mail address<p>\n";
    print"<select name=\"sex\">\n";
    print"\t<option value=\"F\"> Female\n";
    print"\t<option value=\"M\"> Male\n";
    print"</select>\n";
    print"<input type=\"submit\" value=\"submit!\">\n</form>\n";
}
?>
</body>
</html>
[/php]

---

### Post by hyper_ch on 2008-05-17
my mistake, you need to correct your code to this:
[php]
$domain = $_POST['domain'];
$sex = $_POST['sex'];
$mail = $_POST['mail'];

if($domain == '') { unset($domain); }
if($sex == '') { unset($sex); }
if($mail == '') { unset($mail); }
[/php]

you want to check if the domain/sex/mail is empty and if it is empty, then unset the $var.... because if it's not unset, then the (isset...) part will never fail.

---

### Post by shotos on 2008-05-17
it worked.... tanx

---

### Post by hyper_ch on 2008-05-17
or instead of using this:

[php]
$domain = $_POST['domain'];
$sex = $_POST['sex'];
$mail = $_POST['mail'];

if($domain == '') { unset($domain); }
if($sex == '') { unset($sex); }
if($mail == '') { unset($mail); }


if (isset( $domain ) && isset( $sex ) && isset($mail))
[/php]

you could use this:

[php]
$domain = $_POST['domain'];
$sex = $_POST['sex'];
$mail = $_POST['mail'];


if ($domain!='' && $sex!='' && $mail!='' )
[/php]

or you could make some user feedback:

[php]
<html>
<head>
<title>Listing 12.3 Adding user input to a database</title>
</head>
<body>
<?php

$domain = $_POST['domain'];
$sex = $_POST['sex'];
$mail = $_POST['mail'];

unset($error);
if($domain == '') { unset($domain); $error .= 'No domain submitted.<br>' }
if($sex == '') { unset($sex); $error .= 'No sex indicated.<br>' }
if($mail == '') { unset($mail); $error .= 'No email given.<br>' }  

if (isset( $domain ) && isset( $sex ) && isset($mail))
{
    //check user input here!
    $dberror = "";
    $ret = add_to_database($domain, $sex, $mail, $dberror);
    if (!$ret)
    {
        print "Error: $dberror<BR>";
    } else
    {
        print "Thank you very much";
    }
} else
{
    write_form($error);
}

function add_to_database($domain, $sex, $mail, &$dberror )
{
    $user = "kwasi";
    $pass = "shotosnero";
    $db = "sample";
    $link = mysql_pconnect("localhost", $user, $pass );
    if (! $link)
    {
        $dberror = "Couldn't connect to MySQL server";
        return false;
    }
    if (! mysql_select_db($db, $link))
    {
        $dberror = mysql_error();
        return false;
    }
    $query = "INSERT INTO domains (domain, sex, mail)
    values ('$domain','$sex', '$mail')";
    if(! mysql_query($query, $link))
    {
        $dberror = mysql_error();
        return false;
    }
    return true;
}

function write_form($error)
{
    global $PHP_SELF;
    print"$error\n";
    print"<form action=\"$PHP_SELF\" method=\"POST\">\n";
    print"<input type=\"text\" name=\"domain\" value='" . $_POST['domain'] . "'>";
    print"The domain you would like<p>\n";
    print"<input TYPE=\"text\" name=\"mail\"  value='" . $_POST['mail'] . "'>";
    print"Your mail address<p>\n";
    print"<select name=\"sex\">\n";
    print"\t<option value=\"F\"> Female\n";
    print"\t<option value=\"M\"> Male\n";
    print"</select>\n";
    print"<input type=\"submit\" value=\"submit!\">\n</form>\n";
}
?>
</body>
</html>
[/php]

---

### Post by yoda2031 on 2008-05-17
Slightly more elegantly...
[php]
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv='Content-type' content='text/html;charset=utf-8'>
<title>Listing 12.3 Adding user input to a database</title>
</head>
<body>
<?php
// keep configurable options at the top for ease of editing
$user = "kwasi";
$pass = "shotosnero";
$db = "sample";
$dbhost = "localhost";   // allow configuration of this for portability
$tbname = "domains";     // allow configuration of this for portability

$domain = $_POST['domain'];
$sex = $_POST['sex'];
$mail = $_POST['mail'];

unset($error);
if($domain == '') { unset($domain); $error .= 'No domain submitted.<br>' }
if($sex == '') { unset($sex); $error .= 'No sex indicated.<br>' }
if($mail == '') { unset($mail); $error .= 'No email given.<br>' }  

if ($domain != "" && $sex != "" && $mail != "")
{
    $ret = add_to_database($domain, $sex, $mail);
    if ($ret != "")
    {
        print "Error: $ret<br>";
    } 
    else
    {
        print "Information submitted:<br>Domain:" . $domain . "<br>Sex:" . $sex . "<br>Mail:" . $mail . "<br>";
    }
} else
{
    write_form($error);
}

function add_to_database($domain, $sex, $mail)
{
    $link = mysql_pconnect($dbhost, $user, $pass );
    if (! $link)
    {
        return "MySQL Server could not be found on host " . $dbhost;
    }
    if (! mysql_select_db($db, $link))
    {
        return mysql_error();
    }
    $query = "INSERT INTO `$db`.`$tbname` (`domain`, `sex`, `mail`)
    values ('$domain','$sex', '$mail')";
    if(! mysql_query($query, $link))
    {
        return mysql_error();
    }
    return "";
}

function write_form($error)
{
    global $PHP_SELF;
    print "$error\n";
    print "<form action=\"$PHP_SELF\" method=\"POST\">\n";
    print "<input type=\"text\" name=\"domain\" value='" . $_POST['domain'] . "'>";
    print "The domain you would like<p>\n";
    print "<input TYPE=\"text\" name=\"mail\"  value='" . $_POST['mail'] . "'>";
    print "Your mail address<p>\n";
    print "<select name=\"sex\">\n";
    print "\t<option value=\"F\"> Female\n";
    print "\t<option value=\"M\"> Male\n";
    print "</select>\n";
    print "<input type=\"submit\" value=\"submit!\">\n</form>\n";
}
?>
</body>
</html>
[/php]

Some things I would change but are more up to the individual coder to use or not, and the specific application of the script seems to warrant a few quirks.  Note the most important change is the addition of $dbhost and $tbname variables, which should be configurable in case the script is ported to a different platform in which the database is on a different server or if the table name changes for any reason.  It also allows the script to be modified to create backups in a second table - calling the function a second time with a different "$tbname" value.

Sorry to kind of barge in on someone else's solution, but I just love to tweak!  All credit to hyper_ch for the original solution.  Note also the inclusion of the meta content-type and DOCTYPE declarations, which as we all know are HTML 101.

---

### Post by hyper_ch on 2008-05-17
there are many things that could be changed....

(1) complete separation of html and php
(2) better error reporting (still lacking the radio buttons there...)
(3) maybe even ajax to check on-the-fly whether that info is already in the database
(4) maybe JS form checks instead of real submitting and checking then
(5) move the whole mysql database connection stuff outside into a file that will be included... maybe even move it outside the web root...
...
...
...

With practice come more elegant ways ;)

---

### Post by shotos on 2008-05-17
its ma first experience on the forum and am loving it!!!
tanx y`all

---

### Post by hyper_ch on 2008-05-17
with time you'll get much better at it ;) good luck :)

---


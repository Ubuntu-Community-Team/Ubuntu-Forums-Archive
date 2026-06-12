---
title: "PHP showing special characters as question marks when pulling from DB"
date: 2013-08-24
forum: Server Platforms
---

### Post by bigmonmulgrew on 2013-08-24
Hi guys
I have a LAMP server running Drupal 7 based on ubuntu 12.04

I'm pulling data from a secondary database (not drupals main one) for a project I am testing. I'm using php to build a table with the results of the database.

the problem is it wont show special characters, it just shows question marks. These are not the normal question marks in diamonds Drupal uses when it is not happy with the characters you have used. It is just a normal question mark symbol.

I've used php to directly print the string it should be showing  and it displays fine. 

The website is here
[http://regattainabox.co.uk/content/ross-master-junior-regatta-draw#]("http://regattainabox.co.uk/content/ross-master-junior-regatta-draw#")

It should be showing
```
(3) Evesham RC (EVE-Griffiths)&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488; 11:18
```

I've checked and setup the default character encoding in the database, mysql, php and they are all utf8
I've manually set utf8 in my php and no difference.

Any idea why this is ignoring the special characters. Any info would be much appreciated.

Heres the php I'm using
[PHP]<?php
$CompID = 3;
$Host="localhost";
$User="lol";
$Password="lol";
$DatabaseName="lol";
 // Connects to your Database
 $con=mysql_connect($Host, $User, $Password, $DatabaseName);
// Change character set to utf8
 mysqli_set_charset($con,"utf8");
 mysql_select_db("RiaBwebDB") or die(mysql_error());
 $data = mysql_query("SELECT * FROM xtblEventList WHERE "."CompetitionID = ".$CompID." ORDER BY EventNo")
 or die(mysql_error());
 Print "<table border cellpadding=3 >";

 Print "<tr>";
Print "<th>Race No:</th> ";
 Print "<th>Race Time:</th>";
 Print "<th>Re-Time:</th>  ";
 Print "<th>Race Type:</th> ";
 Print "<th>Event:</th> ";
 Print "<th>Crew No:</th>  ";
 Print "<th>Lane 1:</th> ";
 Print "<th>Crew No:</th> ";
 Print "<th>Lane 2:</th> ";
 Print "<th>Crew No:</th>  ";
 Print "<th>Winner:</th> ";
 Print "<th>Next Race:</th>  ";
 Print "<th>Won By:</th></tr>";
 while($info = mysql_fetch_array( $data ))
 {
 Print " <td>".$info['EventNo'] . "</td> ";
 Print "<td>".$info['EventName'] . "</td> ";
 Print "<td>".$info['EventIdentifier'] . "</td> ";
 Print "<td>".$info['DrawString'] . " </td></tr>";
 }
 Print "</table>";

var_dump(mysqli_get_charset($con));

mysqli_close($con);
 ?>
[/PHP]

---

### Post by SeijiSensei on 2013-08-25
I looked at the source for that page and see only question marks there as well.

What special characters should it be displaying?

BTW, I recommend adding a "\n" after the "</tr>" codes that end table rows.  It makes it much easier to read the HTML code that PHP generates.

---

### Post by koenn on 2013-08-25
can you find out if there's a charset set on the **table** whare that data comes from ?


also lots of char set stuff tegatding programs querying databeses : [http://dev.mysql.com/doc/refman/5.1/en/charset-connection.html](http://dev.mysql.com/doc/refman/5.1/en/charset-connection.html)

---

### Post by sandyd on 2013-08-25
Are you using UTF-8 both on the db/tables (mysql_set_charset) and php?
See [http://stackoverflow.com/questions/3547278/mysql-result-returns-question-mark-instead-of-etc](http://stackoverflow.com/questions/3547278/mysql-result-returns-question-mark-instead-of-etc) for details on using mysql_set_charset (even though [it is depreciated]("php.net/manual/en/function.mysql-set-charset.php"))

---

### Post by bigmonmulgrew on 2013-08-25
> **SeijiSensei said:**
> I looked at the source for that page and see only question marks there as well.

What special characters should it be displaying?

BTW, I recommend adding a "\n" after the "</tr>" codes that end table rows.  It makes it much easier to read the HTML code that PHP generates.

I showed what it should be showing in my original post. If I put the characters in directly as a print string then it displays fine. It appears to be the step where the data is pulled from the database that is falling over.
Thanks for the /n tip.

---

### Post by bigmonmulgrew on 2013-08-25
> **koenn said:**
> can you find out if there's a charset set on the **table** whare that data comes from ?


also lots of char set stuff tegatding programs querying databeses : [http://dev.mysql.com/doc/refman/5.1/en/charset-connection.html](http://dev.mysql.com/doc/refman/5.1/en/charset-connection.html)

There is a character set on the database AND table. It's utf8. I'll checkout your link tomorrow I'm out now

---

### Post by bigmonmulgrew on 2013-08-25
> **sandyd said:**
> Are you using UTF-8 both on the db/tables (mysql_set_charset) and php?
See [http://stackoverflow.com/questions/3547278/mysql-result-returns-question-mark-instead-of-etc](http://stackoverflow.com/questions/3547278/mysql-result-returns-question-mark-instead-of-etc) for details on using mysql_set_charset (even though [it is depreciated]("php.net/manual/en/function.mysql-set-charset.php"))

Yes I've checked the db and tables both set to utf8.

I've checked php and both set it.in code to utf8 and set the default on the server to utf8, there was no default.

I'm sure I must be missing it somewhere but I can't figure out where.

---

### Post by SeijiSensei on 2013-08-25
Does using a PHP function like [htmlentities()]("http://php.net/manual/en/function.htmlentities.php") or [htmlspecialchars()]("http://www.php.net/manual/en/function.htmlspecialchars.php") help?

Are the characters already stripped from the string when it is SELECTed from the database?  Perhaps there are string functions in the DB you can use to convert the string into something that will display correctly?

What if you reverse the order of these commands 
```
mysqli_set_charset($con,"utf8");
mysql_select_db("RiaBwebDB") or die(mysql_error());

```
so that you set the character encoding after selecting the database, not before?

---

### Post by bigmonmulgrew on 2013-08-30
> **SeijiSensei said:**
> Does using a PHP function like [htmlentities()]("http://php.net/manual/en/function.htmlentities.php") or [htmlspecialchars()]("http://www.php.net/manual/en/function.htmlspecialchars.php") help?

Are the characters already stripped from the string when it is SELECTed from the database?  Perhaps there are string functions in the DB you can use to convert the string into something that will display correctly?

What if you reverse the order of these commands 
```
mysqli_set_charset($con,"utf8");
mysql_select_db("RiaBwebDB") or die(mysql_error());

```
so that you set the character encoding after selecting the database, not before?

Sadly changing the order of the command has made no difference.

---


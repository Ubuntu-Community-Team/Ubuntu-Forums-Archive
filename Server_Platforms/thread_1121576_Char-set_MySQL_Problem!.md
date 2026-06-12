---
title: "Char-set MySQL Problem!"
date: 2009-04-10
forum: Server Platforms
---

### Post by Spikerok on 2009-04-10
I have database in cp1251, i have improted in mysql 5.0.67, before i was using mysql 5.0.45 which is on windows localhost with char set o cp125. Problem wih russian language. I get what i have imported in databse. When i output information on the website im using next command to display what i see in database, other ways i get question marks every where are on the page
[PHP]
$result = mysql_query("SET NAMES cp1251") or die(mysql_error());
$result = mysql_query("SET CHARACTER SET cp1251") or die(mysql_error());
[/PHP]

and here is the problem, i can display data, but i can't add data.
Well i can, but if add data, it will be added as a question marks.

so her is example of insert code im using
[PHP]
$sql   = "INSERT INTO tbl_articles (id, title, text, date) 
     VALUES ('$Id', '$name', '$description', NOW())";
   $result = dbQuery($sql); 
[/PHP]
So if 
$id = 1
$name = Spiker
$description = Hello World

all them varibales will be in russian, they will be imported in database as question marks. I was thinking of changing database to utf8, but found out that im getting similar problem, but not question marks this time, but some kind of chines letters.
I have tried using official guide on mysql.com on how to fix this problem, it didn't worked, i think they made it for different linux destributor..

---

### Post by dgoosens on 2009-04-10
hi,

you might want to read this:
[http://www.tanzilo.com/2008/10/13/php-mysql-unicode-solution-to-chinese-russian-or-any-language/]("http://www.tanzilo.com/2008/10/13/php-mysql-unicode-solution-to-chinese-russian-or-any-language/")

you will see that you have to make those char encoding queries before inserting things in the database as well
[PHP]
mysql_query("SET character_set_client=utf8", $dbLink);
mysql_query("SET character_set_connection=utf8", $dbLink);
[/PHP]

in your case this would become:
[PHP]
mysql_query("SET character_set_client=cp1251", $dbLink);
mysql_query("SET character_set_connection=cp1251", $dbLink);
[/PHP]

hope this helps

---

### Post by Spikerok on 2009-04-10
Thank you my friend!
You saved my life! \\:D/

---


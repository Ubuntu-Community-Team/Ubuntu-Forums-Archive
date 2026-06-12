---
title: "Dreaming of a script to automate Mysql database"
date: 2008-03-12
forum: Server Platforms
---

### Post by volkswagner on 2008-03-12
I am trying to learn by doing.  I have an Ubuntu 6.06 LAMP server.  Mostly followed the perfect setup and community docs.  I have been reading up on virtual hosts, VM, Mysql, etc, etc.

I am trying to set up a database for a inventory based website.  I have it hosted now by webng, without any database for inventory.  This is a new site with no SEO, and only traffic is by word of mouth.  We do have high hopes of a greater volume.

The point of the post is can some tell me if it is possible to extract data from my already created paypal buttons?  I have over 150 .txt files like this.  One for each item in inventory.  I would like to be able to extract the, price, description, shipping weight from these text files to add to a table in mysql.  I see one immediate problem...the integer and varchar values are all in quotes.   Is this a major problem?  What I am trying to do, is possible or not?  Can anyone lend a hint on how to make it happen.

here is a sample .txt
```

<form target="_self" action="https://www.paypal.com/cgi-bin/webscr" method="post">
<input type="image" src="https://www.paypal.com/en_US/i/btn/btn_cart_SM.gif" border="0" name="submit" alt="Make payments with PayPal - it's fast, free and secure!"/>
<img alt="" border="0" src="https://www.paypal.com/en_US/i/scr/pixel.gif" width="1" height="1">
<input type="hidden" name="add" value="1"/>
<input type="hidden" name="cmd" value="_cart"/>
<input type="hidden" name="business" value="vww@hvc.rr.com"/>
<input type="hidden" name="item_name" value="White Yetti Boots"/>
<input type="hidden" name="item_number" value="1470"/>
<input type="hidden" name="amount" value="10.00"/>
<input type="hidden" name="no_shipping" value="0"/>
<input type="hidden" name="no_note" value="1"/>
<input type="hidden" name="currency_code" value="USD"/>
<input type="hidden" name="weight" value=".1"/>
<input type="hidden" name="weight_unit" value="lbs"/>
<input type="hidden" name="lc" value="US"/>
<input type="hidden" name="bn" value="PP-ShopCartBF"/>
<input type="hidden" name="shopping_url" value="http://vwwagner.webng.com/Boots.html"/>
</form>
```

---

### Post by Dr Small on 2008-03-12
MySQL can be difficult at first, but the syntax is simple.
I have written a script that should add your content to a database. But here are a list of requirements.

A MySQL Database
Php
(Batch) Renaming all the .txt files to .html
Editing each txt file where:
```
<form action="https://www.paypal.com/cgi-bin/webscr"
```

And this will need to be changed to:
```
<form action="http://localhost/submit.php"
```
(Generic script location)


So, once you have created your database, you will need to save and execute this script on your localhost:
[php]
<?php

## CONNECT TO DATABASE ##
## YOU WILL NEED TO CHANGE THIS TO YOUR OWN INFO ###
$sqlhost = 'localhost';
$sqluser = 'rootl';
$sqlpass = '';
$db = 'inventory';
$tableprefix = 'item_';

$connect = mysql_connect($sqlhost, $sqluser, $sqlpass)
or die( "Could not connect to SQL server" );

mysql_select_db($db, $connect)
or die ("Could not open database:" .mysql_error() );


$mktable = "CREATE TABLE {$tableprefix}list (bussiness VARCHAR(1000), item_name VARCHAR(1000), item_number VARCHAR(1000), amount VARCHAR(1000), no_shipping VARCHAR(1000) no_note VARCHAR(1000), currency_code VARCHAR(1000), weight VARCHAR(1000), lc VARCHAR(1000), bn VARCHAR(1000), shopping_url VARCHAR(10000))";
mysql_query($mktable, $connect)
or die("Couldn't make table list<br />" . mysql_error());
echo "Table list created<br />";

[/php]

Now, take script 2 (submit.php) and place it on your localhost:

[php]
<?php

## CONNECT TO DATABASE ##
## YOU WILL NEED TO CHANGE THIS TO YOUR OWN INFO ###
$sqlhost = 'localhost';
$sqluser = 'rootl';
$sqlpass = '';
$db = 'inventory';
$tableprefix = 'item_';

$connect = mysql_connect($sqlhost, $sqluser, $sqlpass)
or die( "Could not connect to SQL server" );

mysql_select_db($db, $connect)
or die ("Could not open database:" .mysql_error() );


#LIST OF VARIBLES#
$bussiness = $_POST['business'];
$item_name = $_POST['item_name'];
$item_number = $_$POST['item_number'];
$amount = $_POST['amount'];
$no_shipping = $_POST['no_shipping'];
$no_note = $_POST['no_note'];
$currency_code = $_POST['currency_code'];
$weight = $_POST['weight'];
$weight_unit = $_POST['weight_unit'];
$lc = $_POST['lc'];
$bn = $_POST['bn'];
$shopping_url = $_POST['shopping_url'];



$mkdb = "INSERT INTO {$tableprefix}list (bussiness, item_name, item_number, amount, no_shipping, no_note, currency_code, weight, weight_unit, lc, bn, shopping_url) VALUES ('$bussiness', '$item_name', '$item_number', '$amount', '$no_shipping', '$no_note', '$currency_code', '$weight', '$weight_unit', '$lc', '$bn', '$shopping_url')" or die( mysql_error() );

mysql_query($mkdb, $connect) or die( mysql_error());

echo 'Data Submitted Sucessfully';

?>[/php]

Now, open up your html files (once the form action has been rewritten to point to submit.php) and click the submit button. Please do not get your hopes up, as it is not guaranteed to work the first time.

I have not tested it, but it should work in theory, an I have taken bits and pieces from different pieces of my scripts to make it. If you encounter an error, by all means please post it here so I can see what the problem is :)

Dr Small

---

### Post by volkswagner on 2008-03-13
Thanks for the response Dr Small.  I am reading W3C'S tutorials.  Perhaps I should have asked the following question.  What will be the solution for creating a dynamic inventory, on a shopping site?  I would like if the database will auto update as items are purchased.  If that is to difficult, I am open to a solution where I manually update for sold items.  Shall I be looking for software solution?

---

### Post by Dr Small on 2008-03-13
It wouldn't be too difficult, if you had it redirect to another page once the item was bought, which would remove the entry from the database, but I really don't have much expirence with shopping stuff. :(

---


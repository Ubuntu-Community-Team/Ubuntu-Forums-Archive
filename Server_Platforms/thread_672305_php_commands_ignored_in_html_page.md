---
title: "php commands ignored in html page?"
date: 2008-01-19
forum: Server Platforms
---

### Post by lucas4ce on 2008-01-19
Hi, apologies for novel below...

I have an html page with some require() php commands that seem to just get ignored.

the command is..
<td colspan="3"><?php require("header.php"); ?></td>
 
I'm simply trying to insert a standard header, but I get no result on the screen.  I changed from include to require to try and get some error messages but no joy, still no errors on the page.

Then I tried calling a php file that doesn't existing to force an error...

<td colspan="3"><?php require("notafile.php"); ?></td>

Still no error on the page, it runs fine just doesnt show the header.php info.

So far I'm trying to get some text from header.php into the table cell.  Figured that would be a good place to start but I've stumbled at the first hurdle.

I'm on Ubuntu 7.10 with Apache 2 and PHP5.  PHP and SSI is working, I can open .php files from the browser although only from [http://mydomain/header.php](http://mydomain/header.php) not locally for some reason.  I followed this advice [https://help.ubuntu.com/community/ServerSideIncludes](https://help.ubuntu.com/community/ServerSideIncludes) and get the ssi-test file to work fine.

I'm thinking its my config?  But no idea where to start

---

### Post by conjur3r on 2008-01-20
Maybe php has been configured to suppress error messages?  If this is the case, the error messages will still be logged in Apache's error log so check there.  Also try using **include**

---

### Post by jure1873 on 2008-01-20
try:
<?php
ini_set('display_errors', 'On');
error_reporting(E_ALL);
?>
<td colspan="3"><?php require("header.php"); ?></td>

do the .php files get parsed by php at all?

---


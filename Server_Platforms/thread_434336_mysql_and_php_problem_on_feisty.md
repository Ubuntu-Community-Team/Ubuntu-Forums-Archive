---
title: "mysql and php problem on feisty"
date: 2007-05-05
forum: Server Platforms
---

### Post by hardawayd on 2007-05-05
I really need some help in understanding why the following code will not work on my server but some packages that use adodb will work.  Here is the test code that is supposed to work but will not: I changed password to the correct one for root before running this.  What could keep these statements from working with mysql?  Thanks for any help.

<?php
   // in chroot use mysql host IP 127.0.0.1
   // if you want to use localhost put /etc/resolve.conf /etc/hosts file
   // to /webroot/etc directory
   $link = mysql_connect("127.0.0.1", "root", "password");
   mysql_select_db("mysql");

   $query = "show tables";
   $result = mysql_query($query);
   print "<h1>MySQL DB Test executed from ". $_SERVER['SCRIPT_NAME']. "</h1>\n";
   print "Script name: ". $_SERVER['SCRIPT_FILENAME'] ."<hr>\n";
   while ($line = mysql_fetch_array($result))
   {
      print "$line[0]<br>\n";
   }
    mysql_close($link);
    // try to open real /etc/passwd file
   print "<h1>Trying to open /etc/passwd file</h1>";
   try2OpenFile("/etc/passwd");
   // try to open real /etc/hosts file
   print "<h1>Trying to open /etc/hosts file</h1>";
   try2OpenFile("/etc/hosts");

function try2OpenFile($file){
   $f = @fopen($file, "r");
   if ( !$f ) { print "Error - Cannot open file <b>".$file."</b>"; return;}
   echo "<hr>File: $file<hr><pre>";
   while ( $line = fgets($f, 1000) ) {
   print $line;
   }
   echo "</pre>";
}
?>

---

### Post by kidders on 2007-05-06
Hi there,

There could be any number of reasons why this code fails. Could you post some details ... error messages/script output/etc?

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---


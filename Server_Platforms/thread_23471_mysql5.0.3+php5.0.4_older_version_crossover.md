---
title: "mysql5.0.3+php5.0.4 older version crossover?"
date: 2005-04-02
forum: Server Platforms
---

### Post by 11evele on 2005-04-02
hi!  ok so i got these babies mysql5.0.3 beta and php5.0.4 running.
i initially set them up because i wanted to learn php for a site im working on with my roommate.  im reading their sites and while i have never used either of these before i read the new versions are a bit different than previous releases.  i just ordered the book "build your own database driven website using php and mysql" by kevin yank of sitepoint, but now im afraid some mysql things won't crossover...am i wrong?  

can anyone recommend a site with a basic umm php script(?) that will interact with mysql to see if its doing its thing?  

i see in php info all the mysql info is there but well like i said this is new space monsters for me so i dont know what that really means....

all the best!
nick

---

### Post by CrustyDOD on 2005-04-02
Simple script to connect to mysql with php:

[PHP]<?
$connect = mysql_connect("localhost", "USERNAME", "PASSWORD") 

or die("Can't connect: " . mysql_error());

mysql_select_db("DATABASE", $connect);
?>[/PHP]

save this script as php file and try it! Before you try it, make sure you change USERNAME, PASSWORD and DATABASE...

If you don't get any errors its working else not :)

---

### Post by 11evele on 2005-04-03
> **CrustyDOD]Simple script to connect to mysql with php:

[PHP]<?
$connect = mysql_connect("localhost", "USERNAME", "PASSWORD") 

or die("Can't connect: " . mysql_error()) said:**
> 

save this script as php file and try it! Before you try it, make sure you change USERNAME, PASSWORD and DATABASE...

If you don't get any errors its working else not :)

well i didnt get any errors...just a blank page..this is good yes?! :)  thanks!

---

### Post by CrustyDOD on 2005-04-03
[QUOTE="11evele"]well i didnt get any errors...just a blank page..this is good yes?![/QUOTE] 

Yes, that means that the connection to mysql was a success!

---


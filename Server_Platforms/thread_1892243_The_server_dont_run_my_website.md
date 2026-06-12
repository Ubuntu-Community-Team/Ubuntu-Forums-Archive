---
title: "The server dont run my website"
date: 2011-12-07
forum: Server Platforms
---

### Post by barezi6 on 2011-12-07
Hi everyone

I created a website with database, on my local machine, using xampp for localhost database, and the webiste works great, now i imported the mysql database to the server and the website code to var/www, but it dont appear on my browser, i use ubuntu 8.04 LTS, the server works great, i only can see something on the browser, if i use the index.html, like it works or something that i write, i really dont know why it dont work, my website conf.php have the right configuration...
$MYSQL['host'] = 'localhost';
$MYSQL['user'] = 'root';
$MYSQL['pass'] = 'mypass';
$MYSQL['data'] = 'network';
$con = @mysql_connect($MYSQL['host'], $MYSQL['user'], $MYSQL['passs']);

i have some doubt if now using the database on the server the host name is localhost like when i used xampp, only need one more help to complete my server with a website to use on the internet.
Thanks for all the help, users :)

---

### Post by dstnvns on 2011-12-07
I didn't see a DB name in your config. This was in one of my config.php files: 

$cfg["db_type"] = $dbtype;
$cfg["db_host"] = $dbserver; 
$cfg["db_name"] = **$dbname**; 
$cfg["db_user"] = $dbuser;
$cfg["db_pass"] = $dbpass;

Connect($cfg["db_host"], $cfg["db_user"], $cfg["db_pass"], $cfg[**"db_name"**]);

Yours did show a DB name, 'data=network', but didn't have the variable in the $con string.

$MYSQL['host'] = 'localhost'; 
$MYSQL['user'] = 'root';
$MYSQL['pass'] = 'mypass';
**$MYSQL['data'] = 'network';**
$con = @mysql_connect($MYSQL['host'], $MYSQL['user'], $MYSQL['passs']) **NO db name**;

i have some doubt if now using the database on the server the host name is localhost like when i used xampp, only need one more help to complete my server with a website to use on the internet.
Thanks for all the help, users :)[/QUOTE]

---

### Post by barezi6 on 2011-12-07
> **dstnvns said:**
> I didn't see a DB name in your config. This was in one of my config.php files: 

$cfg["db_type"] = $dbtype;
$cfg["db_host"] = $dbserver; 
$cfg["db_name"] = **$dbname**; 
$cfg["db_user"] = $dbuser;
$cfg["db_pass"] = $dbpass;

Connect($cfg["db_host"], $cfg["db_user"], $cfg["db_pass"], $cfg[**"db_name"**]);

Yours did show a DB name, 'data=network', but didn't have the variable in the $con string.

$MYSQL['host'] = 'localhost'; 
$MYSQL['user'] = 'root';
$MYSQL['pass'] = 'mypass';
**$MYSQL['data'] = 'network';**
$con = @mysql_connect($MYSQL['host'], $MYSQL['user'], $MYSQL['passs']) **NO db name**;

i have some doubt if now using the database on the server the host name is localhost like when i used xampp, only need one more help to complete my server with a website to use on the internet.
Thanks for all the help, users :)

i dont post the complete sql connection, but i know that my code works good because we run well on my localhost (xampp)

it is the config

$MYSQL['host'] = 'localhost';
$MYSQL['user'] = 'root';
$MYSQL['pass'] = 'mypass';
$MYSQL['data'] = 'network';
$con = @mysql_connect($MYSQL['host'], $MYSQL['user'], $MYSQL['passs']);
$dbError = $con ? false : true;
$db = @mysql_select_db('network', $con);
$dbError = $db ? false : true;

i have the full permissions of the code that i send to the server, what i can test or do to get more informations about the problem?, i tested some things but didnt have results

---

### Post by satanselbow on 2011-12-07
> **barezi6 said:**
> ...

$MYSQL['**pass**'] = 'mypass';

... $con = @mysql_connect($MYSQL['host'], $MYSQL['user'], $MYSQL['**passs**']);
...


The typo would cause a problem and may fail silently - or is that just in this post?

Have you looked at your apache / mysql logs?

---

### Post by barezi6 on 2011-12-07
> **satanselbow said:**
> The typo would cause a problem and may fail silently - or is that just in this post?

Have you looked at your apache / mysql logs?

is just on this post, the code of the website works normally on xampp, i think that my problem is because some config on the server or apache etc. i installed phpmyadmin to var/www to can control the database with GUI, from anywhere, and then i installed the database and put all the code files on the var/www, and dont show nothing,

Have you looked at your apache / mysql logs?
no, if shoud look, what i need to do?

---

### Post by brighty22 on 2011-12-07
Change '*$con = @mysql_connect(...*' to '*$con = mysql_connect(...*' (no @ symbol) and put '*error_reporting(-1);*' at the top of your code. Post any error messages you get when visiting the page.

---

### Post by barezi6 on 2011-12-07
> **brighty22 said:**
> Change '*$con = @mysql_connect(...*' to '*$con = mysql_connect(...*' (no @ symbol) and put '*error_reporting(-1);*' at the top of your code. Post any error messages you get when visiting the page.

ohh, i am thinking that the pass error is only on this post but no, it is on the code,problem resolved, thanks very much for all the help, ubuntu community is great all the help was very important for me, thanks you community :)

---


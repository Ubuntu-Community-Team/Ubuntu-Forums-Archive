---
title: "Server update from 14.04 to 16.04 - Dissaster"
date: 2016-08-01
forum: Server Platforms
---

### Post by Ruxiol on 2016-08-01
Hello ubuntu :)

Guys, im no expert, but i can manage to setup server and stuff.... so please help if you can

On my ubuntu server with RAID mirror,  it had apache, mysql, php... all for webserver that i need to run: 2 joomla sites, 1 discourse forum, and owncloud!

i dont know why i did upgrade to 16.04.1 but after if did it all hell break lose!

Discourse forum, becuse its using all in his container its working with no problem

but owncloud and joomla sites are dead... 

1st joomla site is showing
setStart($startTime, $startMem)->mark('afterLoad') : null; // Instantiate the application. $app = JFactory::getApplication('site'); // Execute the application. $app->execute(); 

2nd joomla site
Error displaying the error page: Application Instantiation Error: Could not connect to MySQL.

and 

owncloud instance its just showing 
Internal Server Error
The server encountered an internal error and was unable to complete your request.
Please contact the server administrator if this error reappears multiple times, please include the technical details below in your report.
More details can be found in the server log.

I know it has something with php and mysql but im not sure what to do :)

i tried to reinstall mysql, php, but no luck

any of you good guys want to help me fix this damn thing? i dont want to build it from scratch, because i have 10 users on owncloud and much data to be synced.

thank you :)

---

### Post by Graham_Willis on 2016-08-01
[quote="Ruxiol"]any of you good guys want to help me fix this damn thing? i dont want to  build it from scratch, because i have 10 users on owncloud and much  data to be synced.[/quote]

It's why it's preferred to have OS on an independent disk. This way if you want to update, you just syncing disks to have a backup and upgrade only then. If something breaks, you can replace disks and gain much shorter downtime.

What you should do - you should do exactly what the third case tells you. That is, check the error logs. Also, your first Joomla site seems to behave a bit as if it wasn't interpreted as PHP code at all, so try to put a file test.php with something like that:

```

<?php
echo "Good morning\n";
?>

```

correct the permissions to this file, and check if it displays the message at all. Also, what's the output of ls -la on the directory which contains the files of this application? And does it display the actual contents in addition to error message you quoted? If yes, it's most likely about PHP version being changed. In this case, the easy solution's to just turn off these warnings. Confirm that this is the case and I'll tell you how. PHP error logs as worth checking, as in all the cases (I believe you have them in **/var/log/php_errors.log**).

As for the second case, just try to connect to the database manually. If you can't, check if the database exists, change the password and try with a new one, if it doesn't work check MySQL error logs ( probably** /var/log/mysql.err **).

As for the third case, we'd really have to take a look at what's in error logs with relevance to the domain generating ISE. The message itself isn't saying much.

---


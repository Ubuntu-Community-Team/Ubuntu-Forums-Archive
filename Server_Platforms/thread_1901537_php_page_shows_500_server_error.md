---
title: "php page shows 500 server error"
date: 2011-12-28
forum: Server Platforms
---

### Post by vernonh76 on 2011-12-28
I have an issue with 10.04 LTS Ubuntu with LAMP installed.  When a .php file is supposed to be shown on the internet, I get a 500 error.  Here is the error.log file.  Any help would be appreciated.  The website is the only one on the server and in the home directory.  


```
[Wed Dec 28 18:04:55 2011] [error] [client 98.91.25.46] PHP Warning:  mysql_pcon                                                                              nect(): Access denied for user 'jack'@'localhost' (using password: YES) in /home                                                                              /jack/Connections/cifc_clients.php on line 9
[Wed Dec 28 18:04:55 2011] [error] [client 98.91.25.46] PHP Fatal error:  Access                                                                               denied for user 'jack'@'localhost' (using password: YES) in /home/jack/Connecti                                                                              ons/cifc_clients.php on line 9
[Wed Dec 28 18:19:53 2011] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/                                                                              conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Wed Dec 28 18:19:54 2011] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.11                                                                               with Suhosin-Patch configured -- resuming normal operations
[Wed Dec 28 18:20:01 2011] [error] [client 98.91.25.46] File does not exist: /ho                                                                              me/jack/favicon.ico
[Wed Dec 28 18:20:03 2011] [error] [client 98.91.25.46] script '/home/jack/admin                                                                              /services_clothing_1.php' not found or unable to stat, referer: [http://cifc.dynd](http://cifc.dynd)                                                                              ns.org/
[Wed Dec 28 18:20:03 2011] [error] [client 98.91.25.46] File does not exist: /ho                                                                              me/jack/favicon.ico
[Wed Dec 28 18:20:06 2011] [error] [client 98.91.25.46] File does not exist: /ho                                                                              me/jack/favicon.ico
[Wed Dec 28 18:20:07 2011] [error] [client 98.91.25.46] PHP Warning:  mysql_pcon                                                                              nect(): Access denied for user 'jack'@'localhost' (using password: YES) in /home                                                                              /jack/Connections/cifc_clients.php on line 9, referer: [http://cifc.dyndns.org/](http://cifc.dyndns.org/)
[Wed Dec 28 18:20:07 2011] [error] [client 98.91.25.46] PHP Fatal error:  Access                                                                               denied for user 'jack'@'localhost' (using password: YES) in /home/jack/Connecti                                                                              ons/cifc_clients.php on line 9, referer: [http://cifc.dyndns.org/](http://cifc.dyndns.org/)
[Wed Dec 28 18:20:09 2011] [error] [client 98.91.25.46] File does not exist: /ho                                                                              me/jack/favicon.ico
[Wed Dec 28 18:20:14 2011] [error] [client 98.91.25.46] File does not exist: /ho                                                                              me/jack/<, referer: [http://cifc.dyndns.org/](http://cifc.dyndns.org/)
[Wed Dec 28 18:20:14 2011] [error] [client 98.91.25.46] File does not exist: /ho                                                                              me/jack/favicon.ico
[Wed Dec 28 18:32:00 2011] [error] [client 98.91.25.46] File does not exist: /ho                                                                              me/jack/favicon.ico
[Wed Dec 28 18:32:03 2011] [error] [client 98.91.25.46] File does not exist: /ho                                                                              me/jack/favicon.ico
[Wed Dec 28 18:32:08 2011] [error] [client 98.91.25.46] PHP Warning:  require_on                                                                              ce(../Connections/cifc_clients.php): failed to open stream: No such file or dire                                                                              ctory in /home/jack/index.php on line 1
[Wed Dec 28 18:32:08 2011] [error] [client 98.91.25.46] PHP Fatal error:  requir                                                                              e_once(): Failed opening required '../Connections/cifc_clients.php' (include_pat                                                                              h='.:/usr/share/php:/usr/share/pear') in /home/jack/index.php on line 1
[Wed Dec 28 18:32:13 2011] [error] [client 98.91.25.46] File does not exist: /ho                                                                              me/jack/favicon.ico
[Wed Dec 28 18:32:18 2011] [error] [client 98.91.25.46] PHP Warning:  require_on                                                                              ce(../Connections/cifc_clients.php): failed to open stream: No such file or dire                                                                              ctory in /home/jack/index.php on line 1
[Wed Dec 28 18:32:18 2011] [error] [client 98.91.25.46] PHP Fatal error:  requir                                                                              e_once(): Failed opening required '../Connections/cifc_clients.php' (include_pat                                                                              h='.:/usr/share/php:/usr/share/pear') in /home/jack/index.php on line 1
[Wed Dec 28 18:32:18 2011] [error] [client 98.91.25.46] File does not exist: /ho                                                                              me/jack/favicon.ico
[Wed Dec 28 18:32:28 2011] [error] [client 98.91.25.46] File does not exist: /ho                                                                              me/jack/favicon.ico
[Wed Dec 28 18:32:50 2011] [error] [client 98.91.25.46] File does not exist: /ho                                                                              me/jack/favicon.ico
[Wed Dec 28 18:36:28 2011] [error] [client 98.91.25.46] File does not exist: /ho                                                                              me/jack/favicon.ico
[Wed Dec 28 18:36:29 2011] [error] [client 98.91.25.46] PHP Warning:  mysql_pcon                                                                              nect(): Access denied for user 'jack'@'localhost' (using password: YES) in /home                                                                              /jack/Connections/cifc_clients.php on line 9, referer: [http://cifc.dyndns.org/](http://cifc.dyndns.org/)
[Wed Dec 28 18:36:29 2011] [error] [client 98.91.25.46] PHP Fatal error:  Access                                                                               denied for user 'jack'@'localhost' (using password: YES) in /home/jack/Connecti                                                                              ons/cifc_clients.php on line 9, referer: [http://cifc.dyndns.org/](http://cifc.dyndns.org/)
[Wed Dec 28 18:36:29 2011] [error] [client 98.91.25.46] File does not exist: /ho                                                                              me/jack/favicon.ico
```

---

### Post by SeijiSensei on 2011-12-29
Did you actually read that log?  Most of the errors are self-explanatory.  Your script can't log into the MySQL server with the credentials you gave it; one of the directory references contains an erroneous space ("/ho me/jack"); the required include script "../Connections/cifc_clients.php" can't be found; and, Apache also can't find "services_clothing_1.php".

---

### Post by vernonh76 on 2011-12-29
I am not the one doing the php programming, and really know nothing about it.  I just set up the server, with LAMP, and didn't know if maybe it was a server error.  Thanks for the help.  He was using the wrong id to log in.

---

### Post by brighty22 on 2011-12-29
There really are some very basic errors in that log... for the future, it may benefit him to put

[PHP]error_reporting(-1);[/PHP]

at the top of all his scripts - that will show all the errors... unless apache gives up and throws 500.

---


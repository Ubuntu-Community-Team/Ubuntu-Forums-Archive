---
title: "DVWA Ubuntu Server 14.04.1 LTS"
date: 2015-02-21
forum: Server Platforms
---

### Post by CrAzY12 on 2015-02-21
So I am trying to install DVWA and I am having trouble connecting to mysql database through dvwa. The web server and DVWA is up and running but when I try to set up the Database I receive the error:

> could not connect to the database - please check the config file

Notes:
-I have changed /etc/mysql/my.cnf file so that the bind address = 10.10.20.100 is equal to the db-server ; '10.10.20.100' in /htdocs/dvwa/config/config.inc.php

-/htdocs/dvwa/config/config.inc.php: Attachment 3
-Error of database : Attachment 2
- netstat -vln ; Attachment 1

---

### Post by MAFoElffen on 2015-02-22
Default Listening port for MySql is 3306... Please post your my.cnf file... to show what you have the bind address mapped to in the "bind=xxxx" line
When you find that, match that bind port in your DVWA config line where you have:
```

$_DVWA[ 'db_port' ] = '[COLOR=#ff0000]5432[/COLOR]';

```
to match the port that was in your my.cnf file.

What I see in your netstat output is... somewhat confusing (not what it should be).

But what is not right off the bat, is something in your DVWS config. Where it says:
```

$_DVWA[ 'db_password' ] = '[COLOR=#ff0000]p@ssw0rd[/COLOR]';

```
Is the defualt installed password that is their default setting, in the defalut config file (just a placeholder, for you to change). You need to change that to what your current password is for MySQL.

---

### Post by CrAzY12 on 2015-02-22
Thank you for helping out again!
And I have changed my DVWA config file to:

```
 [ 'db_port' ] = '3306' 
```

*Or did you meant to change my.cnf to port 5432?
 
Same port as my.cnf file. I also have changed my bind address in my.cnf file to 10.10.20.100 as you suggested earlier. 

I have changed my password for DVWA and if I understood you correctly, my DVWA password must be the same password as mysql password correct? Now I am not to familiar with mysql just yet but when I log into mysql as root I do use the same password as I put into my DVWA, would this suggest my password are now the same?

I have included my.cnf file & netstat -vln screenshots but seems like netstat -vln is the same as last time.

When you said my netstat -vln connections are off what do I need to look for? 
*I do have another interface up 192.168.1.X but will be turned off once I get everything running(had to install everything first)

SOLVED: 
I set the below config.inc.php file to my 10.10.20.100(Which is my DVWA ip address) but it needs to be set to localhost (which was the default) and I changed back my.cnf bind address = localhost (which was back to the default) so the only thing I changed was the port in the config.inc.php file to 3306 and PROBLEM SOLVED

[COLOR=#000000]$_DVWA[ 'db_server' ] = '[/COLOR][COLOR=#ff0000]localhost[/COLOR][COLOR=#000000]';




[/COLOR]

---


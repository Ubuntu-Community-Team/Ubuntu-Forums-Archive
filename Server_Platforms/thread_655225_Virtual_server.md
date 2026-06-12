---
title: "Virtual server"
date: 2008-01-01
forum: Server Platforms
---

### Post by rockinlinux on 2008-01-01
I need to to know how to set up a test server on my computer so i can test my php scripts before uploading them to my actual web server. I have never even used a test server before so please be kind in the explaining. :) 

i need it to be able to have stuff like phpbb and mediawiki installed so i can test my layouts before putting them on the net. 

so i will have to have php and Mysql

thanks for the help. 

and happy 2008 to everyone!!! :)

---

### Post by BL00dFox on 2008-01-01
Sure, thats easy! You need to install a LAMP stack (Linux, apache, mysql and php) on ur computer then you will be ready to go. Do this thru the terminal:
```
$ sudo aptitude install apache2
$ sudo aptitude install php5
$ sudo aptitude install mysql-server
$ sudo aptitude install php5-mysql
```

Cheers

EDIT: I copied and pasted this from another thread, might help you:



Step 1: Get a functional LAMP stack.

To get a 'LAMP' stack running (Linux Apache Mysql Php), you just install the packages "apache2", "php5" and "mysql-server". You can do this using Synaptic (Ubuntu) or Adept (Kubuntu), or on the command line:
Code:

$ sudo aptitude install apache2
$ sudo aptitude install php5
$ sudo aptitude install mysql-server
$ sudo aptitude install php5-mysql

Once these are installed, you should be able to test it by pointing your web-browser to:
[http://localhost/](http://localhost/)

You should see a web-page, not an error message. (You may see a simple web-dir listing with "apache2-default" in it... that's normal.) To test if PHP is working properly, just create a simple test page. For instance, create a file:
Code:

$ sudo nano /var/www/test.php

And put in this text:
Code:

<html>
<head>
  <title>Test Page</title>
</head>
<body>
Test page<br />
<?php 
	echo 'If you can see this text, then PHP is working.';
?>
</body>
</html>

Then go to [http://localhost/test.php](http://localhost/test.php)
If you see the "...then PHP is working" message then all is well.

Since your PHP/MySQL interface will eventually be world-accessible, it makes sense to put some security in place. By default MySQL starts with no password, so you should certainly set one:
Code:

$ mysqladmin -uroot password 'new-password'

(Note: if you're ever having trouble coming up with good passwords, install and run a simple commandline program called "pwgen" ... it will suggest strong passwords that are reasonably easy to remember.)


Step 2: Make sure you can access your webserver.

A common stumbling block in getting a LAMP stack fully functional is that port 80 is blocked. This may be because the Internet Service Provider (ISP) is blocking it, or because your router's firewall is blocking it. To test whether or not you are blocked, first find out your world-facing ("external") IP address. You can do this in any number of ways, such as visiting sites like:
[http://www.ipaddressworld.com/](http://www.ipaddressworld.com/)

Then test your setup by using a web browser to check:
[http://localhost/](http://localhost/)
[http://xxx.xxx.xxx.xxx/](http://xxx.xxx.xxx.xxx/)

(Where the x's are your IP address, of course.) If you see the same apache page in both cases, then everything is working. If in the second case you get an erorrt, then somewhere along the line port 80 is being blocked. It could be your ISP, or the firewall in your router (if any).

---

### Post by rockinlinux on 2008-01-01
thanks so much!!! :)

---

### Post by BL00dFox on 2008-01-01
> **rockinlinux said:**
> thanks so much!!! :)

No problem, happy to help =]

---

### Post by rockinlinux on 2008-01-01
so where am i going to put my files?

---

### Post by BL00dFox on 2008-01-01
You put your web files into:
/var/www/


Then you can point your browser to localhost then it will load.

---

### Post by rockinlinux on 2008-01-01
ok so i got this all working but im not sure how to configure my mysql databases...by this i mean how do i make them? sorry im used to a server with something like cpanel .

cheers :)

---

### Post by wefadu on 2008-01-06
Hello!

I am all new here in these forums, so I hope I do this correctly.

Currently, I also try to set up a LAMP environment. Everythings installed and running stand-alone.

Only it seems I cannot get a connection from php to mysql: A access of a mysql DB (which does exist) via php fails. As described above (2), I tried whether port 80 is accesible via my IP address, which fails. Localhost does work. Disabling the firewall on my computer does not change this. There is still the firewall of my router and of course, I do not know what my internet supplier is doing. 

My question: Can I get this running without having my computer open to the internet? I want to use this only localy.

thanks for any help in advance

---

### Post by rockinlinux on 2008-01-06
sure you can! Let me make sure i understand what you are doing here. You have a computer that you want to set up with a LAMP stack that will go on your local network for testing?

What i am trying to do is just set up my notebook that i use everyay also as a server so i can test php beofre i put it on my real server.

please give me more details about what you are doing, and if you want a fast reply from me post at my site in my signature.

cheers,

nate

---

### Post by johnwillis on 2008-01-06
It is either worth you installing PHPmyadmin (do this by googling the program name) or better still as you are actually sitting at the machine install the official MySQL GUI tools.

In Synaptic (the package manager) do a search for "mysql" somewhere in the list you will come up with "MySQL-GUI-TOOLS" or something similar...

The compontents you are interested in are:

MySQL Administrator

MySQL Query Browser

The first will allow you to set up databases, users, etc

The second allows you to test your SQL queries before going live :)

Hope this helps...

John

---

### Post by wefadu on 2008-01-08
Hi

thank you for your comments!

Here is some more details on what I want to do: 

My intention is run run a digital image database called 'linpha'. This is designed to share images via internet and therefore uses LAMP. I want to use it localy on my own computer alone though. My 'Network' is rather small: A PC conneceted via Ethernet to a Rooter which connects to my internet supplier via a DSL ppp connection. That's it. 

And here, I suspect, my trouble starts: As far as I know connections to the sql - DB server can be established in two ways, internaly and through some network connections coming into the computer from outside. Probably, the first way works, the second not. This I assume because mysql admin does work, while I fail to log into phpmyadmin (for remote administration). An additional hint is that a php skript cannot access the database: Accessing this file with my browser


<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0//EN">
<html><head><title>myphp</title><body>
<?php
$connID = @mysql_connect("localhost", "newuser", "uranus");
if(!$connID) {
  echo "<p>no connection to DBserver</p>\n";
}
else {
  echo "<p>connection to DBserver established</p>\n";
}
?>
</body></html>

results in 'no connection to DBserver'.

Also, there are some users, who cannot log into sql. I created several test users:

mysql> SELECT user, host FROM mysql.user;
+------------------+-----------+
| user                 | host      |
+------------------+-----------+
| root                  | 127.0.0.1 | 
| debian-sys-maint | localhost | 
| testuserA        | localhost | 
| root                  | localhost | 
| root                  | pepe      | 
| testuserB        | pepe      | 
+------------------+-----------+
6 rows in set (0.00 sec)

mysql> 

I can logon as root and as testuserA, but not as testuserB with host 'pepe', which is my computers name. So I suspect there is some kind of routing issue I do not understand here.

I am sorry this is getting pretty long. Maybe I should start a new post? I thought this was related to my questions but I am unsure now, and new here.
thanks!

---

### Post by freymann on 2008-01-08
> **wefadu said:**
> 
Accessing this file with my browser

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0//EN">
<html><head><title>myphp</title><body>
<?php
$connID = @mysql_connect("localhost", "newuser", "uranus");
if(!$connID) {
  echo "<p>no connection to DBserver</p>\n";
}
else {
  echo "<p>connection to DBserver established</p>\n";
}
?>
</body></html>

results in 'no connection to DBserver'.


 As shown in reply #2, you did call this script

test.php

 I hope? If it ends in HTML the PHP section won't be parsed.

 Otherwise, you just need to set up permissions in mysql.

---

### Post by rockinlinux on 2008-01-09
im still a little lost on what you are trying to do. You are trying to set up a image database on your computer but your not going to share it online? if this is the case then may i ask why you are doing this? and if not are you sure that your ISP keeps port 80 open?

I would like to help you more but you might get better faster help if you start a new topic.

thanks :)

---

### Post by wefadu on 2008-01-09
Hi

thank you for your replies!

The .php extension was a good point, but I checked it, it was alright. 

Could you help me how to set up the permissions correctly? Is there something to be set up around the users besides username, host and password? How about uranus, as called in the skript? This one does not exsist at all, so kind of an anomymous login. I wonder why testuserB on host pepe cannot log on while it works with testuserA on host localhost. I would have assumed all this is just the same but obviouly its not, and I do not understand the details here.

I am trying this because of this Linpha programm, which I want to use locally only, as I do not want to share images. I think some features of Linpha are worth trying for me though. According to my test with my IP adress I do not belive port 80 is open by my ISP.

I'll put this on a different post and insert a link here, but have not enough time today

thanks!:)

---

### Post by freymann on 2008-01-09
> **wefadu said:**
> 
Could you help me how to set up the permissions correctly?


 I usually log into mysql from the command line

```

mysql -uroot -ppassword mysql

```

 and enter something like this to allow a username/password access to a specific database:

```

GRANT ALL PRIVILEGES ON dbname.* TO 'yourusername'@'localhost' IDENTIFIED BY 'yourpassword'; 

```

and then you have flush privleges:

```

flush privileges;

```

and exit.

You may find this url useful too:

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---


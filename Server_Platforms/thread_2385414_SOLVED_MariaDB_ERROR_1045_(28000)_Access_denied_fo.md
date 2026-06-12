---
title: "SOLVED: MariaDB ERROR 1045 (28000): Access denied for user 'user'@'localhost'"
date: 2018-02-20
forum: Server Platforms
---

### Post by adriaan4 on 2018-02-20
Wanted to install wordpress on Raspbian Stretch with Apache. 

MySQL (MariaDB) and Apache and PHP were already installed, I experienced a lot of trouble wiht the database access. 

This helped me, I wish I found it faster:

Create user:
```
SET PASSWORD FOR wordpressuser= PASSWORD(&#8220;mypassword&#8221;);
```

You may need not only to do
```
GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpressuser'@'%' IDENTIFIED BY 'mypassword'; 
```

But also 

```
GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpressuser'@'localhost' IDENTIFIED  BY 'mypassword'; 
```

And **do not forget** to: 
```
flush privileges; 
```

By the way, I followed this fast manual, thanks again: (not for absolute beginners)
[http://mitchtech.net/wordpress-on-raspberry-pi/](http://mitchtech.net/wordpress-on-raspberry-pi/)

---

### Post by LHammonds on 2018-02-20
You should understand the reasoning behind the three different contexts in which to grant access.

The most-secure method is to grant the user account and limit to just being able to login on the same database server which is the username@localhost

However, that is ONLY if your application is also on the same machine.  This prevents applications or anything trying to use that account to login remotely.

If you are in a distributed environment where you have separate application and database servers, then you need to specify the calling server that will be accessing the database remotely in your grant statement.  You can do this by specifying the IP address or the name of the server if your database server an resolve the name to the IP...such as username@192.168.0.2 or username@srv-mysql.  This will allow that username to login to the server remotely from that specific machine only.  This prevents hackers that find out the username/password from being able to make use of it anywhere else other than that machine.

The least restrictive option is the "from anywhere" grant statement such as username@% which means that username/password can be logged in from any device in the world without restriction.  This option should NOT be used in a production scenario.

Here are some real-world examples:

[LIST]
[*][Configure database for MediaWiki]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=241#p583") 
[*][Configure database for NextCloud]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=239#p563") 
[*][Configure database for ownCloud]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=234#p537") 
[*][Configure database for phpBB]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=230#p517")
[*][Configure database for qdPM](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=222#p511) 
[*][Configure database for WordPress]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=231#p524") 
[/LIST]

LHammonds

---

### Post by adriaan4 on 2018-04-04
Hey mr Hammonds, that is very helpful. Thanks for the resources!

---


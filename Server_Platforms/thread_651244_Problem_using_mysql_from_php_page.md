---
title: "Problem using mysql from php page"
date: 2007-12-27
forum: Server Platforms
---

### Post by zazuzimbo on 2007-12-27
Hello,

I have a small network with one server and a few machines, linux and windows. The server provides a page wich is php + mysql.

I installed Ubuntu Server 7.10 on another machine, and I am trying to make it run the same page for all my network. PHP and MySQL are good on this **newserver**, as I have tested following instructions on help.ubuntui.com. I have also instaled PHPMyAdmin and tested it.

I copied all the page's files and the database it uses from the working server to my new one. Now I access my page using **[http://newserver/mypage](http://newserver/mypage)**.

But it won't get any data from the database. It gives me this error (spit on my page):
```

Warning: mysql_pconnect() [function.mysql-pconnect]: Lost connection to MySQL server at 'reading initial communication packet', system error: 111 in /test/mypage/db_utils.php on line 224

```

The file db_utils.php contains a funtion called when my page opens. The line that gives the erro is like:

```

$bd = mysql_pconnect("newserver.foomydomain",
     $_SESSION["TheUser"],
     $_SESSION["TheWord"]);

```

The working server is DNS server for newserver. I am not sure if I should put something on it for the MySQL too.

I don't know for sure what else is relevant, so please ask. Any help pointers are good.

Regards.

---

### Post by jtc on 2007-12-27
If I'm not mistaken mysql-error 111 is some kind of access denied. Does the log-file of your mysql-server tell you anything interesting?

Then perhaps you could clarify for me exactly what is running where? Is the MySQL-server running on the same server as the php-script? If so, then my spontaneous guess would be that php is trying to make a network connection while MySQL is listening on a socket.

---

### Post by zazuzimbo on 2007-12-28
Both the PHP and the database are running on **newserver**, with Ubuntu server 7.10.

My goal is to make this **newserver** run completely independent from the oldserver (wich I called "running server"). Now this old server is DNS server for the **newserver**.

I have suceded in running this page on the newserver, using the database on the old server. Works nicely. When I change the call to **mysql_pconnect** to open the data base on the newserver, it gives the error I show.

:oops: What is the log file of the mysql-server? _/var/log/mysql.err_? This one is empty (my disk is not full). I found no other file (looked on [http://dev.mysql.com/doc/refman/5.1/en/log-files.html](http://dev.mysql.com/doc/refman/5.1/en/log-files.html)).

Where should I look for the error code? On mysql.org all error are above 1000 or above 2000 ([http://dev.mysql.com/doc/refman/5.1/en/error-messages-server.html](http://dev.mysql.com/doc/refman/5.1/en/error-messages-server.html)).
On php.net, for the funciont mysql-pconnect there is no info. :(

What should I check to make sure that the SQL database server on my **newserver** is all setup correctly to work with PHP? Is there anything I must do in DNS, ports I should open, sockets...? I dunno.

I am a littlle bit lost on what to do.

Thanks in advance.

---

### Post by jtc on 2007-12-28
Well, most of the settings; including logging, what to listen for, etc are done in /etc/mysql/my.conf

Actually I have a few educated guesses. How about seeing if we can get things working from those, and then from there proceed to the how and why?

Will it work for you if you change the php-code from connecting to "newserver.foomydomain" and instead connect towards "localhost" and/or "127.0.0.1"?

---

### Post by zazuzimbo on 2008-01-03
> **jtc said:**
> 
Will it work for you if you change the php-code from connecting to "newserver.foomydomain" and instead connect towards "localhost" and/or "127.0.0.1"?

:) Yes, it works! Both ways. Thank you!

I am thinking now why it was done that way?

If I keep running the mysql server on the same machine as the apache server, will I ever need to change that again?

Happy new year to all people here, and to Ubuntu!! :popcorn:

---

### Post by andol on 2008-01-03
> **zazuzimbo said:**
> 
I am thinking now why it was done that way?

Default when you install MySQL (at least in Ubuntu) is for it to listen only to your  loopback interface. When you connect towards newserver.foomydomain you tried, in short, to connect thru your normal network interface; the one also accessible to other computers.

(Well, actually besides the loopback interface it also listens on a socket. If you are curious, feel free to look it up.)

> **zazuzimbo said:**
> 
If I keep running the mysql server on the same machine as the apache server, will I ever need to change that again?

As long as MySQL and Apache/PHP is running on the same machine it should work to connect thru the loopback interface. If you decide that you want to be able to connect to the MySQL-server from another machine then you'll need to take a look at the option "bind-address" in /etc/mysql/my.cnf

---


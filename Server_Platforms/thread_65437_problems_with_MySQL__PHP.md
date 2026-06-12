---
title: "problems with MySQL / PHP"
date: 2005-09-14
forum: Server Platforms
---

### Post by Burke on 2005-09-14
I followed all the steps in the Ubuntu guide to install a server.

I installed apache2, then php4, then mysql.  (plus all the bindings that are on the guide as well)

Each of them works very well... on their own.  When I try to do a mysql query from a PHP script, it takes up to a minute to do the query (This was a simple query -- "SELECT pass FROM users" -- with one record, currently). It is worth noting that phpMyAdmin performs just as badly.

I thought this was because I am using a Pentium 150MHz, but in the mysql monitor, through ssh, this was completed in well under a second.

What could cause this considerable lag between PHP and  MySQL?  Could it be a problem with Apache and MySQL instead?

Whatever the answer, thank you so much for taking the time to help me :)
Burke

---

### Post by Burke on 2005-09-14
Just to clarify,

Apache works fine
MySQL works fine
PHP works fine

MySQL queries with PHP running on Apache don't.

Could this be a problem in my.cnf? 

Thanks for the help/

Burke

---

### Post by GrumpySimon on 2005-09-16
[QUOTE=Burke]Just to clarify,

Apache works fine
MySQL works fine
PHP works fine

MySQL queries with PHP running on Apache don't.

Could this be a problem in my.cnf? 

Thanks for the help/

Burke[/QUOTE]
 Can you post your PHP script?

--Simon

---

### Post by heimo on 2005-09-16
Do you have php4-mysql package installed?

EDIT: Oh, you must have. I read this post earlier, but didn't re-read properly before answering. :-( Could you turn on mysql-logging and see if it reveals anything wrong?

---

### Post by Burke on 2005-09-16
my php script is as simple as this:

<?php
include "conf.php";
mysql_connect($sql_database, $sql_user, $sql_pass);
mysql_select_db($sql_database);
$query = "SELECT * FROM users WHERE user = '".$_POST['user']."'";
$result = mysql_query($query);
...
the rest is irrelevant... this is where it starts being slow :)

As I said, phpMySQL runs at about the same speed, so I am doubtful that my horrible coding is the problem this time :).  l will enable mysql logging and post here as soon as something useful turns up.




EDIT:
Maybe I'm missing something? My /var/log/mysql/mysql.log (as pt'ed to by my.cnf) shows the following:

mysqld, Version: 4.0.23_Debian-3ubuntu2-log, started with:
Tcp port: 0  Unix socket: /var/run/mysqld/mysqld.sock
Time                 Id Command    Argument
050916  6:26:06      12 Quit
050916  8:37:02      13 Connect     root@localhost on
                     13 Query       SELECT VERSION() AS version
050916  8:37:03      13 Query       SHOW DATABASES
                     13 Quit
050916  8:37:31      14 Connect     root@localhost on
                     14 Query       SELECT VERSION() AS version
050916  8:37:32      14 Query       SHOW DATABASES
                     14 Query       SHOW TABLES FROM `idesk`
                     14 Query       SHOW TABLES FROM `mysql`
                     14 Quit
050916  8:37:33      15 Connect     root@localhost on
                     15 Query       SELECT VERSION() AS version
050916  8:37:35      15 Query       SHOW DATABASES
                     15 Query       SHOW TABLES FROM `idesk`
                     15 Query       SHOW TABLES FROM `mysql`
                     15 Quit
050916  8:37:51      16 Connect     root@localhost on
                     16 Query       SELECT VERSION() AS version
                     16 Query       SELECT USER()
                     16 Query       SELECT COUNT(*) FROM mysql.user
                     16 Query       SELECT Create_priv, Reload_priv FROM mysql.user WHERE User = 'root' OR User = ''
                     16 Query       SHOW MASTER LOGS
050916  8:37:52      16 Quit


This was phpmyadmin loading and it took just >1 minute. Is this just bacause I am running a Pentium 150MHz? 

Thanks for your help
Burke

---

### Post by heimo on 2005-09-16
You could try to repeat the same commands you see on that log, using mysql command line. You can probably start it using: mysql -uroot

---

### Post by LordHunter317 on 2005-09-16
How much memory do you have?  I think you're swapping out and that's what's killing performance.

---

### Post by Burke on 2005-09-16
I replicated most of those commands from the command line, and the results were literally instantaneous.  This memory problems seems feasible, as I only have ~96MB (i think... it was some odd number between 64 and 128.) I have a swap partition at the end of my 1.5GB disk, which is, according to my rough arithmetic, 99MB. I guess this could potentially be the problem, as writing to the end of the disk is significantly slower and this computer is 9 years old to begin with.

However, the difference between over a minute with php/apache and well under 2 seconds from the command line is significant... it makes me think this is more of a configuration error than a system bottleneck. (As if there was only ONE bottleneck :) )

Should I try disabling swap temporarily, or would that be disastrous?

---

### Post by LordHunter317 on 2005-09-16
That would probably be bad yes.  Post the output of free, for starters.

Giving the mysql monitor is orders of magnitude smaller than Apache w/ PHP, and needs less memory to do it's work, my explanation is still plausible.

---

### Post by Burke on 2005-09-16
I think this is what you wanted (btw, thanks for telling me about 'free', I'd never heard of it before):

```
             total       used       free     shared    buffers     cached
Mem:         77344      59940      17404          0       8460      12068
-/+ buffers/cache:      39412      37932
Swap:       104380       3460     100920

```

I also tried this (every 2 seconds) while I was loading phpmyadmin in my browser.  Here is the result with the lowest free RAM:

```

             total       used       free     shared    buffers     cached
Mem:         77344      75300       2044          0      13488      14588
-/+ buffers/cache:      47224      30120
Swap:       104380       3460     100920
```

When a query executes through the webserver, the free RAM will decrease gradually and then instantly jump back up when the page stops loading.



Hmm... hardware requirement issues are seeming slightly more plausible.  Not very much free RAM. (also, guess I have 76MB total, not 96MB)

So do you recommend I try to upgrade the RAM? Would it help if I downgraded to Apache1.x? Make do without MySQL? Some other suggestion? 

Is there a way I can make the connection from Apache to mySQL more efficient? I've heard vague references to this but haven't found anything of substance.

Whatever the case, thank you very much for your help. :)


btw, I just found a page with an integrated server package insluding apache2, mysql4, and php4. (as I have).  It listed the RAM requirement as "64MB (recommended), which my computer exceeds... food for thought.

---

### Post by heimo on 2005-09-16
I dont' believe it's about too low memory. :-/ :-\ Those delays are way too long and you're not running out of memory (low, but not out of). Have you timed your script? Add output for elapsed time in several places on your script.
[http://php.net/microtime]("http://php.net/microtime")

Also make "bare bones" version of your script, strip it until you find the exact command that causes the delay (or rather, everything that doesn't cause). I don't know if this will have any effect (or even make it worse), but I'd try using mysql_pconnect Then I'd try loading that slow page and at the same time loading static pages from the same server. Is that slow? (I'm trying to rule out Apache)

BTW, If you turned on lots of logging, don't forget to disable that - mysql clear text logging can get quite slow. You could also use some kind of dummy SQL query - 'SELECT "1"'.

;-/ I sincerely hope you can get this problem solved. :-\

Try benchmarking your Apache with ab2

For example:
 ```
 ab2 -n10000 -c2 http://www.example.com/
``` 
(of course, replace the url..)

This of course varies a lot from server to server and according the page that's used. Mine looks like:
 > 
Concurrency Level:      2
Time taken for tests:   35.38179 seconds
Complete requests:      10000
Failed requests:        0
Write errors:           0
Total transferred:      3730373 bytes
HTML transferred:       540054 bytes
Requests per second:    285.40 [#/sec] (mean)
Time per request:       7.008 [ms] (mean)
Time per request:       3.504 [ms] (mean, across all concurrent requests)
Transfer rate:          103.94 [Kbytes/sec] received

I believe basic authentication slowed that one down.

This one is on AMD Athlon 700MHz with 128MB memory 
 > Concurrency Level:      2
Time taken for tests:   21.433713 seconds
Complete requests:      10000
Failed requests:        0
Write errors:           0
Total transferred:      3180000 bytes
HTML transferred:       340000 bytes
Requests per second:    466.55 [#/sec] (mean)
Time per request:       4.287 [ms] (mean)
Time per request:       2.143 [ms] (mean, across all concurrent requests)
Transfer rate:          144.87 [Kbytes/sec] received

Both are Hoary Hedgehog / Apache2. I'll do some basic Apache2/PHP benchmarking - of course these are very, very rough. (I'll try to do this testing in low memory conditions.)

---

### Post by Burke on 2005-09-16
Well, WTF!

All of a sudden, mySQL is cruising!

I tried a test script, and it finished in under a second, so I proceeded to try the original script that wouldn't work... which finished in much less than a second. Huh.  Strange... I didn't change anything, and this is most definitely not the 1st time I have rebooted since I installed new software... 

I honestly don't know what the problem was, but apparently it fixed itself.  

Heimo (and LordHunter), I offer you my immense gratitude. Thank you very much for your help.  With this out of the way, maybe I can actually make myself useful around here :)

---

### Post by heimo on 2005-09-16
Ok... I'll update this post when I get more test results. Still on AMD700MHz, 128MB. Test script is like this:
 [PHP]<script language="php">

mysql_connect('localhost','root','');
mysql_select_db('test');
$query = "SELECT * FROM users";
$result = mysql_query($query);

$row = mysql_fetch_assoc($result);
print_r($row);

</script>
[/PHP] 
WARNING: Anyone who's reading this and doesn't know what these do, these are absolutely only for testing purposes if you know what you're doing and you should never use any of these in production environment - these are insane and insecure scripts to use for anything else. :)


(yeah, I know my mysql doesn't have password for root, nasty habbit)

I have one table like this:
 ```
CREATE TABLE `users` (
  `username` varchar(32) default NULL,
  `password` varchar(32) default NULL,
  `firstname` varchar(32) default NULL,
  `lastname` varchar(32) default NULL
) TYPE=MyISAM;

``` 

Which has one record:
 ```
mysql> select * from users;
+----------+----------+-----------+----------+
| username | password | firstname | lastname |
+----------+----------+-----------+----------+
| user	 | pass	 | first	 | last	 |
+----------+----------+-----------+----------+
1 row in set (0.00 sec)

``` 

With 77372 bytes free memory (
```
			 total	 used	 free	 shared	buffers	 cached
Mem:	 110812	 103120	 7692		 0	 6456	 63256
-/+ buffers/cache:	  33408	  77404
Swap:	   321260	   3908	 317352

``` 

 ```
Document Path:		  /test.php
Document Length:		104 bytes

Concurrency Level:	  2
Time taken for tests:   40.978858 seconds
Complete requests:	  10000
Failed requests:		0
Write errors:		   0
Total transferred:	  3890000 bytes
HTML transferred:	   1040000 bytes
Requests per second:	244.03 [#/sec] (mean)
Time per request:	   8.196 [ms] (mean)
Time per request:	   4.098 [ms] (mean, across all concurrent requests)
Transfer rate:		  92.68 [Kbytes/sec] received

Connection Times (ms)
			  min  mean[+/-sd] median   max
Connect:	    0	0   0.0	  0	   0
Processing:	 3	6 104.4	  3	8051
Waiting:	    1	5  66.5	  3	6000
Total:		 3	6 104.4	 3	8051

Percentage of the requests served within a certain time (ms)
  50%	  3
  66%	  4
  75%	  7
  80%	  7
  90%	  7
  95%	  8
  98%	 11
  99%	 11
 100%   8051 (longest request)

``` 

Of course there's huge difference between 150MHz and 700MHz, but it should be no more than 5-10x.

Then I opened couple applications to eat memory (see swap):
```
			 total	 used	 free	 shared	buffers	 cached
Mem:	 110812	 108584	 2228		 0	 764	 35084
-/+ buffers/cache:	  72736	  38076
Swap:	   321260	  49496	 271764

``` 

 ```
Concurrency Level:	  2
Time taken for tests:   44.512185 seconds
Complete requests:	  10000
Failed requests:		0
Write errors:		   0
Total transferred:	  3890000 bytes
HTML transferred:	   1040000 bytes
Requests per second:	224.66 [#/sec] (mean)
Time per request:	   8.902 [ms] (mean)
Time per request:	   4.451 [ms] (mean, across all concurrent requests)
Transfer rate:		  85.32 [Kbytes/sec] received

```

---

### Post by heimo on 2005-09-17
[QUOTE=Burke]Well, WTF!
Heimo (and LordHunter), I offer you my immense gratitude. Thank you very much for your help. With this out of the way, maybe I can actually make myself useful around here :)[/QUOTE]

:D Thanks! Great you got it working! And you always learn from these problems - you learn to diagnose, isolate, debug... Thanks LordHunter too, I've seen you on many threads helping people.

---


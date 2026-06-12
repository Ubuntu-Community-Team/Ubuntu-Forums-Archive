---
title: "PHP processes keep overwhelming my server, eating up the CPU and making it lock up :("
date: 2013-04-07
forum: Server Platforms
---

### Post by hoppipolla on 2013-04-07
Heya guys.

I set up a Debian Squeeze (I hope you don't mind me posting here - I love Ubuntu too and they are very similar, plus you have a great community here! I actually wish I used Ubuntu server instead now to be honest!) Lighttpd server with PHP and MySQL, and also with XCache and Varnish set up.

I am quite new to this, but have tried as hard as I can to resolve this problem with no success.

Whether I use Lighttpd or Nginx or XCache or APC the problem remains.

Basically the server chugs along processing PHP perfectly fine, the RAM looks fine etc. Then suddenly it seems to grind to a halt and the PHP-CGI (or FPM) processes stack up and stack up, eating up all of my quad core CPU power and causing the whole server to become almost entirely non-responsive.

I have 4 sites on my server, 3 of which are quite low traffic and demand, and one of which is quite intensive and busy. So it's almost definitely that site causing it. However we got that site working on this (VPS) server before with a cPanel setup (that I want to avoid now due to cost and preference of Debian, etc.

Even when I remove all AJAX from the intensive site and lower traffic, it still does it.

There are also no obvious errors reported in the PHP, MySQL or lighttpd logs (I got them all working and check them regularly).

Here is the PHP part of my lighttpd.conf:

[http://pastebin.com/ThXAN7md](http://pastebin.com/ThXAN7md)

(max requests set to 500 as recommended [here]("http://redmine.lighttpd.net/projects/1/wiki/docs_performancefastcgi#Why-is-my-PHP-application-returning-an-error-500-from-time-to-time"), not 100% sure it's correct, but of course the problem happened in nginx too anyway!)

and here is my php.ini:

[http://pastebin.com/8ijyY1d7](http://pastebin.com/8ijyY1d7)

and my MySQL my.cnf:

[http://pastebin.com/E9Jq02v5](http://pastebin.com/E9Jq02v5)

Any thoughts? XCache only has 64mb allocated to it but that's what they recommended to start with and it never seems to use it all in its admin CP (that I notice). Both Varnish and XCache are working fine I think and the sites respond VERY fast until this lock up event happens (which it predictably always does).


Thanks very much guys :)

Hoppi

---

### Post by SeijiSensei on 2013-04-07
Sometimes it is contention over the database server that causes problems like these.  As a PostgreSQL user, I cannot help with MySQL, but do a search for methods of tuning that program and see if you need to raise some of the defaults.

Also how well indexed is this database?  Have you tried running all the queries in the PHP scripts from the command prompt with the mysql command-line client?  Are any of them comparatively slow?  Perhaps some queries rely on non-indexed fields which can take a long time to process.  Try using [EXPLAIN](http://dev.mysql.com/doc/refman/5.5/en/using-explain.html) to diagnose these problems.

---

### Post by hoppipolla on 2013-04-07
Here's what it looks like when it happens:

[http://snag.gy/VzRm8.jpg](http://snag.gy/VzRm8.jpg)

It usually stays like that for ages shuffling processes loads and the server may never recover until I reset it manually.

There probably are quite a few PHP scripts I wouldn't know where to begin ._.

I'll take a look but I'm feeling a tad out of my depth right now lol

---

### Post by hoppipolla on 2013-04-07
I'm really close to just giving up and installing cPanel but I don't want to :(

---

### Post by SeijiSensei on 2013-04-07
You managed to hit a long-term load average over 40 in just 45 minutes?  I don't see how installing cpanel will fix that.  I get worried when my server's load average gets above five for any extended period.  

Something is seriously wrong with the configuration of this server.  I'm an Apache+mod_php user myself, so I cannot say what that might be.  Spawning all those cgi-bin processes has to be part of the problem.  Have you ever tried using Apache with mod_php instead of the more "exotic" options you describe?

---

### Post by Doug S on 2013-04-07
Isn't the problem less to do with the VM itself and more to do with the 92.3% stolen CPU time? (the right most number on the "top" cpu line.) For whatever reason, there isn't much CPU time being made available for this machine. 

Seiji: It probably isn't related at all, but on my i7 based 12.04.2 server, I have now had two occurances of a sudden instantanious jump in load average, such that when reverse calculated, knowing the IIR (Infinite Impulse Response) time constants would have been a one time load hit of around 1024. The second one I was trying to re-create, and thought I had the formula to do so, but no. However, I did catch the event, see plot below. More on this at some later date, if I am able to make progress.  - Actualy the numbers suggest that hoppipolla's load issues are more sustained.

---

### Post by tgalati4 on 2013-04-07
Your PHP cache is set to the default 128MB which normally would be sufficient.  

; Maximum amount of memory a script may consume (128MB)
; [http://php.net/memory-limit](http://php.net/memory-limit)
memory_limit = 128M

Try bumping to 256M and see if the behavior changes.  How much RAM on this system?  Are you hitting swap?

```
free
```

Some other possible tweaks:


[mysqlnd]
; Enable / Disable collection of general statistics by mysqlnd which can be
; used to tune and monitor MySQL operations.
; [http://php.net/mysqlnd.collect_statistics](http://php.net/mysqlnd.collect_statistics)
mysqlnd.collect_statistics = On
 
; Enable / Disable collection of memory usage statistics by mysqlnd which can be
; used to tune and monitor MySQL operations.
; [http://php.net/mysqlnd.collect_memory_statistics](http://php.net/mysqlnd.collect_memory_statistics)
mysqlnd.collect_memory_statistics = Off
 
; Size of a pre-allocated buffer used when sending commands to MySQL in bytes.
; [http://php.net/mysqlnd.net_cmd_buffer_size](http://php.net/mysqlnd.net_cmd_buffer_size)
;mysqlnd.net_cmd_buffer_size = 2048
 
; Size of a pre-allocated buffer used for reading data sent by the server in
; bytes.
; [http://php.net/mysqlnd.net_read_buffer_size](http://php.net/mysqlnd.net_read_buffer_size)
;mysqlnd.net_read_buffer_size = 32768
 
mysqlnd.net_read_timeout = 30

---

### Post by SeijiSensei on 2013-04-08
The [screenshot](http://snag.gy/VzRm8.jpg) he posted above shows he has 2 GB of memory and 5 GB of swap, none of which is in use.  He has almost a gigabyte devoted to disk caching.  So I doubt he is running out of memory.

[quote=Doug S]Actualy the numbers suggest that hoppipolla's load issues are more sustained. [/quote]

The screenshot shows the machine has been up only 45 minutes, yet it is already entirely overwhelmed with an instantaneous load average in the 70's and the long-term figure around 45.  As I said, I never run cgi-bin applications, but I wonder if they carry more overhead than running PHP as a module where a lot of memory is shared, and there is no need to bring up and tear down a separate application for each request.

---

### Post by Doug S on 2013-04-08
> The screenshot shows the machine has been up only 45 minutes, yet it is already entirely overwhelmed with an instantaneous load average in the 70's and the long-term figure around 45.I agree, however the "st" number suggests it is not getting much CPU, so it is not surprising that it is falling further and further behind.
hoppipolla: Is this a virtual computer? the top '"st" number suggests that it is.
 And > with an instantaneous load average in the 70'sThat is actually the 1 minute load average, still heavily filtered. The 1 minute filter is roughly (with a once per 5 seconds sample rate)(it isn't actually calculated this way):```
Load_n = Load * 0.08 + Load_old * 0.92
```And all I was trying say, rather poorly, with my example, is that I have cases where I don't believe the reported load average.

---

### Post by tgalati4 on 2013-04-08
How much RAM is allocated to the virtual machine that is running this instance?

---

### Post by CharlesA on 2013-04-08
Wow. I just checked my single core VPS and even though it is only running three low traffic sites, the stats in top were way more conservitive than the screenshot of the terminal posted.

```
top - 14:13:18 up 6 days, 21:31,  1 user,  load average: 0.00, 0.00, 0.00
Tasks:  33 total,   1 running,  32 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni, 99.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    524288k total,   104024k used,   420264k free,        0k buffers
Swap:   524288k total,       12k used,   524276k free,    73356k cached

```

What has me concerned is they have 65 running processes at the moment and only 6.9% CPU is id (idle) and [92.3% CPU is st (stolen time).]("http://serverfault.com/questions/230495/what-does-st-mean-in-top")

It sounds like whatever host they have this VM on, it cannot handle the stress of running that many processes at once.

The number of processes sounds like a configuration thing to me, but I don't know much about php-cgi as I have only really used Apache with mod_php and Nginx with php-fpm.

---

### Post by tgalati4 on 2013-04-08
What is the hypervisor that is being used?  It seems to be a hypervisor problem (possibly due to bad hardware?) if it only gives 8% of the CPU cycles to the virtual machine.  The PHP issues may be due to lack of processing power, not RAM.  What other VM's are running?  What does their load look like?

---

### Post by Doug S on 2013-04-08
Out of interest, I tried to create a situation on my test server where I had a very high percentage of stolen CPU time. I was unsuccessful, achieving around 10% max.

I made a VM and loaded it down like crazy, then I also loaded down like crazy the host. The VM (The snapshot was not at the max stolen that I acheived):```
top - 17:18:56 up  1:29,  2 users,  load average: 68.48, 68.64, 68.41
Tasks: 161 total,  [COLOR=#ff0000]69[/COLOR] [COLOR=#ff0000]running,  [/COLOR]92 sleeping,   0 stopped,   0 zombie
Cpu(s): 93.9%us,  0.2%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  [COLOR=#ff0000]5.9%st[/COLOR]
Mem:   2050976k total,   220292k used,  1830684k free,    11468k buffers
Swap:  2093052k total,        0k used,  2093052k free,    80556k cached
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1709 doug      20   0  4164   88    0 R    6  0.0   4:41.65 waiter
 1685 doug      20   0  4164   88    0 S    6  0.0   4:43.02 waiter
 1686 doug      20   0  4164   88    0 R    6  0.0   4:43.76 waiter
 1688 doug      20   0  4164   88    0 R    6  0.0   4:45.73 waiter
 1689 doug      20   0  4164   88    0 R    6  0.0   4:43.25 waiter
 1694 doug      20   0  4164   88    0 R    6  0.0   4:45.58 waiter
 1696 doug      20   0  4164   88    0 R    6  0.0   4:43.98 waiter
 1697 doug      20   0  4164   88    0 R    6  0.0   4:43.59 waiter

```The host:```
top - 17:19:48 up 10 days,  7:40,  5 users,  load average: 72.54, 72.71, 72.45
Tasks: 213 total,  [COLOR=#ff0000]70[/COLOR][COLOR=#ff0000] running, [/COLOR]143 sleeping,   0 stopped,   0 zombie
Cpu(s):100.0%us,  0.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  16004120k total, 13766388k used,  2237732k free,  1121260k buffers
Swap:  8294396k total,   102792k used,  8191604k free, 10403068k cached
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
30938 libvirt-  20   0 6274m 1.2g 6944 S  [COLOR=#ff0000]378  8.1 345:10.46 kvm[/COLOR]
32044 doug      20   0  4164   88    0 R    7  0.0   5:17.52 waiter
32072 doug      20   0  4164   88    0 R    7  0.0   5:15.29 waiter
32045 doug      20   0  4164   88    0 R    6  0.0   5:16.25 waiter
32047 doug      20   0  4164   88    0 R    6  0.0   5:15.97 waiter
32050 doug      20   0  4164   88    0 R    6  0.0   5:15.83 waiter

```Ignore that the host has swap used, that is left over from some other test. I realize this doesn't help the main thread, but if I could have achieved over 90% stolen I was going to look for accouting issues in top.

---

### Post by hoppipolla on 2013-04-08
My friend who does this stuff for a living (I believe) thinks it's due to the size of the forum database. The MyBB database is about 350mb, and we're thinking that some MySQL queries are taking a long time and causing things to bottleneck.

We're looking at the slow queries logs and stuff at the moment... but I think we're close.

It does work on cPanel though so that's my last resort. I'll stick this out for a few more days though :)

---

### Post by CharlesA on 2013-04-08
Nevermind. :)

---

### Post by SeijiSensei on 2013-04-09
The size of the database matters less than whether it is well-indexed. I built an application for a client where the database had over eight million records.  At first it took ages to run queries, but after I spent some time with tools like EXPLAIN, I created some additional indexes, and the queries then ran nearly instantaneously.

---

### Post by CharlesA on 2013-04-09
> **hoppipolla said:**
> We're looking at the slow queries logs and stuff at the moment... but I think we're close.

It does work on cPanel though so that's my last resort. I'll stick this out for a few more days though :)

Now the question becomes: What is the difference between the cPanel setup and the way you have it setup now?

---

### Post by hoppipolla on 2013-04-09
Very good observations and comments guys!

I think you're both right there!

Hm.. I know little to nothing about indexing... I may have to learn about that!

And we do still need to look into what cPanel was doing differently.

But, at least we now know the problem! I locked the forum just temporarily to keep the site up and running until we sort this!! :)

---

### Post by SeijiSensei on 2013-04-09
Suppose you have a table called "people" with names and addresses in it that you want to search by last name.  Let's call that field "last_name".  Assuming that last_name is not the primary key, which is unlikely since primary keys need to be unique, you need to add another index with the [CREATE INDEX]("https://dev.mysql.com/doc/refman/5.5/en/create-index.html") command like this:

```
CREATE INDEX people_last ON people (last_name);
```

If your query uses both first and last name, you'd need this instead:

```
CREATE INDEX people_name ON people (last_name, first_name);
```

That creates an index that uses the combination of those two fields.

The name of the index is arbitrary.  I usually name them with the name of the table and some mnemonic device to remind me which fields were used.

You can see the existing indexes on a table with the [SHOW INDEX](http://dev.mysql.com/doc/refman/5.5/en/show-index.html) command.

---

### Post by Doug S on 2013-04-09
In my previous post, it might have appeared as though I was going off on a tangent, since I couldn't get the "stolen" percentage high enough to prove what I suspected.
Now, I can and the point is that with a high percentage of "stolen" time, the accounting in "top" does not reflect reality. Rather, the accounting in "top" includes the stolen time.

So, and for example from that screen shot, for PID 1653 28% CPU time and 1:29.23 total CPU time at 92.3% "stolen". It is actually 2.2% CPU time and 6.87 seconds total CPU time. (assumes constant "stolen" time, which is probably incorrect)
I suppose even 6.87 seconds is still rather horrendous for one of those php-cgi scripts. I just wanted to understand the discrepencies we were seeing in the screen shot of "top".

Example from my computer (Where the sum of the %CPU per PID is about 400% (4 CPUs are used by this VM), but 98% of that isn't really there):```
top - 14:40:28 up 45 min,  2 users,  load average: 68.80, 68.60, 63.70
Tasks: 161 total,  [COLOR=#ff0000]70[/COLOR] [COLOR=#ff0000]running,  [/COLOR]91 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  0.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si, [COLOR=#ff0000]98.0%st[/COLOR]
Mem:   2050976k total,   223752k used,  1827224k free,    20256k buffers
Swap:  2093052k total,        0k used,  2093052k free,    80696k cached
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1697 doug      20   0  4164   88    0 R   11  0.0   2:16.70 waiter
 1725 doug      20   0  4164   88    0 R   11  0.0   2:11.44 waiter
 1732 doug      20   0  4164   88    0 R   11  0.0   2:12.57 waiter
 1749 doug      20   0  4164   88    0 R   11  0.0   2:15.49 waiter
 1708 doug      20   0  4164   88    0 R   10  0.0   2:14.86 waiter
 1747 doug      20   0  4164   88    0 R   10  0.0   2:08.70 waiter
 1722 doug      20   0  4164   88    0 R    9  0.0   2:11.07 waiter
 1729 doug      20   0  4164   88    0 R    8  0.0   2:12.01 waiter
 1757 doug      20   0  4164   88    0 R    8  0.0   2:10.13 waiter
 1705 doug      20   0  4164   88    0 R    7  0.0   2:10.17 waiter
 1698 doug      20   0  4164   88    0 R    7  0.0   2:17.56 waiter
 1699 doug      20   0  4164   88    0 R    7  0.0   2:16.93 waiter
 1710 doug      20   0  4164   88    0 R    7  0.0   2:14.10 waiter
 1713 doug      20   0  4164   88    0 R    7  0.0   2:13.69 waiter
 1718 doug      20   0  4164   88    0 R    7  0.0   2:14.67 waiter
 1723 doug      20   0  4164   88    0 R    7  0.0   2:14.50 waiter
 1735 doug      20   0  4164   88    0 R    7  0.0   2:09.35 waiter
 1738 doug      20   0  4164   88    0 R    7  0.0   2:10.52 waiter
 1741 doug      20   0  4164   88    0 R    7  0.0   2:09.20 waiter
 1743 doug      20   0  4164   88    0 R    7  0.0   2:10.35 waiter
 1748 doug      20   0  4164   88    0 R    7  0.0   2:10.09 waiter
 1755 doug      20   0  4164   88    0 R    7  0.0   2:10.20 waiter
 1758 doug      20   0  4164   88    0 R    7  0.0   2:08.76 waiter
 1760 doug      20   0  4164   88    0 R    7  0.0   2:09.92 waiter
 1763 doug      20   0  4164   88    0 R    7  0.0   2:08.86 waiter
 1765 doug      20   0  4164   88    0 R    7  0.0   2:10.54 waiter
 1736 doug      20   0  4164   88    0 R    6  0.0   2:09.31 waiter
 1737 doug      20   0  4164   88    0 R    6  0.0   2:10.51 waiter
```I suspect, but am not sure, that when things work when you use cPanel, you are actually just setting up the VM correctly to not have all of its processor time re-allocated elsewhere. (Also, I suspcect Seiji's ideas will help a lot also).

---

### Post by hoppipolla on 2013-04-09
I'll try to catch up soon (it's all very heavy for me lol) but also here is my my.cnf:

[http://pastebin.com/q2unrNZF](http://pastebin.com/q2unrNZF)

and some of my slow queries log:

[http://pastebin.com/AsFJseyb](http://pastebin.com/AsFJseyb)


Some are really long I know... sometimes it might be due to a maxed out CPU though I dunno o.O

---

### Post by hoppipolla on 2013-04-09
OK erm... in response to the posts...

**Seiji -** I suspect that the variety and complexity of MyBB searches may be a bit too much for working out indexing? Wouldn't it take aaaages? >.<

**Doug S -** With st (Steal Time) and stolen CPU... I think there might be something there! I'm asking my host...

**tgalati4 -** With the modifications to my.cnf... I may make them! Do you have high hopes for them? I don't really like to make changes unless I really think they might make a difference!

EDIT -- Although I see you were also mentioning the st CPU like Doug S... that is VERY interesting isn't it... :o

Thanks a lot again guys! :)

---

### Post by SeijiSensei on 2013-04-10
> **hoppipolla said:**
> **Seiji -** I suspect that the variety and complexity of MyBB searches may be a bit too much for working out indexing? Wouldn't it take aaaages? >.<

Not necessarily. 

First, let me suggest you set up the application on another machine for testing purposes.  It's hard to play around on a production machine without possibly compromising the application for actual users.

Since you have so many contending processes I'd have to guess that any queries that are causing the problem must be fairly common ones.  Searches would be at the top of my list.  Walk yourself through the application and try everything that normal users would do.  Do some activities take longer than expected?  If so, look in the PHP code to find the queries those activities employ, then run them yourself from the command line using the mysql client.  Look at the criteria in their WHERE clauses and make sure that those criteria are well-indexed.

A lot of bulletin-board applications rely on simple SQL queries to handle searching.  That often leads to deteriorating performance as the size of the database increases.  I use [SphinxSearch]("http://www.sphinxsearch.com/") to do full-text queries in situations like yours as it is exceedingly fast.  Sphinx is designed for applications like forums and catalogs where all the information is stored in an SQL database.  In one case, where someone was using [Zen Cart]("http://www.zen-cart.com/") to handle a 50,000+ catalog of items, full-text searches could take up to a minute.  After I replaced the standard SQL-based method with Sphinx, those searches were nearly instantaneous.

---

### Post by hoppipolla on 2013-04-10
One issue is that even after I disabled all searches by removing the search.php page, the server still died in the same way.

Only by closing the forum completely (and just leaving up the shoutbox, chat room and gallery) can I keep the server up :(

Even users coming online can sometimes result in a very slow query, even though only one row has to be examined. Look:

[http://pastebin.com/DNh9ahFv](http://pastebin.com/DNh9ahFv)

---

### Post by SeijiSensei on 2013-04-12
> UPDATE mybb_users SET lastactive='1365606064', timeonline=timeonline+105  WHERE uid='12504';
# Time: 130410 16:01:22
# User@Host: sonichen[sonichen] @ localhost []
# Query_time: 15.888670  Lock_time: 0.000030 Rows_sent: 0  Rows_examined: 1


Does that mean it took 15 seconds (!) just to update a single field?  Use the mysql command-line client to show the indexes on the "users" table.  Is uid the primary key?  If not, is it indexed?

This could be because the server itself is overburdened, or it could be bad database design.  If you take down the webserver and just run the same query from the command line with mysql, does it still take a long time?

It's also weird that uid is encased in quotes.  Isn't it a numerical field?

---

### Post by hoppipolla on 2013-04-12
Ah it's not stolen time ._.

Look...

[http://i.imgur.com/gASMyQM.jpg](http://i.imgur.com/gASMyQM.jpg) (my site on low CPU)

[http://i.imgur.com/RmT9JcW.jpg](http://i.imgur.com/RmT9JcW.jpg) (my site when it all locks up)


And sometimes it can take minutes to log a user on (to finish the query)... it's weird.

---

### Post by Doug S on 2013-04-12
> **hoppipolla said:**
> Ah it's not stolen time ._.Your new pie chart links do not prove that your VM was not suffering from "stolen" time.
Your much much earlier link to your screen capture of your "top" command does prove (I think) that your VM was, at that time, suffering from an extreme percentage of "stolen" time.
The new pie chart links might suggest that your VM might be limited to 23.51% (perhaps 25%) of the host overall CPU capactity. The host hypervisor does not have to actually use the time, if it steals it. However, that is likely a substantial  amount of CPU time available to your VM.
By the way, for my example from my computer of post #20, the host load averages were very low: ```
doug@s15:~/temp$ uptime
15:28:28 up 3 days,  1:41,  5 users,  load average: 0.00, 0.06, 0.26
```

---

### Post by hoppipolla on 2013-04-16
I really think it's PHP processes getting "locked up". The more I allow it to start, the more they stack up and the longer it takes for them to clear ._.

---

### Post by hoppipolla on 2013-04-29
For the record erm, I managed to put a fast and I think fully working server together by installing Ubuntu 12.04, then ZPanel, then memcache, APC and Varnish, and then switching Apache for Lighttpd. I lost the ZPanel interface as it relies on Apache AFAIK, but I got a working and very fast server out of the deal I think.

Whatever change had to be made to stop the crashes I think was made by the ZPanel staff in the background (for their default ZPanel install).

So erm... yeah, result, I think :)

---


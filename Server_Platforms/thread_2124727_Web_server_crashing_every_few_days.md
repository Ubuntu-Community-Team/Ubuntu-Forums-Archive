---
title: "Web server crashing every few days"
date: 2013-03-11
forum: Server Platforms
---

### Post by self-defence on 2013-03-11
Hi guys I've got an Ubuntu web server that keeps crashing on me every few days but don't even know where to start looking for the problem.
I've already updated and upgraded it but no luck. 

When I took it out of the rack and hooked it up to a monitor and a keyboard it booted. So I stuck it back in and first time it booted ok but then a couple of days later went down and didn't want to boot up anymore. It has happened the same way a couple of times no.

So can anyone give me some advice how to start or what to look for?

Thanks and best regards

---

### Post by tgalati4 on 2013-03-11
Look in /var/log and check every file for clues.  If you don't find anything, then that usually points to a hardware problem--power supply or dying motherboard.  While you have the rack out, reseat RAM, cables, and blow out the dust.

Post any messages that you don't understand, don't bother posting entire log files.

ssh in from another terminal and run* top *or *htop* and keep it running.  If it freezes, you sometimes get a snapshot of what was running, take a picture with a digital camera, or cut and paste if possible.

---

### Post by GordThompson on 2013-03-12
> **self-defence said:**
> I've got an Ubuntu web server that keeps crashing on me every few days
[...]
I stuck it back in and first time it booted ok but then a couple of days later went down and didn't want to boot up anymore. It has happened the same way a couple of times no.

So can anyone give me some advice how to start or what to look for?
I had a similar experience with a Ubuntu 8.x virtual server. It ran fine for a couple of years and then it started "winking out". A hardware problem was ruled out fairly quickly because the host machine was not having any problems at all.

It turns out that the client's "web guy" had just given the company's main website a makeover, changing it from (mostly) static web pages to a WordPress monstrosity with 40 or 50 plugins installed. Prior to that change an inconsiderate bot could establish multiple connections and "scarf down" the entire site without overwhelming the server. After the change one of those bots would come along and lock up the server so tight that it would not respond *at all*; the only thing I could do was reset (i.e., "power cycle") the VM.

So, +1 for starting by looking at the logs. That's how I came to the conclusion that those bots were killing us, and once I installed `mod_limitipconn` and capped the number of simultaneous connections from a given IP the server stopped tanking.

---

### Post by hydn79 on 2013-03-12
There's a strong change its related to Apache. Can you run to command the press Shift + M and paste screenshot here?

What type of website(s) are on this server? Wordpress, Drupal, custom code?

---

### Post by self-defence on 2013-03-13
Sorry guys had some stuff and couldn't get to the server.

I'll be able to get it out tomorrow since it doesn't even boot after the last failure. 

The websites running are mostly Wordpress and a couple of static ones and some very basic custom work.

You think it might be something to do with Apache?

Thanks for the help I'll check the logs and top. I've already tried to look at the logs but wasn't able to decode much.

---

### Post by self-defence on 2013-03-18
Hi guys.

Thanks for helping me so quickly but I was unable to access the server quicker because of my scheduled. 

The server is a Dell PowerEdge 2400 if it makes any difference. 

As always the server became unresponsive after a couple of days and this was the error on the screen when I turned on the monitor:
[IMG]http://img255.imageshack.us/img255/9047/img286j.jpg[/IMG]

So I switched it off and booted it up again and it booted fine and is working for the time being but there was an error during boot up regarding Apache just before the log on screen:
[IMG]http://imageshack.us/a/img824/1872/img289n.jpg[/IMG]

I'm guessing there's something wrong in the Apache configuration file. Although I have no idea what since I used Webmin to configure everything. 

But I don't know if the two errors are connected?

I logged in and left TOP running for when the server fails if something of significance can be caught there. 

Thanks for the help and best regards.

---

### Post by tgalati4 on 2013-03-18
Linux is unforgiving when it runs out of memory.  Did you not see the "Out of memory . . ." message?  Linux will start killing processes to survive, but that won't help with a remote server.

Instead of htop, run an ssh session and watch *free*.  Do you have a large enough swap file?  Do you have large enough memory footprint in php.ini?  How much RAM in the machine?  What is the output of *free* right after boot and starting all services.

---

### Post by self-defence on 2013-03-19
The sever has 512MB of RAM installed. But it had been working fine for the last three years before any problems showed up. I even ran Memtest to see if the memory was defective but it all passed. 

It crashed again during the night.

Here is the free right after boot up:
```
free
             total       used       free     shared    buffers     cached
Mem:        515488     509140       6348          0       2468     324280
-/+ buffers/cache:     182392     333096
Swap:      1020116        896    1019220

```

And here's the top from when it crashed. It was still on the screen:
[IMG]http://img7.imageshack.us/img7/937/img290ia.jpg[/IMG]

I don't think it has anything to do with increased activity on the web server if any there is less activity now that there was two years ago. So it should have been crashing then.

Or should I just download the whole web server and db content and do a fresh install?

Thanks for the help. :)

---

### Post by Doug S on 2013-03-19
Look at your load average, the 15 minute time constant one is 76!!!! Your swap space is full, and the memory is consumed. Your server appears to be very very severly overloaded. Of course, once it starts swapping a lot, things gets worse, as more and more time is spent just swapping.

---

### Post by SeijiSensei on 2013-03-19
I see so many apache and postgresql instances there that I have to wonder what this machine is doing.  If it's a web server, and those are requests for pages that use the database, this machine is way underpowered for the amount of traffic it is handling.  Increasing swap will help, but you need a lot more physical memory.  I get worried when I have machines with load averages above 3-4.  Values like 90 are off the charts.  Upgrade to at least 2 GB of physical memory and a swap file of at least equal size.

---

### Post by koenn on 2013-03-19
> **Doug S said:**
> Look at your load average, the 15 minute time constant one is 76!!!! Your swap space is full, and the memory is consumed. Your server appears to be very very severly overloaded. Of course, once it starts swapping a lot, things gets worse, as more and more time is spent just swapping.
Looks like all available swap space has been used up as well. 
There's no way that system can stay up.

---

### Post by lisati on 2013-03-19
I had a similar out of memory problem a couple of months back. The solution I put in place, which might not suit someone with a busy site, was to look for a section in apache2.conf that began *<IfModule mpm_prefork_module>* and comment out the line *MaxClients 150*, and add a new line in that section:
```
MaxClients 50
```

---

### Post by koenn on 2013-03-19
> **self-defence said:**
>  booted it up again and it booted fine and is working for the time being but there was an error during boot up regarding Apache just before the log on screen:
[...]


I guess you'd have to look into this as well. A shipload of Apache processes after Apache announced "undefined results" (read; unpredictable behavior)  - there might be a connection there.

Also, any reason why you have both mysql and postgres ? Unless there's a specific reason you need two different database engines, this (to me) suggests a certain sloppiness in the setup,  which in turn hints at "all sorts of things could be going on there, it's gonna be hell to figure it all out"

---

### Post by lisati on 2013-03-19
> **koenn said:**
> 
Also, any reason why you have both mysql and postgres ? Unless there's a specific reason you need two different database engines, this (to me) suggests a certain sloppiness in the setup,  which in turn hints at "all sorts of things could be going on there, it's gonna be hell to figure it all out"

Good catch: unless there's good reason to do otherwise, I'd recommend choosing between mysql and postgres. It might be coincidence, but having both can potentially introduce opportunities for conflicts.

---

### Post by SeijiSensei on 2013-03-19
I have often run both MySQL and PostgreSQL on servers.  They listen on separate ports, have entirely separate data directories, and generate no conflicts that I can see.  I prefer PostgreSQL but some web applications presume MySQL.

As I said before, a lot more physical memory and a lot more swap would do wonders.

---

### Post by tgalati4 on 2013-03-19
I'm glad you were able to take a picture of the* top *screen as it crashed.  You definitely need more RAM.  You have a memory leak or runaway apache/postgres/mysql processes.  The logs must show something--you have logs for apache, mysql, and postgres.  What is generating all of the activity?  Is it strictly traffic or an internal problem?

---

### Post by koenn on 2013-03-20
> **SeijiSensei said:**
> I have often run both MySQL and PostgreSQL on servers. 
I'm not so questioning  the *possibility* of having multiple DBMS and certainly not *your*  ability to setup and run such a configuration.
I'm just wondering whether it, in the OP's case, has been done deliberately and correctly, or if we should treat it as an indication that  the whole system might be an unpredictable mess. 


> **SeijiSensei said:**
> 
As I said before, a lot more physical memory and a lot more swap would do wonders.

No doubt about it.
But the OP saying " it had been working fine for the last three years before any problems showed up" and " there is less activity now that there was two years ago"  makes me wonder whether there could be more to it than just not enog RAm and swap. Denial of Servide ? Site harvesters ?  configuration issues causing apache to spwan child processes in an endless loop ? ...  just thinking out loud here.

---

### Post by self-defence on 2013-03-20
First thing is the traffic on the gateway doesn't support the activity supposed to be on the server. 
There are a few websites running on the server but nothing that could have that kind of traffic. They mostly use MySql but there was one that used PostgreSql that's why it's there. But It could just as well be removed since it is no longer critical.

I checked the Apache access log and found something a little strange. There were a lot of requests from 127.0.0.1 entered as denied. And in the error log some requests to MySql that were not finding tables. I'm wondering if this could be the problem.

As far as physical memory is concerned unfortunately I don't have any top upgrade and as I said the server worked for years with almost no problems with the same stack of websites. The only thing that might be different a few WordPresses might have been upgraded to newer versions.

Thanks for the help guys. I'll try and investigate further the MySql error in the error log but I have no idea what the localhost access is all about.

---

### Post by koenn on 2013-03-20
you could post those log entries, see if someone here has an idea what they might mean

---

### Post by self-defence on 2013-03-25
Hi.

Well I was able to logon and get some logs form the server between crashes. It really does seem that the load seems to go out of control.

Here they are.

Access log (the last couple of lines):
```
27.0.0.1 - - [25/Mar/2013:14:48:32 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache (internal dummy connection)"
127.0.0.1 - - [25/Mar/2013:15:00:13 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache (internal dummy connection)"
127.0.0.1 - - [25/Mar/2013:15:18:34 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache (internal dummy connection)"
220.181.108.122 - - [25/Mar/2013:15:30:15 +0100] "GET / HTTP/1.1" 200 16392 "-" "Mozilla/5.0 (compatible; Baiduspider/2.0; +http://www.baidu.com/search/spider.html)"
123.125.71.13 - - [25/Mar/2013:15:30:42 +0100] "GET / HTTP/1.1" 200 16392 "-" "Mozilla/5.0 (compatible; Baiduspider/2.0; +http://www.baidu.com/search/spider.html)"
127.0.0.1 - - [25/Mar/2013:15:42:36 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache (internal dummy connection)"
127.0.0.1 - - [25/Mar/2013:15:42:37 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache (internal dummy connection)"
127.0.0.1 - - [25/Mar/2013:15:42:38 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache (internal dummy connection)"
127.0.0.1 - - [25/Mar/2013:15:42:39 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache (internal dummy connection)"
127.0.0.1 - - [25/Mar/2013:15:42:55 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache (internal dummy connection)"
127.0.0.1 - - [25/Mar/2013:15:42:56 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache (internal dummy connection)"
127.0.0.1 - - [25/Mar/2013:15:42:57 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache (internal dummy connection)"
127.0.0.1 - - [25/Mar/2013:15:42:58 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache (internal dummy connection)"
127.0.0.1 - - [25/Mar/2013:15:42:59 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache (internal dummy connection)"
127.0.0.1 - - [25/Mar/2013:15:43:16 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache (internal dummy connection)"
127.0.0.1 - - [25/Mar/2013:15:43:17 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache (internal dummy connection)"
127.0.0.1 - - [25/Mar/2013:15:43:18 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache (internal dummy connection)"
127.0.0.1 - - [25/Mar/2013:15:43:19 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache (internal dummy connection)"
127.0.0.1 - - [25/Mar/2013:15:43:21 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache (internal dummy connection)"
199.30.16.63 - - [25/Mar/2013:16:28:32 +0100] "GET /robots.txt HTTP/1.1" 404 268 "-" "msnbot-media/1.1 (+http://search.msn.com/msnbot.htm)"
199.30.16.63 - - [25/Mar/2013:16:28:33 +0100] "GET /images/index_r1_c1.jpg HTTP/1.1" 404 280 "-" "msnbot-media/1.1 (+http://search.msn.com/msnbot.htm)"
157.56.93.38 - - [25/Mar/2013:17:28:23 +0100] "GET /robots.txt HTTP/1.1" 404 277 "-" "Mozilla/5.0 (compatible; bingbot/2.0; +http://www.bing.com/bingbot.htm)"
157.56.93.38 - - [25/Mar/2013:17:30:17 +0100] "GET /galerija/?p=311 HTTP/1.1" 404 276 "-" "Mozilla/5.0 (compatible; bingbot/2.0; +http://www.bing.com/bingbot.htm)"
202.46.60.63 - - [25/Mar/2013:17:39:01 +0100] "GET / HTTP/1.1" 200 16392 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0)"
119.63.193.130 - - [25/Mar/2013:17:39:08 +0100] "GET / HTTP/1.1" 200 16392 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0)"

```
The localhost seems to be turning up the same way allover the place.

And the error log (the lats couple of lines but the log is filled with it):
```
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('hits_month','1','2013','03','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('hits_week','8','2013','13','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('hits_day','10','2013','1364166000','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('hits_nobots','21','0','0','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('hits_year_nobots','25','2013','0','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('hits_month_nobots','99','2013','03','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('hits_week_nobots','23','2013','13','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('hits_day_nobots','19','2013','1364166000','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('visits','7','0','0','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('visits_year','2','2013','0','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('visits_month','3','2013','03','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('visits_week','9','2013','13','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('visits_day','11','2013','1364166000','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('visits_nobots','22','0','0','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('visits_year_nobots','26','2013','0','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('visits_month_nobots','98','2013','03','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('visits_week_nobots','24','2013','13','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS (name,type,val1,val2,val3) VALUES ('visits_day_nobots','17','2013','1364166000','1') made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS_RAW' is marked as crashed and should be repaired for query INSERT INTO wp_TABLE_STATISTICS_RAW\r\n\t\t\t\t\t(\r\n\t\t\t\t\t\tremote_addr,\r\n\t\t\t\t\t\thttp_user_agent,\r\n\t\t\t\t\t\thttp_accept_language,\r\n\t\t\t\t\t\tpage,\r\n\t\t\t\t\t\tpagetype,\r\n\t\t\t\t\t\tpageid,\r\n\t\t\t\t\t\tstamp,\r\n\t\t\t\t\t\tbrowser,\r\n\t\t\t\t\t\tbrowserversion,\r\n\t\t\t\t\t\tbrowsertype,\r\n\t\t\t\t\t\tos,\r\n\t\t\t\t\t\treferer,\r\n\t\t\t\t\t\tmethod,\r\n\t\t\t\t\t\tsearchstring,\r\n\t\t\t\t\t\tsearchstringtype,\r\n\t\t\t\t\t\treferertype,\r\n\t\t\t\t\t\tentrypage\r\n\t\t\t\t\t\t)\r\n\t\t\t\t\tVALUES\r\n\t\t\t\t\t (\r\n\t\t\t\t\t\t'-730782814',\r\n\t\t\t\t\t\t'',\r\n\t\t\t\t\t\t'',\r\n\t\t\t\t\t\t'/',\r\n\t\t\t\t\t\t'0',\r\n\t\t\t\t\t\t'1344',\r\n\t\t\t\t\t\t'1364233757',\r\n\t\t\t\t\t\t'100',\r\n\t\t\t\t\t\t'5.0',\r\n\t\t\t\t\t\t'0',\r\n\t\t\t\t\t\t'',\r\n\t\t\t\t\t\t'',\r\n\t\t\t\t\t\t'1',\r\n\t\t\t\t\t\t'',\r\n\t\t\t\t\t\t'0',\r\n\t\t\t\t\t\t'0',\r\n\t\t\t\t\t\t'1'\r\n\t\t\t\t\t\t) made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update
[Mon Mar 25 17:49:18 2013] [error] [client 212.113.35.162] WordPress database error Table './WEBSITE/wp_TABLE_STATISTICS' is marked as crashed and should be repaired for query SELECT count(type)\r\n                    FROM wp_TABLE_STATISTICS\r\n                    WHERE\r\n                        type=6 made by require, require_once, do_action, call_user_func_array, cystats_update_data, statistics->update

```
Could this WordPress be overloading the server?

Thanks for the help and best regards.

---

### Post by tgalati4 on 2013-03-25
You have baidu and bing spiders crawling through your web pages.  I don't know if that would create the load you are seeing, but I would use IPtables to clamp down on activity from those IP addresses.  That would free up resources to allow you to better troubleshoot what is going on.  The Wordpress database crash could be the cause or side effect of the load.  The system doesn't have the RAM or CPU cycles to write the database entries, so it has crashed.  But probably in a recoverable fashion.

Make note of the time that the dummy Apache connections occur and relate them to the other log files--especially auth.log and see if you can determine what process is causing that.  I'm guessing it's a network monitor program--to see if your site is up.  What do you use for site monitoring?  Why does it need 14 pings? Perhaps it is collecting Apache responsiveness statistics.  Try turning off that service temporarily, until you get your system repaired.

---

### Post by Doug S on 2013-03-25
My experience with the spiders part: I have not found the bing bot to be an annoying web crawler. The baidu one, used to be O.K., but here is the edit header from my robots.txt file:```
# robots.txt 2011.09.26
#            Until now I have allowed Baiduspider. But it has gone mental and also ignores some meta tags.
#            Disallow it.
#            A new robot, AhrefsBot, does not behave or obey meta tags.
#            Disallow it.
```Both obey the robots.txt file, so I suggest that method as a possible easier way to deal with them than iptables, given the many IP addresses they have. Here is the related entry:```
User-agent: Baiduspider
Disallow: /
```

---

### Post by hydn79 on 2013-03-26
So much incorrect info and assumptions being posted. :/ As I said before OP even posted screenshots this sounds like Apache. Tweaking a few conf lines isn't going to resolve this. How important is this server to you? It is to much to help via forums for me, as you can see took a while for me to check back here. There needs to be a full audit and Apache issues resolved.

---

### Post by hydn79 on 2013-03-26
Also looking at the requested top stats, you suffered a MySQL OOM crash. You may now have crashed database tables because of that. The first thing you want to do is add more RAM to this server. Usually this cannot be recommended until other things like memory leaks, etc are eliminated. But with only 512MB of RAM you won't be able to run a MySQL, Apache (w/ PHP) website unless is a small database, small website and with little traffic and correct settings to ensure demand on RAM by Apache/PHP is reduced.

I manage similar sized servers on AWS (t1.mico) with very little RAM as well but these are small Wordpress blogs with very little traffic. Also see:
[http://thehayden.org/when-to-use-amazon-ec2-t1-micro-instances/](http://thehayden.org/when-to-use-amazon-ec2-t1-micro-instances/)

So please don't take this to say that I'm saying you can't run LAMP based websites with 512MB or less. Yes you can be each setup differs and in your case your screenshots are saying you should increase RAM.

Next we'll need to audit Apache, PHP & MySQL and optimize them to be more efficient to fit available hardware.

---


---
title: "Apache - MaxClients and ServerLimit - doesn't seem to set?"
date: 2009-11-01
forum: Server Platforms
---

### Post by victorhooi on 2009-11-01
heya,

We're serving a PHP-based website off a 9.10 image on Amazon's EC2 cloud.

According to one of the other guys, the site seemed to become periodically inaccessible, and required a restart of Apache2.

I checked the output from Munin, and the CPU load, memory, and I/O all seem to be fine.

However, in the Apache error logs, there were lines like:
```
[error] server reached MaxClients setting, consider raising the MaxClients setting
```.

In /etc/apache2/apache2.conf, it was set:
```
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>
...
<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>
```

I checked the output from apache2ctl status, and it was:
```
Apache Server Status for localhost                         

Server Version: Apache/2.2.12 (Ubuntu) PHP/5.2.10-2ubuntu6 with Suhosin-Patch
    mod_python/3.3.1 Python/2.6.4rc2                                         
Server Built: Aug 18 2009 13:02:37                                           

-------------------------------------------------------------------------------

Current Time: Monday, 02-Nov-2009 09:13:58 EST
Restart Time: Sunday, 01-Nov-2009 23:32:23 EST
Parent Server Generation: 1                   
Server uptime: 9 hours 41 minutes 35 seconds  
150 requests currently being processed, 0 idle workers

WWWKWWWWWWWWWWWWWWKKWWWWWWWKWWKWCKKWWWWKWWWWWWWWWWKKWWWKWKKWWWWW
WWKWWWWWKWWWWWWWWWWWWWWKWKWWWWWKWWWWWWWWWWWKWWWWWWWWWWKWWCWWWKKK
KKWWWWWKWWWWKWWWKKWKKC..........................................
................................................................

Scoreboard Key:
"_" Waiting for Connection, "S" Starting up, "R" Reading Request,
"W" Sending Reply, "K" Keepalive (read), "D" DNS Lookup,         
"C" Closing connection, "L" Logging, "G" Gracefully finishing,   
"I" Idle cleanup of worker, "." Open slot with no current process
```

Anyhow, I increased the MaxClients line for the prefork and worker module to 450, however, when I restarted Apache, it complained:
```
WARNING: MaxClients of 450 exceeds ServerLimit value of 256 servers,
 lowering MaxClients to 256.  To increase, please see the ServerLimit
 directive.
 ... waiting WARNING: MaxClients of 450 exceeds ServerLimit value of 256 servers,
 lowering MaxClients to 256.  To increase, please see the ServerLimit
 directive.
```
I couldn't seem to find any mention of ServerLimit in the Apache config file, so I added a new line, "Server Limit 450" to both the perfork and worker section.

However, Apache still gives the same error when you restart. Is this meant to be set somewhere else?

Also, I was wondering, the MaxRequestsPerChild - is that meant to be set to 0?

Cheers,
Victor

---

### Post by mrsteveman1 on 2009-11-02
You must actually stop apache and start it again to change ServerLimit, you can't just issue a restart.

I assume you're using the prefork module if you are hosting a PHP application, and i assume you're using mod_php and not a fastcgi setup. Right? 

If you don't know, run "apache2 -V" in a terminal and check the "server mpm" setting.

With prefork, MaxRequestsPerChild is the maximum number of requests that each process can service before it is recycled, a sane number there would be 10,000 for starters, when it hits that number of requests for a process it will be killed and a new one will start up in its place (there is some overhead involved). Setting this to 0 means the processes will just keep serving requests, which may or may not be what you want it to do, depends on the application. If there is a memory leak somewhere, and the processes never die, they will end up killing your server.

If you are actually serving 150+ requests at the same time, either you must have a lot of memory and very high traffic, or you have keepalives or something else configured incorrectly. You should be caching anything you can to keep the load down and serve requests quickly.

---

### Post by victorhooi on 2009-11-02
heya,

Yeah, I got bitten by that quirk, didn't realised I need to do a full stop =). Thanks for the tip.

And yes, it's prefork, mod_php.

```
Server version: Apache/2.2.12 (Ubuntu)
Server built:   Aug 18 2009 13:02:37
Server's Module Magic Number: 20051115:23
Server loaded:  APR 1.3.8, APR-Util 1.3.9
Compiled using: APR 1.3.8, APR-Util 1.3.9
Architecture:   32-bit
Server MPM:     Prefork
  threaded:     no
    forked:     yes (variable process count)
Server compiled with....
 -D APACHE_MPM_DIR="server/mpm/prefork"
 -D APR_HAS_SENDFILE
 -D APR_HAS_MMAP
 -D APR_HAVE_IPV6 (IPv4-mapped addresses enabled)
 -D APR_USE_SYSVSEM_SERIALIZE
 -D APR_USE_PTHREAD_SERIALIZE
 -D SINGLE_LISTEN_UNSERIALIZED_ACCEPT
 -D APR_HAS_OTHER_CHILD
 -D AP_HAVE_RELIABLE_PIPED_LOGS
 -D DYNAMIC_MODULE_LIMIT=128
 -D HTTPD_ROOT=""
 -D SUEXEC_BIN="/usr/lib/apache2/suexec"
 -D DEFAULT_PIDLOG="/var/run/apache2.pid"
 -D DEFAULT_SCOREBOARD="logs/apache_runtime_status"
 -D DEFAULT_LOCKFILE="/var/run/apache2/accept.lock"
 -D DEFAULT_ERRORLOG="logs/error_log"
 -D AP_TYPES_CONFIG_FILE="/etc/apache2/mime.types"
 -D SERVER_CONFIG_FILE="/etc/apache2/apache2.conf"
```

Currently, we're serving around 40-50 requests at a time, sometimes it goes up to 80 or so. I'm not sure how it spiked above 150 before. Do you think that's indicative of a leak, or configuration issue? Any general hints for tracking something like this down?

Also, regarding caching, I don't believe we've got anything setup at the moment. Do you think there's any value in looking at someting like Nginx, and getting it to cache, and proxy stuff to Apache? 

Cheers,
Victor

PS:I know for some of these questions, I might need to provide more info - I'm happy to provide any info, just not sure what to post - ask (and perhaps tell me where to get it), and I'll post it.

---

### Post by mrsteveman1 on 2009-11-02
Try reducing the apache keepalive setting to less than 7 seconds, that should prevent connections that aren't being used from staying open too long (Each one eats an apache process that could be doing other things). If your server isn't done serving a page after 7 seconds other optimizations are needed.

Otherwise if you constantly see a lot of connections open, you probably have a lot of concurrent traffic, or your application or database are taking a long time to serve pages, which is where caching helps.

If your application supports it, some of them can do caching natively or through a plugin, like wordpress has W3 Total Cache. That will be an easy way to reduce apache load quickly.

If you do have a lot of traffic though you will want to look into a proxy like nginx to keep the apache load (mostly memory if you're already doing application caching), down.

---

### Post by victorhooi on 2009-11-02
heya,

Just checked again, it's around 380 to 400 connections at the moment.
```
Apache Server Status for localhost                               

Server Version: Apache/2.2.12 (Ubuntu) PHP/5.2.10-2ubuntu6 with Suhosin-Patch
    mod_python/3.3.1 Python/2.6.4rc2                                         
Server Built: Aug 18 2009 13:02:37                                           

-------------------------------------------------------------------------------

Current Time: Tuesday, 03-Nov-2009 13:01:37 EST
Restart Time: Monday, 02-Nov-2009 18:12:27 EST 
Parent Server Generation: 0                    
Server uptime: 18 hours 49 minutes 10 seconds  
410 requests currently being processed, 7 idle workers

WWWWWWWWWWWKWWWWWWWWWWWWWWWWWWWWWW.WWWWWWWWWWWWWWWWWWWWWWWKWWWWW
WWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWW
WWWWWWWWWWWWWW.WWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWW
WWWWWWWWWWWWWKWWWWCWWWWWWWWKWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWW_W
WWWWW.WWW_WWWWWKWWWWWWWWKWWWWWWWWWWWKWWW.WWWWWWWC.WWWWWWWWKWWWWW
WWWWWWWWWWWWWWC_KWWWWC_W.WWWWWWWWWWWKCW.KWKWWWWCWKWWWWWWWW.WKKKK
WW.WWKWWWWC.W.KW.WCKKWWKK._KKW_KKK.K._WK.KKKKKKK..K.............
..                                                              

Scoreboard Key:
"_" Waiting for Connection, "S" Starting up, "R" Reading Request,
"W" Sending Reply, "K" Keepalive (read), "D" DNS Lookup,         
"C" Closing connection, "L" Logging, "G" Gracefully finishing,   
"I" Idle cleanup of worker, "." Open slot with no current process
```

and then later, again:
 
```
Apache Server Status for localhost

Server Version: Apache/2.2.12 (Ubuntu) PHP/5.2.10-2ubuntu6 with Suhosin-Patch
    mod_python/3.3.1 Python/2.6.4rc2
Server Built: Aug 18 2009 13:02:37

-------------------------------------------------------------------------------

Current Time: Tuesday, 03-Nov-2009 13:12:27 EST
Restart Time: Monday, 02-Nov-2009 18:12:27 EST
Parent Server Generation: 0
Server uptime: 18 hours 59 minutes 59 seconds
394 requests currently being processed, 7 idle workers

WWWWWWWWWWWKWWWWWWWWWWKWWWW_WWWWWW.WWWWWWWWWWWWWKW.WWWWWWW.WWKWW
WWWWWWWWW_WWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWW
WWWWWWWWWWWWWWKWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWW.
WWWWWWWWWWWWWKWWWWKWWWWWWWWKWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWW.W
WWWWWKWWWKWWWWW_WWWWWWWWWWWWWWWWWWWKKWWW_WWWWWWWKWWWWWWWWW.WWWWW
WWWWWWWWWWWWWWKKKWWWW.KW.WWWWWWWWWWWWKWK.WKWW.WKWKWWWWWWWWKWWW.K
WWKWW_WWWWWKWKKW.W...WWK.W._.W..KK._K.W.........................
..

Scoreboard Key:
"_" Waiting for Connection, "S" Starting up, "R" Reading Request,
"W" Sending Reply, "K" Keepalive (read), "D" DNS Lookup,
"C" Closing connection, "L" Logging, "G" Gracefully finishing,
"I" Idle cleanup of worker, "." Open slot with no current process
```

It's currently around 8-9pm in the US, so I'm guessing a lot of that's legitimate traffic, and it's just busy.

So you think I should set "KeepAliveTimeout 7", or less? What's a good way to find out what the hit-profile is like, and how long clients are holding connections open, on what requests?

Currently, our memory usage isn't too bad (it's an Amazon EC2 small instance, with 1.7 Gb). According to Munin, it's 1.02 Gb to apps, and around 450 Mb to cache, 100Mb unused (and other smaller stuff).

But yeah, I guess we probably want to look at getting something like Nginx setup. Is something like Nginx and php-fpm hard to get up on Ubuntu? Or is there a different setup recommended for Ubuntu?

Cheers,
Victor

---

### Post by mrsteveman1 on 2009-11-02
Well, according to the readout you posted, most of those connections aren't actually in keepalive state...... hadn't noticed that before. Keepalives probably aren't hurting anything for you right now, but they certainly shouldn't be set very high anyhow.

Profiling a sites performance isn't too hard, the apache "ab" tool can show you some basic stats per-page (take caching into account if you do this, cached pages will always return fast). There are other ways to directly profile php applications but it isn't something i've done before, perhaps someone else can chime in :)

As always lots of things depend on the application, if your site serves a lot of content that never changes (single pages, jpg files, css files) you can setup nginx to serve those things, and pass dynamic requests back to apache. This is a very well documented setup, i'm sure there are tutorials on the ubuntu forum on how to set it up.

You can also have nginx cache whole pages for you, something i'm not as familiar with. 

In either case apache is still the one executing code, so you don't need any cgi modules for nginx, only setting it up in front of apache with the right config. 

Does that help?

---

### Post by mrsteveman1 on 2009-11-02
This looks like good info on profiling a php application directly:

[http://www.linuxjournal.com/article/7213]("http://www.linuxjournal.com/article/7213")

---


---
title: "Apache2 High load web server"
date: 2008-09-12
forum: Server Platforms
---

### Post by Hungry Snail on 2008-09-12
Hi Guys,

Was hoping for some help in tweaking/optimising my apache2.conf.

It is a dedicated web server (no mysql running on it).
Dual Core, Dual Opteron
4Gb memory
raid 1

At peak time the CPU usage us about 84%, earlier today the server locked up (although it was still pingable) and ever since then webpages have been really slow to load, and often give a "page cannot be displayed" error.

I have removed all the commented out lines so it does not take up so much space when posting, the actual config has the commented out lines.


### Section 1: Global Environment

ServerRoot "/etc/apache2"
PidFile ${APACHE_PID_FILE}
Timeout 300
KeepAlive On
MaxKeepAliveRequests 800
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
##

<IfModule mpm_prefork_module>
    ServerLimit          2000
    StartServers         5
    MinSpareServers      5
    MaxSpareServers      10
    MaxClients           2000
    MaxRequestsPerChild  0
</IfModule>

User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}


AccessFileName .htaccess


<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>


DefaultType text/plain
HostnameLookups Off
ErrorLog /var/log/apache2/error.log
LogLevel warn
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
Include /etc/apache2/httpd.conf
Include /etc/apache2/ports.conf
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent
ServerTokens Full
ServerSignature On
Include /etc/apache2/conf.d/
Include /etc/apache2/sites-enabled/

Thanks in advance.

---

### Post by windependence on 2008-09-13
OK, I will need a bit more info to get a feel for what you are doing. Are you servering just static web pages or what kind of content do yo have there if not an SQL database? How many page views (not hits) do you get per day. What kind of site is it ie. blog, forum, etc.? Also, what kind of netowrk connections do you have on the LAN and WAN?

-Tim

---

### Post by Hungry Snail on 2008-09-13
Hi,

It is serving ads across our websites, we have a sql database, its just on a different server.

The Apache server-status has the following.

Server uptime: 14 hours 39 minutes 41 seconds 
Total accesses: 5659608 - Total Traffic: 2.8 GB 
CPU Usage: u3490.02 s191 cu0 cs0 - 6.97% CPU load 
107 requests/sec - 55.2 kB/second - 527 B/request 
489 requests currently being processed, 41 idle workers 

It is running on a 100mb external connection, and Gb internal connection.

I made a couple of changes to the config last night, and it seems to be running a lot better, but as I am no apache expert it may still be seriously unoptimised,

I changed the following.

KeepAliveTimeout 10
Timeout 150


<IfModule mpm_prefork_module>
    ServerLimit          1000
    StartServers         5
    MinSpareServers      5
    MaxSpareServers      10
    MaxClients           1000
    MaxRequestsPerChild  1000
</IfModule>

Cheers

---

### Post by hyper_ch on 2008-09-13
if you want a high load webserver why not using lighttpd instead?

---

### Post by windependence on 2008-09-13
> **hyper_ch said:**
> if you want a high load webserver why not using lighttpd instead?

Why, when Apache is a more mature product and the de facto standard? I am genuinely interested if you know something I don't ;)

@Hungry Snail, I will be able to post some info for you later tonight when I get to work. I'll give you some ideas then. Are you serving this site over a DSL line, or is it a dedicated line such as a T1 or T3?

-Tim

---

### Post by hyper_ch on 2008-09-13
because apache is heavy compared to lighttpd and if you want a high load server you want something light. As the TO said there's no mysql invovled... furthermore there's probably no php either or any dynamic language. So lighttpd would be a wise choice ;)

---

### Post by syadnom on 2008-09-13
agreed.  lighttpd true to it's name.  For such a simple purpose lighttpd will perform faster in it's stock configuration than a highly tweaked apache config.

Apache is an awesome, highly complex webserver but lighttpd is an awesome, nice and simple webserver that will suit this purpose much better.

Also, choosing lighttpd does not lock you in to some special design, you can switch to apache at any time.  

FYI, you can run apache and lighttpd side by side on the same server as long as they both serve content on different ports!

---

### Post by windependence on 2008-09-13
I'm aware that it's faster, I just wonder if it's as scalable as Apache. The OP asked about a high volume server, although from the info he posted, I don't think his traffic is very heavy right now at all, but maybe he is looking ahead a bit.

-Tim

---

### Post by Hungry Snail on 2008-09-13
> **windependence said:**
> Why, when Apache is a more mature product and the de facto standard? I am genuinely interested if you know something I don't ;)

@Hungry Snail, I will be able to post some info for you later tonight when I get to work. I'll give you some ideas then. Are you serving this site over a DSL line, or is it a dedicated line such as a T1 or T3?

-Tim

Hi Tim,

It's a dedicated line (connected to a 100mb port on a cisco switch which has a gigabite connection going into it)

---

### Post by syadnom on 2008-09-14
I guess a better question is, how much bandwith could be running through this.  Could you actually be delivering 100Mb or is that just the interface speed to the cisco.

I still think that a basic lighttpd will be the fastest if you just want to server static content without complicating things.  

What else you could consider is doing a reverse proxy with squid.  If you have enough RAM (which depends on the content), then you could use RAM as the squid cache.  Squid's cache query mechanism is much much faster than apache or lighttpd's page delivery mechanism even for static content because it is much simpler.

good luck

---

### Post by windependence on 2008-09-14
@syadnom, I agree with you for the traffic he has now, lighthttpd should be just fine. I'm sure it's not at 100mb since a T1 is only 1.5mb. I doubt seriously that bandwidth is a problem here, but I do agree that a reverse proxy would speed things up IF he gets a lot of concurrent requests.

-Tim

---

### Post by syadnom on 2008-09-14
a single T1 doesnt really fix the "high load" webserver part if it serving static content.  If there was a ton of CGI or PHP or some other server side processing it might demand more performance but a T1 is only 192KB/s.  

For some perspective, I run a site on a 20Mb Fiber line.  I have 1 web server and a seperate mysql server.  I run a lot of php but it is basic stuff like <!php include file.html !> or mysql lookups and I have times that the whole pipe is saturated and the server is calmly handling all the requests with moderate load.  The server is a dual core 3Ghz + 8GB RAM and a simple md mirror.  The mysql server is the same specs except has mysql sitting on  a 4 drive raid5 as I do mostly reads so wasnt terribly concerned with raid5 parity penalty on writes.  

for those that want Byte speeds, that is about 2.5MB/s.

this is running apache 2.2.8 on ubuntu 8.04 64bit and the mysql is also on ubuntu 8.04 64bit  (recent update, was on 7.04 for both)

I also run lighttpd on the same server on a different port for some employee access pages and webdav, and those server the internal network which as about 100 users on 100Mb ethernet and have 500 more comming in over my VPN which is on another partition of 20Mb on that fiber.

I used to run this all with a single apache setup but had some performance issues with the internal users which was mainly because of the webdav.  

I switched the internal site over to lighttpd and the webdav to lighttpd and now the same server, with the same amount of traffic performs much better.

I dont mean to say apache is not awesome, because it really is.  It is my first choice in webserver the vast majority of the time BUT lighttpd is an amazing LITTLE webserver and is much faster at doing the things it does because of sheer simplicity.

I have never seen a faster webdav server.  I have run apache1, apache2, and MS ISS and nothing is as fast.

one weakness of lighttpd is speed of php execution.  it can handle php and simply php is nice and fast(maybe faster than apache) but it does not scale up like apache does when running lots of php or lots of simultaneous php.


Good luck.

---


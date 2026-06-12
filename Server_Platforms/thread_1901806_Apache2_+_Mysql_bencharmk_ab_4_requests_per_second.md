---
title: "Apache2 + Mysql bencharmk ab 4 requests per second"
date: 2011-12-29
forum: Server Platforms
---

### Post by pmla on 2011-12-29
Hi,

It's official. I have the worse apache2 + php + mysql ever running on Ubuntu server 10.04LTS 64x.
Dual CPU Xeon 3,2 dual core = 8 cores
3GB RAM
800GB SAS

My best benchmar using apachebench is:
ab -n 500 -c 20 [http://www.example.com/](http://www.example.com/)
```
Server Software:        Apache/2.2.14
Server Hostname:        www.example.com
Server Port:            80

Document Path:          /
Document Length:        20590 bytes

Concurrency Level:      90
Time taken for tests:   231.692 seconds
Complete requests:      1000
Failed requests:        106
   (Connect: 0, Receive: 0, Length: 106, Exceptions: 0)
Write errors:           0
Total transferred:      18923080 bytes
HTML transferred:       18410852 bytes
Requests per second:    4.32 [#/sec] (mean)
Time per request:       20852.285 [ms] (mean)
Time per request:       231.692 [ms] (mean, across all concurrent requests)
Transfer rate:          79.76 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0    0   0.8      0       3
Processing:    99 20433 8935.3  21352   44022
Waiting:       99 19119 8354.0  20284   42850
Total:         99 20433 8935.3  21352   44022

```

By now I bench marked pretty much all hardware faults:
Processor	8x Intel(R) Xeon(TM) CPU 3.20GHz
Memory	3090MB (799MB used)
Operating System	Ubuntu 10.04.3 LTS
**CPU Bench using hardinfo:**
```
CPU Blowfish
This Machine	3192 MHz	3.450
CPU CryptoHash
This Machine	3192 MHz	369.540
```
**Hard Drive Bench using hdparm -t /dev/sda**
```
/dev/sda:
 Timing buffered disk reads:  780 MB in  3.01 seconds = 259.42 MB/sec
```

So...that leaves me with software configuration.
apache2.conf
```
TimeOut 300
KeepAlive on
MaxKeepAliveRequests 100
KeepAliveTimeout 5
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>
<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>
```
I tested running apache2 with startservers8,4 but results got worse, so the default seems to work best.
Also I disabled all logging in apache2.conf and the virtualhosts, getting desperate :)

MYSQL, my.conf
```
[client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock


[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0

[mysqld]
#skip-innodb
skip-name-resolve
# END SKIPPING THINGS
user            = mysql
socket = /var/run/mysqld/mysqld.sock
port = 3306
basedir         = /usr
datadir = /var/lib/mysql
tmpdir          = /tmp
skip-external-locking
bind-address = 127.0.0.1
key_buffer              = 64M
max_allowed_packet      = 16M
thread_stack            = 192K
thread_cache_size       = 64
myisam-recover          = BACKUP
query_cache_limit       = 64M
query_cache_size        = 128M
query_cache_type        = 1
join_buffer_size        = 512K
max_connections         = 90
log_error               = /var/log/mysql/error.log
#log_slow_queries        = /var/log/mysql/mysql-slow.log
expire_logs_days        = 2
max_binlog_size         = 100M
# Try number of CPU's*2 for thread_concurrency
#thread_concurrency     = 4
wait_timeout            = 10

[mysqldump]
quick
quote-names
max_allowed_packet      = 16M

[mysql]


[isamchk]
key_buffer              = 16M
#key_buffer = 150M
#sort_buffer = 64M
#read_buffer = 16M
#write_buffer = 16M

[myisamchk]
#key_buffer = 150M
#sort_buffer = 64M
#read_buffer = 16M
#write_buffer = 16M
!includedir /etc/mysql/conf.d/
```
I tested the memory and swap for the key_buffer, right now is set to 64M, but i also tested with 16M, 32M and 128M.
64M and 128M seems to provide the best results... but still extremely low:
Requests per second:    4.40 [#/sec] (mean)
Requests per second:    4.69 [#/sec] (mean) WOW my best result ever?!?! :)

Also removed all dns queries from apache2 and mysql, so it does not take time to resolve hostnames, IP based only.

Tested DNS (pointed at google DNS), tested the network card, seems normal.

I'm out of ideas?!
p.s. Sorry for the long post.

---

### Post by rubylaser on 2011-12-29
Just a few questions:
1. What is the content for the page you're trying to serve?
2. Is there a programming language involved, or straight HTML?
3. Have you run your benchmark against other webservers with pages of similar length?

---

### Post by pmla on 2011-12-29
Hi,

The content is php, and 13 js scripts.
It's a joomla website + jomsocial.

Now I have other hosts, just joomla so the js is smaller and I get around 9 requests per second.

This one as jomsocial component on top. It's a really bad component when it comes to server speeds and js... among other things.

testing against other servers that use joomla+jomsocial
[http://people.joomla.org/](http://people.joomla.org/)
Requests per second:    8.63 [#/sec] (mean)
[https://www.linux.com/community](https://www.linux.com/community)
Requests per second:    45.23 [#/sec] (mean)

---

### Post by rubylaser on 2011-12-29
> **pmla said:**
> Hi,

The content is php, and 13 js scripts.
It's a joomla website + jomsocial.

Now I have other hosts, just joomla so the js is smaller and I get around 9 requests per second.

This one as jomsocial component on top. It's a really bad component when it comes to server speeds and js... among other things.

testing against other servers that use joomla+jomsocial
[http://people.joomla.org/](http://people.joomla.org/)
Requests per second:    8.63 [#/sec] (mean)
[https://www.linux.com/community](https://www.linux.com/community)
Requests per second:    45.23 [#/sec] (mean)

13 Javascripts! ;) Have you tried consolidating them, and [minifying them as well]("http://developer.yahoo.com/performance/rules.html")?  Also, are the javascripts in separate files so that they can be cached by the browser, rather than inline (this won't effect ab, but it's a good practice)?

I haven't used Joomla in years and I've never used jomsocial, but [this looks promising]("http://www.jomsocial.com/download/addons/core-enhancements/speedbooster-for-joomla-a-jomsocial.html").

---

### Post by pmla on 2011-12-29
Thanks for your help.

Link of consolidating and minifying js is for joomla 1.5 (running 1.7)
But I have tried a bunch of plugins... and they all mess one or another part/function of the website.
Because in joomla you will need other components than just jomsocial, i.e. mailing list component, polls, faq, etc. So, there is always 1 or 2 that get messed up. No perfect solution for that yet.

Everything is related, but what you are mentioning I think it affects more the:
Time per request:       231.692 [ms] (mean, across all concurrent requests)
And that is kinda ok.
For me it's somewhat mind boggling that an 8 core 3,2 xeon with SAS drives can only server 3 to 4 request per second ôÔ

---

### Post by rubylaser on 2011-12-29
Like I said, it's been a long time since I've used Joomla, and that was for a reason :)  Your machine should support MANY more requests per second than that.  The code sounds inefficient and buggy.  If I don't roll my own apps with RoR, I fall back to Wordpress for a quick website.  

I just grabbed a quick page from our corporate website as a test.  It's not quite as big, but still a decent sized page.  This is on an ESXi box with 2 cores and 4GB of RAM.  This is a custom Ruby on Rails application and contains consolidated / minified Javascript and CSS files.  This uses a MySQL database and Apache + Passenger.

```

Rubylasers-MacBook-Pro ~ $ ab -n 500 -c 20 http://www.domain.com/company/

Server Software:        Apache/2.2.14
Server Hostname:        www.example.com
Server Port:            80

Document Path:          /company/
Document Length:        13530 bytes

Concurrency Level:      20
Time taken for tests:   3.732 seconds
Complete requests:      500
Failed requests:        0
Write errors:           0
Total transferred:      7074127 bytes
HTML transferred:       6765000 bytes
Requests per second:    133.99 [#/sec] (mean)
Time per request:       149.264 [ms] (mean)
Time per request:       7.463 [ms] (mean, across all concurrent requests)
Transfer rate:          1851.31 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        1  141  99.8    127    1048
Processing:     0    4  23.0      0     175
Waiting:        0    4  22.3      0     174
Total:         48  146 108.6    129    1223

```

---

### Post by pmla on 2011-12-29
Agree with you "code sounds inefficient and buggy". Not the joomla CMS but the component Jomsocial is extremely buggy (most of the times doesn't even work in IE8 and IE9).

Basically they have huge fat PHP and CSS... and ohhh boy, their js is just ridiculous, just a few:
/plugins/system/azrul.system/pc_includes/ajax_1.5.pack.js
/com_community/assets/minitip-1.0.js
/com_community/assets/joms.ajax.js
/com_community/assets/window-1.0.js
/com_community/assets/script-1.2.js
/com_community/assets/joms.jquery.js

Using the [http://www.webpagetest.org](http://www.webpagetest.org)
MIME Type&#8195;	Bytes&#9660;
js	314732
css	70914

Many users pointed this out, but no avail. They have their agenda for making sales and are clearly not concerned with bugs and website optimization.

So, without a fact... any website with jomsocial installed will be the sloppiest, slowest ever. Just do the [www.webpagetest.org](www.webpagetest.org) in any website running jomsocial, specially the latest version 2.4.x (worse ever so far).

---

### Post by rubylaser on 2011-12-29
Sorry, I couldn't have the magic bullet to solve the problem, but at least you've identified the issue.

---


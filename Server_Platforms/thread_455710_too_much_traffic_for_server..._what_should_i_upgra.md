---
title: "too much traffic for server... what should i upgrade?"
date: 2007-05-26
forum: Server Platforms
---

### Post by envis on 2007-05-26
look at my server status

Apache Server Status for mydomain.com

Server Version: Apache/2.0.55 (Ubuntu) PHP/5.1.6
Server Built: Sep 27 2006 16:51:31

Current Time: Saturday, 26-May-2007 22:04:12 EDT
Restart Time: Saturday, 26-May-2007 22:00:15 EDT
Parent Server Generation: 0
Server uptime: 3 minutes 57 seconds
Total accesses: 1037 - Total Traffic: 3.6 MB
CPU Usage: u.42 s171.3 cu0 cs0 - 72.5% CPU load
4.38 requests/sec - 15.6 kB/second - 3641 B/request
256 requests currently being processed, 0 idle workers

WWKWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWRWWWWWWWWWWWWWWWW
WWWWWWWWWWWWWCWWWWWWWWWWWKWWWWWWWWWWWWKWWWWWWWWWWWWWWWWWWWWWWWWW
WWWWWWWWWCWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWRWWWWWWWWWWWWWWWW
WWWWWWWWWWWWWWWKWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWW

Scoreboard Key:
"_" Waiting for Connection, "S" Starting up, "R" Reading Request,
"W" Sending Reply, "K" Keepalive (read), "D" DNS Lookup,
"C" Closing connection, "L" Logging, "G" Gracefully finishing,
"I" Idle cleanup of worker, "." Open slot with no current process

Srv	PID	Acc	M	CPU 	SS	Req	Conn	Child	Slot	Client	VHost	Request
0-0	4910	0/2/2	W 	0.82	83	0	0.0	0.01	0.01 	86.150.85.84	movies.mydomain.com	GET / HTTP/1.1
1-0	4911	0/2/2	W 	0.42	5	0	0.0	0.01	0.01 	68.32.37.2	movies.mydomain.com	GET /list.php?movieorserie=0 HTTP/1.1

ect....

its been like that for at least 10 hours today... its almost impossible to get a page from my site...

the CPU load sometimes goes up to 90+%


Current Time: Saturday, 26-May-2007 22:07:23 EDT
Restart Time: Saturday, 26-May-2007 22:00:15 EDT
Parent Server Generation: 0
Server uptime: 7 minutes 8 seconds
Total accesses: 2160 - Total Traffic: 7.8 MB
CPU Usage: u1.64 s364.38 cu0 cs0 - 85.5% CPU load
5.05 requests/sec - 18.7 kB/second - 3796 B/request
256 requests currently being processed, 0 idle workers

WWWWWCWWWWWWWWKWWWWWWWKWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWW
WWWWWWWWWWWRWWWWWWWWWWKWWWKWWWWWWWWWWWWWKWWWWCKWWWWWWWWWWWWWWWWW
WWWWWWWWWWKWWWWWWWWKWWWWWWWKWWWWWWWWWRWWWWWWWWKWWWWKWWWWWWWWWWWW
WKWWWWWKWWWWWWWWKWWWWWWCWWWWWWWWWWWWWWWWWWKWWWWWWKKWWWWWWWWWWWKC


the servers are all full... my maxclients is at 256... if i put it higher... my server seems to have strange problems and kind of crashes... becomes pretty much unusable but not completely but anyways i cant restart it without getting an error when i go over 256 clients and im not talking about the "you need to increase the server limit" error.. .its an error that says unable to use port 80 stopping service...

though the SSH server, FTP server and even the MySQL server (which i access with a second server from home) are running fine!....

do you think that if i bought an extra GIG of RAM i might help my problem?

i tried setting it at more servers for a test and even at 2048 maxclients 2048 serverlimit the 2048 slots were still pretty much filling with WWWWW....

i have no problem when its not traffic peak time...

---

### Post by MrHorus on 2007-05-27
> **envis said:**
> 
do you think that if i bought an extra GIG of RAM i might help my problem?


How can we answer that without knowing the spec of your system as it as just now?

What about if you run top, does it show that httpd is using up all the RAM?
What about the CPU?

---

### Post by envis on 2007-05-27
top - 09:30:49 up 21 min,  1 user,  load average: 216.21, 210.69, 150.57
Tasks: 306 total,   2 running, 304 sleeping,   0 stopped,   0 zombie
Cpu(s): 30.3%us, 69.3%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.4%hi,  0.0%si,  0.0%st
Mem:   1010532k total,   619236k used,   391296k free,   159704k buffers
Swap:  2955920k total,        0k used,  2955920k free,   114948k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3395 mysql     15   0  138m  25m 5372 S 35.0  2.6   3:45.18 mysqld
 3801 www-data  16   0 93776 8064 4312 S 15.7  0.8   0:04.84 apache2
 3676 www-data  15   0 94932 8712 4860 D 15.3  0.9   0:04.69 apache2
 3871 www-data  15   0 94916 8788 4936 S 14.9  0.9   0:02.74 apache2
 3908 www-data  16   0 93824 7916 4164 D 11.7  0.8   0:03.57 apache2
 3712 www-data  17   0 94828 8448 4680 R  5.6  0.8   0:05.38 apache2
 4064 envis     16   0 10896 1492  960 R  0.4  0.1   0:00.04 top
    1 root      16   0  2732  600  476 S  0.0  0.1   0:00.68 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
   10 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kblockd/0
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   12 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
  131 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
  167 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  168 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  169 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  170 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
 1602 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0
 1607 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 1608 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1
 1611 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2
 1612 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3
 1716 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd


where do i see my RAM? is is the "Mem:   1010532k total,   619236k used,   391296k free"?
it seems to show there are some available

this morning its 9h30 am and the server is still so crowed you almost cant get any page, usually its pretty calm on a sunday morning...

i had to restart the server this morning when i woke up even though it usually never crashes at 256 maxclients

Current Time: Sunday, 27-May-2007 09:33:31 EDT
Restart Time: Sunday, 27-May-2007 09:09:47 EDT
Parent Server Generation: 0
Server uptime: 23 minutes 44 seconds
Total accesses: 5524 - Total Traffic: 32.4 MB
CPU Usage: u3.2 s1073.38 cu0 cs0 - 75.6% CPU load
3.88 requests/sec - 23.3 kB/second - 6.0 kB/request
256 requests currently being processed, 0 idle workers

WWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWW
WWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWCWCWWWWWWWWWWWWCWWWWWWWWWWWWWWW
WWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWKWWWWK
WWWWKWWWKWWWWWWWWKWWWWWWWWWWWWWWWWWWCWWWWWWWWWWWWWWWWWWKWWWWWWWW

im on an AMD64, 3000 Mhz CPU, 1 gig of RAM, 250 gig SATA hard drive.. on a NVIDIA mother board that goes with the AMD64 processor... running the site on Ubuntu server 6.10

how can i determine if the traffic is legitimate traffic or not?
i tried to see if ads were getting clicked or not, if ads get clicked, no matter if the traffic is legitimate or not its at least worth it... but im gonna have to wait a bit more today to find out for sure...

yesterday, in a desperate attempt to help my situation, i installed APC (the alternative PHP cache) and also i changed a few links on my page to redirect most of the non-logged-in traffic through a CDN (coral CDN) by addin .nyud.net:8090 at the end of the links only if the user is not logged in (cos changing my domain doesnt work with log in mechanisms)

APC
[http://baheyeldin.com/technology/linux/installing-php-apc-on-ubuntu-dapper-and-debian.html](http://baheyeldin.com/technology/linux/installing-php-apc-on-ubuntu-dapper-and-debian.html)
[http://www.debianadmin.com/php-cache-accelerators-with-installation-tutorials.html](http://www.debianadmin.com/php-cache-accelerators-with-installation-tutorials.html)

CDN and other apache optimizations
[http://blogcritics.org/archives/2006/01/27/175740.php](http://blogcritics.org/archives/2006/01/27/175740.php)
[http://www.coralcdn.org/](http://www.coralcdn.org/)

but even with those things... its still so slow!!! so everwhelmed by traffic... how can io have so much traffic on a Sunday morning like that?...

---

### Post by envis on 2007-05-27
do i need to go ahead and blow full of money on a bigger server or something... i wish i was able to find a way to fix this annoying problem.... but i have difficulty understanding really whats the problem...

---

### Post by envis on 2007-05-27
actually it seems to be legitimate traffic, as i just been slashdotted by digg.com....

i used to not make it at peak time... but now peak time never ends anymore....

---


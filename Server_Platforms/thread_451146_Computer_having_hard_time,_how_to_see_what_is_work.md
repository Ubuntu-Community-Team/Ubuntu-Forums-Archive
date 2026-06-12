---
title: "Computer having hard time, how to see what is working too hard? (Apache crashing)"
date: 2007-05-22
forum: Server Platforms
---

### Post by envis on 2007-05-22
i have a website installed on an AMD 64 3200 MGhz processor, 250 gig SATA hard drive with 1 gig of RAM

i have too much traffic, if i set my apache at 
StartServers          10
MinSpareServers        5
MaxSpareServers       25
ServerLimit          512
MaxClients           384
MaxRequestsPerChild    0
</IfModule>
it ends up crashing when i get traffic peaks
if i set it at
StartServers          10
MinSpareServers        5
MaxSpareServers       25
ServerLimit          512
MaxClients           256
MaxRequestsPerChild    0
</IfModule>
its either Extremely slow or times out during connection peaks..

so basically my conclusion is that the computer hosting the server is not strong enough anymore....

if i do a TOP, (im not on a traffic peak right now, its pretty relax..) i see this:
top - 01:36:23 up  2:35,  1 user,  load average: 1.41, 1.09, 0.99
Tasks:  76 total,   2 running,  74 sleeping,   0 stopped,   0 zombie
Cpu(s): 34.3%us,  9.0%sy,  0.0%ni, 55.0%id,  1.0%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:   1010532k total,   864144k used,   146388k free,   166396k buffers
Swap:  2955920k total,       96k used,  2955824k free,    50808k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3399 mysql     15   0  169m  45m 5416 S 34.6  4.6  31:46.31 mysqld
 8228 www-data  15   0 63396 8004 3808 S  2.7  0.8   1:10.57 apache2
 7828 www-data  15   0 63384 7976 3792 S  0.7  0.8   1:04.86 apache2
10629 www-data  15   0 63428 7992 3768 S  0.7  0.8   0:19.31 apache2
 8030 www-data  15   0 63412 8040 3828 S  0.3  0.8   0:58.97 apache2
 8181 www-data  15   0 63396 8000 3804 S  0.3  0.8   1:02.66 apache2
 8206 www-data  15   0 63452 8056 3808 S  0.3  0.8   1:01.58 apache2
 8599 www-data  15   0 63380 7940 3796 S  0.3  0.8   0:56.16 apache2
 9173 www-data  16   0 63404 7988 3792 S  0.3  0.8   0:56.74 apache2
 9864 www-data  16   0 63416 8060 3848 S  0.3  0.8   0:44.64 apache2
 9914 www-data  15   0 63424 8004 3780 S  0.3  0.8   0:36.46 apache2
10541 www-data  15   0 63376 7968 3792 S  0.3  0.8   0:22.71 apache2
10544 www-data  15   0 63312 7872 3760 S  0.3  0.8   0:18.97 apache2
10545 www-data  15   0 63376 7940 3800 S  0.3  0.8   0:23.96 apache2
10549 www-data  15   0 63432 8004 3772 S  0.3  0.8   0:17.26 apache2
10576 www-data  16   0 63356 7904 3784 S  0.3  0.8   0:20.77 apache2
10614 www-data  16   0 63368 7916 3760 S  0.3  0.8   0:19.64 apache2

i dont know what the 9.0%sy means, but this one very often reaches very close to 100%

the CPU usually is between 10% and 30%, sometimes goes up to 50%

when the server "crashes" what happens is that 1 site becomes unreachable.. it times out after a long wait, 2 i can still SSH in the box but its really Reeally super slow... and 3 trying to restart apache gives me
envis@mybox:~$ sudo /etc/init.d/apache2 restart
* Forcing reload of apache 2.0 web server... [Sat May 12 15:37:57 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
(98): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
[fail]
envis@mybox:~$

when that happens i have usually to reset the box (sudo shutdown -r now) but these days that not enough, i also need to lower the settings first (the apache settings)... and then reset...

im not too knowledgeable in hardware, and googling for that problem is complicated... can anybody give me some guidelines? their opinion?....

should i go ahead and buy myself another couple of Gigs of RAM.. buy a SCSI hard-drive? buy a special computer specifically made to be a webserver? ([http://www.microbytes.com/computer/ordinateur/product_info.php?cPath=1920000&products_id=24977](http://www.microbytes.com/computer/ordinateur/product_info.php?cPath=1920000&products_id=24977))... do you think theres something wrong in my settings? that im getting hacked?

by the way, when restarting apache, when it says * Forcing reload of apache 2.0 web server... [Sat May 12 15:37:57 2007] [warn] NameVirtualHost *:0 has no VirtualHosts thats not really a problem.. well, maybe it is but it always said that... i have no idea what it means but it says that too when the server is working fine...

the problem part is the
(98): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
[fail]

---

### Post by MJN on 2007-05-22
This again?!

Firstly, **leave the config alone**! How many times do we need to tell you this? You're fiddling with the figures like a monkey on a typewriter and without any feedback measurement (other than either the server crashes or it doesn't) you'll never reach your goal!

Did you implement the load measurement techniques I mentioned last time you asked?

Mathew

---

### Post by envis on 2007-05-23
but i had to play with the config... i left the config along for a long time maybe 6 months and then someday it needed to be boosted... the basic config is like what? maxClients = 20 thats not enough for the people wanting to access my little site... i have approximatively a million hits per day.. on bad days its half a million... with maxClients = 256 i dont have any crash ever but its almost unreachable during peaktime (maybe 15% of the time, american evenings..)  with maxClients = 300 it ends up crashing during peaktime

ok.. ok... im gonna try implementing the load measurement techniques you told me about... i didnt in the first place cos i judged it was gonna be extra load

---

### Post by envis on 2007-05-23
> Try this...

Add the following to your <Virtualhost> config:

Code:

<Location /status>
SetHandler server-status
</Location>

and, optionally given there can be a slight performance hit (but it's worth it given the extra output) add Extendedstatus on to /etc/apache2/apache2.conf.

Restart Apache and got to /status and you'll see a whole load of performance info which is essential if you're going to tweak performance options. Doing it 'blind' is futile - you need feedback on the results so you can identify the bottlenecks.

im trying to implement this to my server...

im a bit confused when you say to add that to my Virtualhost config

i have many virtual host configs theyre in my "sites-available" folder

though i have that at the end of my apache2.conf

# Allow server status reports, with the URL of [http://servername/server-status](http://servername/server-status)
# Change the ".your_domain.com" to match your domain to enable.
#
#<Location /server-status>
#    SetHandler server-status
#</Location>

# Allow remote server configuration reports, with the URL of
#  [http://servername/server-info](http://servername/server-info) (requires that mod_info.c be loaded).
# Change the ".your_domain.com" to match your domain to enable.
#
#<Location /server-info>
#    SetHandler server-info
#    Order deny,allow
#    Deny from all
#    Allow from .your_domain.com
#</Location>

so i changed that part like this:

# Allow server status reports, with the URL of [http://servername/server-status](http://servername/server-status)
# Change the ".your_domain.com" to match your domain to enable.
#
<Location /server-status>
    SetHandler server-status
</Location>

Extendedstatus on

# Allow remote server configuration reports, with the URL of
#  [http://servername/server-info](http://servername/server-info) (requires that mod_info.c be loaded).
# Change the ".your_domain.com" to match your domain to enable.
#
#<Location /server-info>
#    SetHandler server-info
#    Order deny,allow
#    Deny from all
#    Allow from .your_domain.com
#</Location>

and i can see my status now at [http://your.server.name/server-status](http://your.server.name/server-status)


Current Time: Wednesday, 23-May-2007 05:43:58 EDT
Restart Time: Wednesday, 23-May-2007 05:38:02 EDT
Parent Server Generation: 0
Server uptime: 5 minutes 56 seconds
Total accesses: 7117 - Total Traffic: 23.4 MB
CPU Usage: u10.38 s55.2 cu0 cs0 - 18.4% CPU load
20 requests/sec - 67.2 kB/second - 3441 B/request
10 requests currently being processed, 15 idle workers
ect...

can you help me understanding what i need to look for in there?

at the moment the server is working fine... maybe i need to wait for wen it gets slow to see a problem in there...

---

### Post by envis on 2007-05-23
if i understand well.. my actual traffic is tiny:

Current Time: Wednesday, 23-May-2007 05:50:05 EDT
Restart Time: Wednesday, 23-May-2007 05:38:02 EDT
Parent Server Generation: 0
Server uptime: 12 minutes 2 seconds
Total accesses: 14546 - Total Traffic: 46.9 MB
CPU Usage: u21.73 s97.65 cu0 cs0 - 16.5% CPU load
20.1 requests/sec - 66.5 kB/second - 3381 B/request
6 requests currently being processed, 19 idle workers


almost 15000 hits already and not even 50M transfered yet

so maybe it means that the i run too many scripts or something... i have made a script that reads each post before displaying it and finds all the hyperlinks and transforms each of them into an hyperlink with a unique tag id for javascript to be able to apply hover effect to each of them with the colors of this perticular user...
so, thats an example of a script that i think might be demanding for the server...

does it look to you like i could be able to afford raising my maxclients if i just added a few gigs of RAM? i have 1 gig of RAM right now.. i think it could go up to 4 at least...

---

### Post by envis on 2007-05-23
hmm actually the "accesses" are probably not only "hits" from visitors

---

### Post by envis on 2007-05-23
i been looking at my server-status a lot now... look theres something strange

Apache Server Status for lalala.com

Server Version: Apache/2.0.55 (Ubuntu) PHP/5.1.6
Server Built: Sep 27 2006 16:51:31

Current Time: Wednesday, 23-May-2007 21:46:17 EDT
Restart Time: Wednesday, 23-May-2007 05:38:02 EDT
Parent Server Generation: 0
Server uptime: 16 hours 8 minutes 15 seconds
Total accesses: 2312190 - Total Traffic: 6.5 GB
CPU Usage: u92.93 s498.05 cu.01 cs0 - 1.02% CPU load
39.8 requests/sec - 117.9 kB/second - 3032 B/request
42 requests currently being processed, 48 idle workers

W..W...C....W..WW_.WW_.W_.._.___._C..WW_._......W. ...[WWW.___...C](WWW.___...C)
_........W.__C..._W_..WW._W_._.W...W___.W____WWW._ ..W__._.W__.W.
W..._._.._.R__.....__C....W___W_...W.._..W_W_.W... ..............
...................................W.............. ..............
.................................................. ..............
.................................................. ..............
.................................................. ..............
.................................................. ..............

Scoreboard Key:
"_" Waiting for Connection, "S" Starting up, "R" Reading Request,
"W" Sending Reply, "K" Keepalive (read), "D" DNS Lookup,
"C" Closing connection, "L" Logging, "G" Gracefully finishing,
"I" Idle cleanup of worker, "." Open slot with no current process

Srv PID Acc M CPU SS Req Conn Child Slot Client VHost Request
0-0 19898 0/1369/54133 W 7.91 838 0 0.0 3.83 155.63 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
1-0 - 0/0/50512 . 7.17 84 0 0.0 0.00 148.49 71.225.113.104 movies.lalala.com GET /movies.js HTTP/1.1
2-0 - 0/0/51181 . 6.21 18 801 0.0 0.00 152.39 24.190.96.3 movies.lalala.com GET /list.php?movieorserie=0 HTTP/1.1
3-0 20551 0/14/53901 W 0.38 822 0 0.0 0.04 155.36 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
4-0 - 0/0/51630 . 0.42 16 0 0.0 0.00 147.90 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
5-0 - 0/0/49196 . 0.96 9 0 0.0 0.00 140.44 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
6-0 - 0/0/43018 . 0.86 39 1532 0.0 0.00 127.35 66.249.67.117 games.lalala.com GET /?game=47&genre=all&multiplayer=single%20player&pag e=1 HTTP
7-0 20895 1/625/45859 C 4.38 0 0 9.2 1.83 138.66 24.9.219.231 backstage.lalala.com GET /protected_content/29415/userspics/42.gif HTTP/1.1
8-0 - 0/0/45390 . 0.03 57 0 0.0 0.00 131.14 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
9-0 - 0/0/43623 . 0.01 73 0 0.0 0.00 127.73 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
10-0 - 0/0/41382 . 0.17 45 34 0.0 0.00 119.26 67.10.109.28 movies.lalala.com GET / HTTP/1.1
11-0 - 0/0/41026 . 2.30 52 0 0.0 0.00 121.22 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
12-0 19316 0/1944/36935 W 13.44 822 0 0.0 5.17 106.84 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
13-0 - 0/0/33940 . 0.22 35 0 0.0 0.00 96.94 71.126.29.219 movies.lalala.com GET /movies.js HTTP/1.1
14-0 - 0/0/37946 . 8.65 10 333 0.0 0.00 108.97 67.188.52.40 lalala.com GET / HTTP/1.1
15-0 20579 0/1/37064 W 0.00 817 0 0.0 0.00 108.48 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
16-0 16636 0/2451/48290 W 19.36 828 0 0.0 7.30 142.20 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
17-0 21592 0/54/26843 _ 0.26 0 0 0.0 0.20 78.45 68.161.76.194 lalala.com GET /common_files/lalala.css HTTP/1.1
18-0 - 0/0/31075 . 0.45 55 0 0.0 0.00 94.86 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
19-0 20584 0/30/32753 W 0.39 783 0 0.0 0.22 93.16 69.86.233.91 movies.lalala.com GET /links_page.php?movie=1275 HTTP/1.1
20-0 20585 0/31/34753 W 0.35 784 0 0.0 0.08 101.73 69.86.233.91 movies.lalala.com GET /links_page.php?movie=1275 HTTP/1.1
21-0 21594 0/57/33125 _ 0.46 0 0 0.0 0.18 99.03 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
22-0 - 0/0/31969 . 0.45 17 0 0.0 0.00 92.33 127.0.1.1 lalala.com GET /common_files/DOCTYPE.php HTTP/1.0
23-0 20591 0/2/33059 W 0.00 816 0 0.0 0.00 95.81 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
24-0 21675 0/38/37856 _ 0.81 1 0 0.0 0.08 112.81 68.227.197.140 movies.lalala.com GET /divx.php?movie=http://video.stage6.com/1061921/.divx HTTP/
25-0 - 0/0/22893 . 0.80 6 0 0.0 0.00 67.19 127.0.1.1 lalala.com GET /common_files/DOCTYPE.php HTTP/1.0
26-0 - 0/0/34640 . 0.05 74 0 0.0 0.00 100.64 212.1.139.105 lalala.com GET /common_files/pics/tape4rev.ico HTTP/1.1
27-0 21614 0/71/26497 _ 0.10 0 0 0.0 0.18 78.89 70.56.27.29 lalala.com GET /common_files/lalala.css HTTP/1.1
28-0 - 0/0/26868 . 0.04 88 0 0.0 0.00 78.12 127.0.1.1 lalala.com GET /common_files/ads/cpx_leaderboard_ultimate.php HTTP/1.0
29-0 21623 0/57/29945 _ 0.72 0 0 0.0 0.11 87.15 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
30-0 21624 0/63/38580 _ 0.12 0 0 0.0 0.12 115.08 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
31-0 21625 0/55/31735 _ 0.82 0 0 0.0 0.19 95.08 24.136.59.120 lalala.com GET /common_files/pics/play1.gif HTTP/1.1
32-0 - 0/0/22951 . 6.89 85 0 0.0 0.00 69.55 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
33-0 21626 0/44/27837 _ 0.33 2 0 0.0 0.09 84.01 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
34-0 21627 1/65/31119 C 0.44 0 0 1.8 0.11 88.73 71.76.201.134 movies.lalala.com GET /movies.js HTTP/1.1
35-0 - 0/0/29842 . 2.94 87 0 0.0 0.00 87.26 74.222.70.224 lalala.com GET /common_files/lalala.js HTTP/1.1
36-0 - 0/0/17340 . 0.88 26 0 0.0 0.00 50.40 127.0.1.1 lalala.com GET /common_files/ads/cpx_leaderboard_ultimate.php HTTP/1.0
37-0 20609 0/0/18476 W 0.20 815 0 0.0 0.00 53.79 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
38-0 17094 0/1304/16189 W 10.37 821 0 0.0 3.36 42.72 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
39-0 21629 0/58/17278 _ 0.52 1 0 0.0 0.15 50.55 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
40-0 - 0/0/23615 . 0.04 41 0 0.0 0.00 67.58 127.0.1.1 lalala.com GET /common_files/ads/cpx_square.php HTTP/1.0
41-0 21631 0/58/20197 _ 0.84 1 78 0.0 0.11 58.03 74.116.5.244 movies.lalala.com GET /list.php?genre=comedy&movieorserie=0 HTTP/1.1
42-0 - 0/0/21956 . 0.17 43 0 0.0 0.00 61.77 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
43-0 - 0/0/17638 . 0.24 49 0 0.0 0.00 50.52 70.83.18.2 lalala.com GET /common_files/pics/play2.gif HTTP/1.1
44-0 - 0/0/22602 . 6.28 53 86 0.0 0.00 63.66 76.179.0.161 movies.lalala.com GET /list.php?movieorserie=0&alpha=S HTTP/1.1
45-0 - 0/0/19686 . 0.01 91 0 0.0 0.00 57.04 127.0.1.1 lalala.com GET /common_files/DOCTYPE.php HTTP/1.0
46-0 - 0/0/12958 . 2.76 2 0 0.0 0.00 37.11 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
47-0 - 0/0/13825 . 0.47 21 0 0.0 0.00 40.62 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
48-0 21636 0/48/15932 W 0.55 0 0 0.0 0.08 46.49 68.12.224.64 movies.lalala.com GET /links_page.php?movie=122 HTTP/1.1
49-0 - 0/0/19387 . 0.04 28 0 0.0 0.00 55.71 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
50-0 - 0/0/13904 . 0.37 67 0 0.0 0.00 37.90 127.0.1.1 lalala.com GET /common_files/DOCTYPE.php HTTP/1.0
51-0 - 0/0/20818 . 3.78 40 0 0.0 0.00 59.70 70.127.147.46 lalala.com GET /common_files/pics/play2.gif HTTP/1.1
52-0 - 0/0/14629 . 0.18 51 0 0.0 0.00 42.54 70.83.18.2 backstage.lalala.com GET /protected_content/29415/userspics/352.gif HTTP/1.1
53-0 19358 0/1836/10592 W 10.37 831 0 0.0 4.78 29.05 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
54-0 20638 0/2/11252 W 0.00 814 0 0.0 0.00 31.07 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
55-0 20639 0/0/9825 W 2.14 814 0 0.0 0.00 29.48 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
56-0 - 0/0/14073 . 0.36 59 0 0.0 0.00 39.59 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
57-0 21644 0/49/10588 _ 0.56 1 26 0.0 0.10 28.76 69.73.92.20 movies.lalala.com GET / HTTP/1.1
58-0 21645 0/78/10597 _ 0.26 0 286 0.0 0.19 30.31 65.48.54.10 movies.lalala.com GET /links_page.php?movie=1241 HTTP/1.1
59-0 21646 0/58/19392 _ 0.28 0 348 0.0 0.17 57.10 76.177.214.88 movies.lalala.com GET /list.php?movieorserie=0&alpha=T HTTP/1.1
60-0 - 0/0/11526 . 0.04 61 0 0.0 0.00 33.32 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
61-0 - 0/0/8001 . 0.22 20 0 0.0 0.00 22.48 127.0.1.1 lalala.com GET /common_files/ads/cpx_leaderboard_ultimate.php HTTP/1.0
62-0 - 0/0/5886 . 0.23 19 0 0.0 0.00 17.43 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
63-0 21108 1/215/7304 C 1.19 0 633 18.7 0.55 20.59 208.13.217.225 movies.lalala.com GET /links_page.php?movie=768 HTTP/1.1
64-0 21650 0/56/9396 W 0.60 0 0 0.0 0.21 27.29 161.73.37.26 movies.lalala.com GET /list.php?movieorserie=0&alpha=L HTTP/1.1
65-0 - 0/0/16028 . 2.61 60 49 0.0 0.00 45.34 75.25.0.20 movies.lalala.com GET /movies.js HTTP/1.1
66-0 - 0/0/17761 . 0.07 23 80 0.0 0.00 51.26 68.192.126.164 games.lalala.com GET / HTTP/1.1
67-0 - 0/0/8348 . 0.42 30 0 0.0 0.00 21.72 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
68-0 - 0/0/7396 . 0.54 81 0 0.0 0.00 22.56 127.0.1.1 lalala.com GET /common_files/ads/cpx_leaderboard_ultimate.php HTTP/1.0
69-0 - 0/0/5078 . 0.01 79 0 0.0 0.00 13.78 198.53.104.191 lalala.com GET /common_files/lalala.css HTTP/1.1
70-0 - 0/0/14900 . 0.55 76 0 0.0 0.00 47.28 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
71-0 - 0/0/9498 . 0.47 11 246 0.0 0.00 27.96 157.228.101.125 movies.lalala.com GET /list.php?movieorserie=0&page=9 HTTP/1.1
72-0 - 0/0/6266 . 0.38 12 0 0.0 0.00 17.62 24.231.44.231 movies.lalala.com GET /favicon.ico HTTP/1.1
73-0 20658 0/27/8422 W 0.07 783 0 0.0 0.07 23.01 69.86.233.91 movies.lalala.com GET /links_page.php?movie=1275 HTTP/1.1
74-0 - 0/0/8599 . 0.37 75 8218 0.0 0.00 24.26 212.1.139.105 lalala.com GET / HTTP/1.1
75-0 21658 0/50/5926 _ 0.50 1 128 0.0 0.15 16.94 70.127.147.46 movies.lalala.com GET /list.php?movieorserie=0&page=3 HTTP/1.1
76-0 21659 0/52/6709 _ 0.08 1 218 0.0 0.25 18.16 75.35.5.65 movies.lalala.com GET /list.php?movieorserie=0 HTTP/1.1
77-0 21676 0/49/5897 C 0.67 0 0 0.0 0.07 15.84 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
78-0 - 0/0/16716 . 3.85 56 1764 0.0 0.00 47.05 68.229.166.240 movies.lalala.com GET /links_page.php?movie=1238 HTTP/1.1
79-0 - 0/0/3866 . 0.16 50 0 0.0 0.00 11.18 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
80-0 - 0/0/6162 . 0.42 38 0 0.0 0.00 17.03 75.67.7.96 lalala.com GET /common_files/pics/error2.gif HTTP/1.1
81-0 21663 0/51/6216 _ 0.20 0 0 0.0 0.13 18.42 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
82-0 19382 0/1940/7223 W 10.99 827 0 0.0 4.59 20.46 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
83-0 21664 0/36/6221 _ 0.43 0 0 0.0 0.15 18.26 127.0.1.1 lalala.com GET /common_files/DOCTYPE.php HTTP/1.0
84-0 - 0/0/8089 . 2.34 47 340 0.0 0.00 22.98 207.200.116.10 movies.lalala.com GET /list.php?movieorserie=0 HTTP/1.1
85-0 - 0/0/6337 . 0.03 34 281 0.0 0.00 17.04 65.114.16.94 movies.lalala.com GET /list.php?movieorserie=&page=5 HTTP/1.1
86-0 19388 0/1737/9718 W 10.70 836 0 0.0 5.20 28.11 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
87-0 19405 0/942/6383 W 8.35 840 0 0.0 3.24 19.09 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
88-0 - 0/0/6709 . 0.02 65 0 0.0 0.00 18.47 68.19.167.77 lalala.com GET /common_files/lalala.css HTTP/1.1
89-0 21667 0/49/3267 _ 0.08 0 0 0.0 0.10 8.61 127.0.1.1 lalala.com GET /common_files/ads/cpx_leaderboard_ultimate.php HTTP/1.0
90-0 19408 0/1845/8223 W 14.99 831 0 0.0 5.19 24.27 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
91-0 21668 0/50/6254 _ 0.60 1 0 0.0 0.11 16.66 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
92-0 - 0/0/4207 . 0.02 89 16085 0.0 0.00 11.62 68.200.105.0 movies.lalala.com GET /links_page.php?movie=864 HTTP/1.1
93-0 21670 0/55/4304 _ 0.17 0 199 0.0 0.09 12.94 207.200.116.14 movies.lalala.com GET /list.php?movieorserie=0&page=4 HTTP/1.1
94-0 - 0/0/3010 . 0.17 84 644 0.0 0.00 9.11 69.59.255.5 movies.lalala.com GET /shitnaz.php?mi=1311&ln=6 HTTP/1.1
95-0 21672 0/47/3189 W 0.55 0 0 0.0 0.13 9.36 70.127.147.46 movies.lalala.com GET /list.php?movieorserie=0&page=2 HTTP/1.1
96-0 - 0/0/9714 . 3.16 72 6675 0.0 0.00 27.86 71.188.226.46 movies.lalala.com GET /list.php?movieorserie=0&page=4 HTTP/1.1
97-0 - 0/0/11885 . 0.23 31 0 0.0 0.00 35.00 71.161.52.24 lalala.com GET /common_files/lalala.css HTTP/1.1
98-0 - 0/0/5722 . 0.00 86 0 0.0 0.00 16.41 65.71.93.248 movies.lalala.com GET /flvplayer.swf?url=http://www.dailymotion.com/get/14/320x24
99-0 21679 0/53/2166 W 0.08 0 0 0.0 0.14 5.00 69.223.128.60 movies.lalala.com GET /list.php?movieorserie=0&page=2 HTTP/1.1
100-0 21680 0/41/3792 _ 0.40 1 0 0.0 0.12 10.61 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
101-0 21681 0/48/761 _ 1.18 0 0 0.0 0.27 2.32 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
102-0 21682 0/40/2097 _ 0.40 0 0 0.0 0.09 5.32 70.56.27.29 movies.lalala.com GET /movies.js HTTP/1.1
103-0 - 0/0/6723 . 0.01 78 0 0.0 0.00 18.31 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
104-0 19469 0/1449/5818 W 12.69 824 0 0.0 4.27 16.27 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
105-0 21684 0/45/2766 _ 1.17 0 0 0.0 0.15 7.41 24.136.59.120 lalala.com GET /common_files/lalala.css HTTP/1.1
106-0 21685 0/34/8079 _ 0.65 0 0 0.0 0.14 21.56 127.0.1.1 lalala.com GET /common_files/DOCTYPE.php HTTP/1.0
107-0 21143 0/360/10259 _ 4.34 0 493 0.0 1.05 30.95 71.76.201.134 movies.lalala.com GET / HTTP/1.1
108-0 21686 0/40/1689 _ 0.85 0 0 0.0 0.09 5.79 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
109-0 21701 0/52/837 W 0.10 0 0 0.0 0.13 2.85 74.14.248.7 lalala.com GET /server-status HTTP/1.1
110-0 21716 0/37/5714 W 0.21 0 0 0.0 0.11 16.76 68.149.27.109 movies.lalala.com GET / HTTP/1.1
111-0 19481 0/1783/2435 W 9.83 837 0 0.0 4.92 6.49 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
112-0 - 0/0/1000 . 0.18 24 0 0.0 0.00 3.16 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
113-0 21718 0/68/4391 _ 0.20 1 0 0.0 0.11 12.11 127.0.1.1 lalala.com GET /common_files/ads/cpx_square.php HTTP/1.0
114-0 - 0/0/863 . 0.99 25 0 0.0 0.00 2.26 127.0.1.1 lalala.com GET /common_files/ads/firefox.php HTTP/1.0
115-0 - 0/0/929 . 0.11 13 0 0.0 0.00 2.80 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
116-0 21731 1/36/1846 C 0.52 0 491 9.6 0.08 5.05 71.29.73.235 movies.lalala.com GET /?movie=190 HTTP/1.1
117-0 21734 0/46/1440 _ 0.67 0 0 0.0 0.13 4.06 58.110.187.51 lalala.com GET /common_files/lalala.js HTTP/1.1
118-0 21735 0/59/1725 _ 0.10 0 0 0.0 0.12 5.16 71.76.201.134 lalala.com GET /common_files/lalala.css HTTP/1.1
119-0 - 0/0/1664 . 0.05 58 0 0.0 0.00 4.43 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
120-0 21742 0/58/899 _ 0.44 0 0 0.0 0.11 2.51 24.9.219.231 lalala.com GET /common_files/pics/play1.gif HTTP/1.1
121-0 - 0/0/439 . 0.73 77 8198 0.0 0.00 1.69 24.9.219.231 movies.lalala.com GET / HTTP/1.1
122-0 21750 0/50/1477 W 0.04 0 0 0.0 0.07 3.63 151.199.247.232 movies.lalala.com GET /links_page.php?movie=588 HTTP/1.1
123-0 21751 0/52/2191 _ 0.05 0 0 0.0 0.09 6.05 70.56.27.29 lalala.com GET /common_files/pics/tape4rev.ico HTTP/1.1
124-0 21775 0/42/2666 _ 0.09 0 0 0.0 0.09 6.88 127.0.1.1 lalala.com GET /common_files/ads/cpx_leaderboard_ultimate.php HTTP/1.0
125-0 - 0/0/4088 . 4.01 62 0 0.0 0.00 11.04 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
126-0 19496 0/1747/2528 W 9.14 830 0 0.0 5.05 7.07 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
127-0 - 0/0/1540 . 3.49 71 6498 0.0 0.00 4.34 207.38.166.6 movies.lalala.com GET /list.php?movieorserie=0&alpha=J HTTP/1.1
128-0 21237 0/286/4884 W 3.40 0 0 0.0 0.87 12.71 24.44.180.24 movies.lalala.com GET /list.php?movieorserie=0 HTTP/1.1
129-0 - 0/0/1135 . 0.10 22 0 0.0 0.00 3.32 66.214.140.133 lalala.com GET /common_files/pics/error2.gif HTTP/1.1
130-0 - 0/0/887 . 0.02 32 0 0.0 0.00 2.67 209.206.133.219 movies.lalala.com GET /divx.php?movie=http://video.stage6.com/1167925/.divx HTTP/
131-0 - 0/0/939 . 0.05 27 320 0.0 0.00 2.62 66.227.192.182 movies.lalala.com POST / HTTP/1.1
132-0 21788 0/38/1239 _ 0.07 0 942 0.0 0.12 3.52 58.110.187.51 movies.lalala.com GET /links_page.php?movie=106 HTTP/1.1
133-0 - 0/0/3189 . 3.59 1 0 0.0 0.00 8.83 127.0.1.1 lalala.com GET /common_files/ads/google_ad_bottom.php HTTP/1.0
134-0 21789 0/38/3017 _ 0.90 0 0 0.0 0.14 8.07 24.136.59.120 movies.lalala.com GET /divx.php?movie=http://video.stage6.com/1241561/.divx HTTP/
135-0 - 0/0/866 . 0.55 29 0 0.0 0.00 2.55 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
136-0 - 0/0/719 . 0.00 64 0 0.0 0.00 1.96 127.0.1.1 lalala.com GET /common_files/DOCTYPE.php HTTP/1.0
137-0 19506 0/1414/2122 _ 12.11 0 0 0.0 4.24 6.18 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
138-0 - 0/0/471 . 0.01 69 0 0.0 0.00 1.22 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
139-0 21793 0/50/1627 R 0.07 7 0 0.0 0.09 4.23 ? ? ..reading..
140-0 21794 0/38/1135 _ 0.50 1 0 0.0 0.16 3.29 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
141-0 21795 0/57/521 _ 1.16 0 0 0.0 0.17 1.70 71.76.201.134 lalala.com GET /common_files/pics/tape4rev.ico HTTP/1.1
142-0 - 0/0/1380 . 0.77 4 12 0.0 0.00 4.42 207.38.166.6 movies.lalala.com GET /list.php?movieorserie=0&alpha=Y HTTP/1.1
143-0 - 0/0/374 . 0.16 37 0 0.0 0.00 0.62 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
144-0 - 0/0/1047 . 0.03 63 0 0.0 0.00 2.50 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
145-0 - 0/0/545 . 0.03 7 270 0.0 0.00 1.40 84.74.247.35 movies.lalala.com GET /list.php?genre=drama&movieorserie=0 HTTP/1.1
146-0 - 0/0/2340 . 3.04 44 0 0.0 0.00 6.24 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
147-0 21800 0/37/731 _ 0.07 1 0 0.0 0.25 2.36 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
148-0 21256 0/29/1340 _ 0.23 0 0 0.0 0.29 3.46 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
149-0 21801 0/51/552 _ 0.43 0 426 0.0 0.14 1.77 68.161.76.194 movies.lalala.com GET /list.php?movieorserie=2 HTTP/1.1
150-0 - 0/0/4167 . 20.01 54 0 0.0 0.00 12.21 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
151-0 - 0/0/776 . 0.22 14 0 0.0 0.00 2.09 130.39.0.27 movies.lalala.com GET /divx.php?movie=http://video.stage6.com/229866/1093529.divx
152-0 - 0/0/3082 . 0.34 82 0 0.0 0.00 10.91 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
153-0 - 0/0/813 . 0.04 46 0 0.0 0.00 2.30 202.151.80.135 lalala.com GET /common_files/pics/error.gif HTTP/1.1
154-0 19526 0/1853/4196 W 14.12 826 0 0.0 4.77 10.97 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
155-0 21805 0/45/2257 _ 0.07 1 426 0.0 0.16 7.35 66.61.239.101 movies.lalala.com GET /list.php?movieorserie=3 HTTP/1.1
156-0 21806 0/42/621 _ 0.51 1 0 0.0 0.12 1.71 24.9.219.231 lalala.com GET /common_files/lalala.js HTTP/1.1
157-0 21807 0/47/614 _ 0.10 0 0 0.0 0.12 1.44 68.161.76.194 movies.lalala.com GET /movies.js HTTP/1.1
158-0 19530 0/1786/2239 W 13.26 823 0 0.0 4.43 5.94 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
159-0 21808 0/43/416 _ 0.93 0 279 0.0 0.10 1.43 70.56.27.29 movies.lalala.com POST / HTTP/1.1
160-0 - 0/0/2591 . 0.47 15 0 0.0 0.00 7.10 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
161-0 - 0/0/1324 . 0.44 42 0 0.0 0.00 3.93 67.83.185.204 lalala.com GET /common_files/lalala.css HTTP/1.1
162-0 - 0/0/533 . 0.01 68 0 0.0 0.00 1.37 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
163-0 19536 0/1305/2328 W 9.75 830 0 0.0 3.62 6.49 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
164-0 - 0/0/1088 . 4.45 48 371 0.0 0.00 3.10 71.63.11.155 movies.lalala.com GET /links_page.php?movie=1309 HTTP/1.1
165-0 - 0/0/911 . 0.35 70 5500 0.0 0.00 2.30 24.36.16.115 movies.lalala.com GET /list.php?movieorserie=0&page=2 HTTP/1.1
166-0 21270 0/32/1540 _ 0.40 1 245 0.0 0.08 3.97 24.144.10.24 movies.lalala.com GET /links_page.php?movie=1248 HTTP/1.1
167-0 - 0/0/539 . 3.34 66 0 0.0 0.00 1.92 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
168-0 - 0/0/431 . 0.52 3 0 0.0 0.00 1.12 127.0.1.1 lalala.com GET /common_files/ads/google_ad.php HTTP/1.0
169-0 19542 0/1694/2312 W 12.00 828 0 0.0 5.34 7.01 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
170-0 21273 0/315/1783 _ 3.19 0 0 0.0 0.98 4.61 24.9.219.231 lalala.com GET /common_files/pics/error2.gif HTTP/1.1
171-0 21814 0/46/3561 _ 1.30 0 410 0.0 0.32 10.44 68.195.78.117 movies.lalala.com GET /list.php?movieorserie=0&alpha=P HTTP/1.1
172-0 19545 0/2451/2779 _ 16.98 0 0 0.0 6.92 7.84 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
173-0 - 0/0/2052 . 0.06 9 0 0.0 0.00 5.13 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
174-0 21276 0/274/682 W 0.96 0 0 0.0 0.70 1.83 24.239.169.50 movies.lalala.com GET /list.php?movieorserie=0 HTTP/1.1
175-0 - 0/0/2463 . 0.40 5 26 0.0 0.00 6.79 24.44.180.24 movies.lalala.com GET / HTTP/1.1
176-0 - 0/0/6634 . 0.03 33 0 0.0 0.00 18.36 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
177-0 - 0/0/602 . 0.45 36 0 0.0 0.00 1.07 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
178-0 - 0/0/1022 . 1.17 182 0 0.0 0.00 2.94 127.0.1.1 lalala.com GET /common_files/ads/cpx_square.php HTTP/1.0
179-0 - 0/0/4290 . 0.02 353 0 0.0 0.00 11.68 71.130.27.70 lalala.com GET /common_files/pics/downarrow1.gif HTTP/1.1
180-0 - 0/0/2506 . 0.21 260 0 0.0 0.00 6.71 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
181-0 - 0/0/731 . 0.50 298 687 0.0 0.00 2.04 208.120.58.12 movies.lalala.com GET /shitnaz.php?mi=348&ln=6 HTTP/1.1
182-0 - 0/0/451 . 0.05 347 0 0.0 0.00 1.43 71.120.243.128 lalala.com GET /common_files/lalala.css HTTP/1.1
183-0 - 0/0/1139 . 2.75 0 0 0.0 0.00 3.06 72.80.13.99 lalala.com GET /common_files/pics/tape4rev.ico HTTP/1.1
184-0 - 0/0/307 . 0.88 301 0 0.0 0.00 0.85 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
185-0 - 0/0/996 . 0.44 2775 17721 0.0 0.00 2.69 86.156.168.14 movies.lalala.com GET /?movie=252 HTTP/1.1
186-0 - 0/0/1489 . 10.68 1834 0 0.0 0.00 3.82 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
187-0 - 0/0/4000 . 2.91 2584 0 0.0 0.00 11.46 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
188-0 - 0/0/440 . 0.42 2650 0 0.0 0.00 1.10 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
189-0 - 0/0/350 . 2.37 2414 126 0.0 0.00 1.08 72.39.189.97 movies.lalala.com GET /list.php?movieorserie=0&page=2 HTTP/1.1
190-0 - 0/0/461 . 2.83 2628 0 0.0 0.00 1.15 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
191-0 - 0/0/2537 . 0.70 2488 256 0.0 0.00 8.18 84.44.129.154 movies.lalala.com GET /list.php?movieorserie=0&page=2 HTTP/1.1
192-0 - 0/0/1307 . 5.47 2134 1626 0.0 0.00 3.98 81.106.37.241 movies.lalala.com GET /links_page.php?movie=1403 HTTP/1.1
193-0 - 0/0/154 . 1.81 2734 22898 0.0 0.00 0.48 206.248.162.156 movies.lalala.com GET /list.php?movieorserie=0&page=5 HTTP/1.1
194-0 - 0/0/303 . 1.88 2573 0 0.0 0.00 0.74 68.164.246.141 lalala.com GET /common_files/lalala.js HTTP/1.1
195-0 - 0/0/405 . 1.15 2577 0 0.0 0.00 0.87 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
196-0 - 0/0/159 . 0.08 2631 0 0.0 0.00 0.44 71.79.156.100 lalala.com GET /common_files/lalala.css HTTP/1.1
197-0 - 0/0/715 . 2.50 2566 329 0.0 0.00 1.85 89.243.48.75 movies.lalala.com GET /links_page.php?movie=1574 HTTP/1.1
198-0 - 0/0/996 . 7.98 2246 0 0.0 0.00 2.49 76.187.254.179 lalala.com GET /common_files/pics/play2.gif HTTP/1.1
199-0 - 0/0/333 . 2.84 2716 17237 0.0 0.00 0.92 64.228.211.146 movies.lalala.com GET / HTTP/1.1
200-0 - 0/0/293 . 3.42 2681 0 0.0 0.00 0.80 88.98.16.146 movies.lalala.com GET /movies.js HTTP/1.1
201-0 - 0/0/1112 . 7.90 2175 243 0.0 0.00 2.66 82.7.110.29 movies.lalala.com GET /flvplayer.swf?url=http%3A%2F%2Fliveu-38.vo.llnwd.net%2Fsvc
202-0 - 0/0/2629 . 2.90 2493 0 0.0 0.00 7.36 127.0.1.1 lalala.com GET /common_files/ads/cpx_square.php HTTP/1.0
203-0 - 0/0/883 . 4.00 2194 0 0.0 0.00 2.79 59.92.152.111 lalala.com GET /common_files/lalala.css HTTP/1.1
204-0 - 0/0/2120 . 0.02 2706 0 0.0 0.00 6.04 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
205-0 - 0/0/237 . 3.18 2704 0 0.0 0.00 0.59 63.229.79.87 lalala.com GET /common_files/pics/error.gif HTTP/1.1
206-0 - 0/0/618 . 0.03 2724 19658 0.0 0.00 1.61 80.192.83.145 movies.lalala.com GET /list.php?movieorserie=0 HTTP/1.1
207-0 - 0/0/352 . 1.50 2635 0 0.0 0.00 1.26 82.35.8.173 lalala.com GET /common_files/pics/tape4rev.ico HTTP/1.1
208-0 - 0/0/6315 . 6.53 1892 0 0.0 0.00 18.61 206.116.183.178 lalala.com GET /common_files/pics/play1.gif HTTP/1.1
209-0 - 0/0/751 . 1.13 2629 0 0.0 0.00 1.96 212.201.42.55 lalala.com GET /common_files/pics/play2.gif HTTP/1.1
210-0 - 0/0/1141 . 1.49 2630 0 0.0 0.00 3.25 68.122.226.110 lalala.com GET /common_files/pics/error2.gif HTTP/1.1
211-0 - 0/0/346 . 3.08 2608 0 0.0 0.00 0.91 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
212-0 - 0/0/361 . 0.42 2634 228 0.0 0.00 0.91 75.82.137.77 movies.lalala.com GET /list.php?movieorserie=0&page=7 HTTP/1.1
213-0 - 0/0/288 . 3.71 2712 0 0.0 0.00 0.83 142.162.49.119 lalala.com GET /common_files/pics/tape4rev.ico HTTP/1.1
214-0 - 0/0/791 . 2.60 1887 0 0.0 0.00 2.96 127.0.1.1 lalala.com GET /common_files/ads/cpx_leaderboard_ultimate.php HTTP/1.0
215-0 - 0/0/295 . 1.17 2773 0 0.0 0.00 0.77 127.0.1.1 lalala.com GET /common_files/ads/cpx_leaderboard_ultimate.php HTTP/1.0
216-0 - 0/0/522 . 0.44 2641 0 0.0 0.00 1.49 122.30.64.176 lalala.com GET /common_files/pics/play2.gif HTTP/1.1
217-0 - 0/0/451 . 0.45 2792 0 0.0 0.00 1.00 127.0.1.1 lalala.com GET /common_files/ads/cpx_leaderboard_ultimate.php HTTP/1.0
218-0 - 0/0/747 . 5.22 2491 770 0.0 0.00 1.81 129.169.70.46 movies.lalala.com GET /shitnaz.php?mi=1536&ln=1 HTTP/1.1
219-0 - 0/0/288 . 2.46 2657 0 0.0 0.00 1.04 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
220-0 - 0/0/3777 . 2.76 2587 0 0.0 0.00 10.14 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
221-0 - 0/0/559 . 2.47 2613 1519 0.0 0.00 1.26 71.97.40.181 movies.lalala.com GET /list.php?movieorserie=0&page=6 HTTP/1.1
222-0 - 0/0/1692 . 1.09 2789 5772 0.0 0.00 4.55 68.255.235.74 movies.lalala.com GET / HTTP/1.1
223-0 - 0/0/1211 . 0.78 2626 757 0.0 0.00 3.27 65.9.102.36 movies.lalala.com GET /links_page.php?movie=1333 HTTP/1.1
224-0 - 0/0/235 . 0.35 2795 0 0.0 0.00 0.61 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
225-0 - 0/0/1017 . 6.64 2176 0 0.0 0.00 3.67 127.0.1.1 lalala.com GET /common_files/ads/bidvertiser.php HTTP/1.0
226-0 - 0/0/3372 . 1.98 2644 0 0.0 0.00 9.55 74.110.210.13 lalala.com GET /common_files/pics/error2.gif HTTP/1.1
227-0 18070 0/2643/2819 W 20.11 840 0 0.0 8.11 8.65 69.86.233.91 movies.lalala.com GET /links_page.php?movie=771 HTTP/1.1
228-0 - 0/0/813 . 2.66 2456 0 0.0 0.00 2.79 146.203.130.11 lalala.com GET /common_files/pics/play1.gif HTTP/1.1
229-0 - 0/0/423 . 3.63 2605 0 0.0 0.00 1.27 24.174.242.136 lalala.com GET /common_files/lalala.js HTTP/1.1
230-0 - 0/0/408 . 0.83 2583 0 0.0 0.00 1.03 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
231-0 - 0/0/6438 . 2.56 2470 0 0.0 0.00 17.14 127.0.1.1 lalala.com GET /common_files/DOCTYPE.php HTTP/1.0
232-0 - 0/0/215 . 0.80 2589 0 0.0 0.00 0.68 68.85.111.115 movies.lalala.com GET /movies.js HTTP/1.1
233-0 - 0/0/5235 . 5.48 1894 0 0.0 0.00 14.74 141.214.17.5 movies.lalala.com GET /movies.js HTTP/1.1
234-0 - 0/0/4694 . 1.94 2698 0 0.0 0.00 12.63 127.0.1.1 lalala.com GET /common_files/DOCTYPE.php HTTP/1.0
235-0 - 0/0/924 . 1.43 2701 0 0.0 0.00 2.52 24.0.210.202 lalala.com GET /common_files/lalala.js HTTP/1.1
236-0 - 0/0/2506 . 7.08 2132 0 0.0 0.00 7.22 71.63.11.155 lalala.com GET /common_files/pics/tape4rev.ico HTTP/1.1
237-0 - 0/0/272 . 1.48 2604 845 0.0 0.00 0.66 24.91.211.42 movies.lalala.com GET /list.php?movieorserie=0&page=3 HTTP/1.1
238-0 - 0/0/201 . 0.06 2602 5 0.0 0.00 0.53 75.176.54.27 movies.lalala.com GET / HTTP/1.1
239-0 - 0/0/263 . 1.47 2633 694 0.0 0.00 0.56 138.162.140.56 movies.lalala.com GET /links_page.php?movie=1618 HTTP/1.0
240-0 - 0/0/887 . 1.98 2559 0 0.0 0.00 2.48 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
241-0 - 0/0/3618 . 7.32 2180 0 0.0 0.00 10.87 70.21.36.31 lalala.com GET /common_files/pics/error2.gif HTTP/1.1
242-0 - 0/0/226 . 1.77 2710 0 0.0 0.00 0.53 87.211.178.38 lalala.com GET /common_files/pics/play1.gif HTTP/1.1
243-0 - 0/0/210 . 1.38 2752 0 0.0 0.00 0.34 216.48.50.179 movies.lalala.com GET /movies.js HTTP/1.1
244-0 - 0/0/1746 . 2.14 2484 0 0.0 0.00 5.04 127.0.1.1 lalala.com GET /common_files/DOCTYPE.php HTTP/1.0
245-0 - 0/0/260 . 0.74 2794 0 0.0 0.00 0.64 74.140.216.122 lalala.com GET /common_files/pics/error.gif HTTP/1.1
246-0 - 0/0/995 . 6.32 2107 203 0.0 0.00 2.78 75.108.167.57 movies.lalala.com GET /list.php?movieorserie=0 HTTP/1.1
247-0 - 0/0/282 . 3.91 2594 666 0.0 0.00 0.87 71.134.240.75 movies.lalala.com GET /list.php?movieorserie=0&page=2 HTTP/1.1
248-0 - 0/0/231 . 1.52 2703 13557 0.0 0.00 0.60 72.51.113.22 movies.lalala.com GET / HTTP/1.1
249-0 - 0/0/684 . 8.06 2178 381 0.0 0.00 2.33 24.47.227.229 movies.lalala.com GET /list.php?movieorserie=0&page=2 HTTP/1.1
250-0 - 0/0/1205 . 2.89 2485 0 0.0 0.00 3.72 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
251-0 - 0/0/410 . 1.19 2656 0 0.0 0.00 0.88 204.210.217.240 backstage.lalala.com GET /protected_content/29415/userspics/42.gif HTTP/1.1
252-0 - 0/0/244 . 1.36 2720 0 0.0 0.00 0.76 127.0.1.1 lalala.com GET /common_files/ads/cpx_skyscraper_ultimate.php HTTP/1.0
253-0 - 0/0/2280 . 0.41 2654 0 0.0 0.00 5.88 59.92.152.111 lalala.com GET /common_files/lalala.js HTTP/1.1
254-0 - 0/0/358 . 0.72 2788 7633 0.0 0.00 1.54 76.178.170.105 movies.lalala.com GET / HTTP/1.1
255-0 - 0/0/172 . 1.06 2715 17092 0.0 0.00 0.73 192.44.136.113 movies.lalala.com GET /list.php?movieorserie=0 HTTP/1.1
Srv Child Server number - generation
PID OS process ID
Acc Number of accesses this connection / this child / this slot
M Mode of operation
CPU CPU usage, number of seconds
SS Seconds since beginning of most recent request
Req Milliseconds required to process most recent request
Conn Kilobytes transferred this connection
Child Megabytes transferred this child
Slot Total megabytes transferred this slot
Apache/2.0.55 (Ubuntu) PHP/5.1.6 Server at lalala.com Port 80


that ip 69.86.233.91 is there like 15 times, each instance is downloading the same page and theyre downloading it forever... though i visited that page and me it took me like 2 seconds to get it....

---

### Post by envis on 2007-05-23
i have monitored my server status for about 3 hours

the ip address 69.86.233.91 was always there on about 15 servers downloading continuously the same 2 pages from my site

i tested it and me it takes me 2 seconds to download that 1 page....

my conclusion: this ip address is hacking me! some kind of cheap DDOS attack

i denied this ip from my main domain and now i find that my server is much faster!!

does anyone know any better?

i have thousands of pages on there... this ip was there always about 15 times or so downloading always the same 2 pages for as long as i could see until i block it...

so to all the ppl who thoughed i was parano, i think i was not...

---

### Post by envis on 2007-05-24
or maybe its someone's server gathering too much info my pages

---

### Post by dfreer on 2007-05-30
wtf are you running on your site that you get a million hits a day?! 

in other words, "Old man teach me some voodoo magic!!1!"

---


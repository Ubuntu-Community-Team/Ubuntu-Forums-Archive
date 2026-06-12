---
title: "Apache 2 on Ubuntu : when accessed from external IP, bandwidth is very low"
date: 2017-08-22
forum: Server Platforms
---

### Post by damgaarderik on 2017-08-22
Hi All,

I´m very puzzled about this issue that I am having.

I have installed a Ubuntu 17.04 LTS on my server.
Next I have installed the http Apache 2 (version 2.4) server and enabled subversion on it.
No special configuration is done :
In apache2.conf, added the following :
```

<Directory /media/server/www/>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
</Directory>

``` 

added the following to /sites-available
svn.conf  to make subversion work.



Also I have installed a J2EE server (Glassfish 4.1.2) 

On my router I have made a port forwarding from 80 to the apache server and a port forwarding, on 8081, to the Glassfish4 server.

When I access the apache2/subversion from a local IP address (eg. 192.168.0.32) the bandwidth is high as well as on the glassfish4 server. Download/Upload is very fast (no waitingtime)

When I access the apache2/subversion from a external IP address then the download/upload is very slow < 10-20 Kb/s (actually if I request a document over 1 MB then the connection time out).
When I use the glassfish4 server the bandwidth is still high.....

I´m not a apache 2 expert so I have no clue about what is missing or need to be configured which could eventually cause this limitation on bandwidth ?

Anybody who can help me with some hints ?

I have tried to search for help but have not found any usefull help until now.

---

### Post by darkod on 2017-08-22
1. There is no 17.04 LTS. I guess you meant 16.04 LTS. If you really installed 17.04 that is not LTS version and will soon run out of support.

2. What is your internet upload connection speed? You have to consider that on local LAN you will usually have good speed, but requesting data from the internet means your server has to upload it towards the internet. So the upload speed of the connection is also important, not only download speed. It doesn't look like any limitation in apache because there is no one by default, and if it was, it would apply to LAN traffic too.

---

### Post by damgaarderik on 2017-08-23
Hi Darko,

Thanks for your answer. you are right (not LTS) it is Ubuntu Server 17.04 64bit. (maybe not the wises choice, but that is what I have done :))
My internet connection is 100 down/30 up Mbps.

As I have tried to describe : When I eg. access the glassfish4 server I experience no problem....only when I request data from the Apache 2 server?

Erik.

---

### Post by SeijiSensei on 2017-08-23
Try forwarding a different external port to Apache, say 8080.  Any better?

---

### Post by damgaarderik on 2017-08-24
Hi SeijiSensei,
Just tried to change port to 8080, but unfortunately I got the same result.
Get a 8MB document from Apache = "download time 2 min 48 sec"....and after 2 min the connection times out....
Get a 8MB document from GlassFish (port 8081) ==> download 15 sec.

Any other idea what this can be ?

---

### Post by damgaarderik on 2017-08-26
I found the solution.

I have separated the site-available in two separate sites.
One for www and another for subversion....for some reason this solves the issue ???
Now I can access the subversion site, from an external IP, and download with real speed (3 Mb instead of 20 kb).
Also the two site are splitte in two different domains ([www.mydomain.com](www.mydomain.com) and svn.mydomain.com)

I have no idea why this works....but it does.....

---


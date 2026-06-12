---
title: "tips on securing apache2?"
date: 2009-05-31
forum: Server Platforms
---

### Post by ant284 on 2009-05-31
Hi,
 
I have apache 2 installed and everything is working well, until my site is being use as a proxy... 
I have tried to modified the proxy.conf file but nothing seems to work. I'm just curious should i just change host with different ip 
or there is a way to block external site to use my server to access different site.
 
I checked the log files and I found the following 
 
125.89.79.182 - - [31/May/2009:13:06:08 +0000] "GET [5&mediaID=69937&tracking=&url]("http://scripts.affiliatefuture.com/AFClick.asp?affiliateID=178246&merchantID=3739&programmeID=9595&mediaID=69937&tracking=&url")= HTTP/1.0" 404 209 "[http://scripts.affiliatefuture.com/AFClick.asp?=69937&tracking=&url](http://scripts.affiliatefuture.com/AFClick.asp?=69937&tracking=&url)=" "Mozilla/4.0 (compatible; MSIE 4.5; Mac_PowerPC)"
 
119.123.133.180 - - [31/May/2009:13:06:12 +0000] "GET [http://www.baidu.com/s?wd=%D6%FA%BF%BC](http://www.baidu.com/s?wd=%D6%FA%BF%BC) HTTP/1.1" 404 174 "[http://www.baidu.com/](http://www.baidu.com/)" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)"
 
202.125.156.122 - - [31/May/2009:13:06:13 +0000] "GET [http://l05.member.in2.yahoo.com/config/isp_verify_user?l=n_nichole&p=teen](http://l05.member.in2.yahoo.com/config/isp_verify_user?l=n_nichole&p=teen) HTTP/1.0" 404 220 "-" "-"
 
62.109.3.160 - - [31/May/2009:13:06:13 +0000] "GET [http://sadmin.1124.ru/69057915](http://sadmin.1124.ru/69057915) HTTP/1.0" 404 206 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; MRA 4.2 (build 01102))"
 
221.215.205.82 - - [31/May/2009:13:06:14 +0000] "GET [http://ad.spot200.com/st?ad_type=iframe&ad_size=728x90&section=452049](http://ad.spot200.com/st?ad_type=iframe&ad_size=728x90&section=452049) HTTP/1.0" 404 200 "[http://www.jobcentral.com](http://www.jobcentral.com)" "Mozilla/4.0 (compatible; MSIE 5.0; Windows 98; Alexa Toolbar)"
 
127.0.0.1 - - [31/May/2009:13:06:17 +0000] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (internal dummy connection)"
127.0.0.1 - - [31/May/2009:13:06:17 +0000] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (internal dummy connection)"
 
 
 
any help is appreciated

---

### Post by alastair on 2009-05-31
You are probably not a proxy, but it is good to check. All the above requests seem to return a 404 error code - so it looks OK. People are trying, and failing. You will have to put up with people trying to do bad things to internet facing systems ...

If you don't want/need to proxy, don't even load the proxy module (mod_proxy) i.e. remove any links to the proixy module in :

/etc/apache2/mods-enabled/

and restart apache.

Even if people try and get a "200" (OK) code, your server is probably only serving your HOME page!

Resource :

[http://www.karkomaonline.com/index.php/2004/04/apache-as-an-open-proxy/](http://www.karkomaonline.com/index.php/2004/04/apache-as-an-open-proxy/)

---

### Post by ant284 on 2009-05-31
Hi,
 
thank you for your information very helpfull, but the problem are those request makes my virtual host consume memory!! 
and then I have ask the hosting company to restart my virtual server 
 
but thnx again

---

### Post by Vegan on 2009-05-31
You should not need to be overly concerned with idiots gnawing away at you server, I see this garbage all day and just ignore it.

There is nothing a miscreant can do to my server, nothing.

No proxy is needed, all you need is the ability to ignore the problem.

I see crap daily from all manor of places including university mistakes attempting to find a share that does not exist.

---


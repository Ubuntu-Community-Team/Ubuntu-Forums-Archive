---
title: "Web server problem - unrelated connection"
date: 2007-11-29
forum: Server Platforms
---

### Post by sanctus on 2007-11-29
Hi, 

I'm getting a load of connections on my http/80 port.

The problem is that apache log it in the access file, and sometime it really load my bandwidth. 

I had a ubuntu server 7.04 (updated from 6.10) running apache 2.2.3 when I started to see these log. I did some reasearch and I found that there is a problem wih apache 2.2.2, 2.2.3 and 2.2.4 with mod_status and mod_proxy that enable other to hijack the server as an anonymous proxy. [http://www.securityfocus.com/bid/24645/info](http://www.securityfocus.com/bid/24645/info)

First I tried to disable the proxy, rewrite and status module. The problem was still there.

Then I upgrade to 7.10 and apache 2.2.4.

Samething ...

I though the problem could still be with apache, so I installed lighttpd. Same problem, except the log are in the lighttpd/access.log

The log show 400 (error) and a 300 (redirection) .

Here is a snapshot of log: (I have 800mo of log file ;-) )
```

apache :

|||222.89.236.71 - - [19/Nov/2007:21:09:42 -0500] "GET http://media.fastclick.net/w/safepop.cgi?cid=88828&mid=173391&sid=26024&c=32 HTTP/1.0" 302 - "http://www.chaoticarcade.com/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; .NET CLR 1.0.3705)"
|||72.232.29.114 - - [19/Nov/2007:21:09:41 -0500] "GET http://www.mellis-reiter-shop.de/guestbox.php HTTP/1.0" 302 3844 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
|||745||||123.8.230.33 - - [19/Nov/2007:21:09:42 -0500] "GET http://media.fastclick.net/w/get.media?sid=27849&m=1&tp=5&d=j&t=s&upsid=736367626387 HTTP/1.0" 200 745 "http://www.recruit.net/" "Mozilla/4.0 (compatible; MSIE 5.5; Windows NT 4.0)"
|||125.77.78.108 - - [19/Nov/2007:21:09:42 -0500] "GET http://banner.adtrgt.com/cpi.jsp?pvr=84&p=111665&aid=21707&partnerMin=0&ron=on&ronMin=0&cpviw=728&cpvih=90&url=http%3A//www.mauland.us/&context=home%20page HTTP/1.0" 302 - "http://www.mauland.us/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; Q312461)"
|||121.32.28.197 - - [19/Nov/2007:21:08:42 -0500] "GET http://www.a-mail.cn/webmail1.php HTTP/1.1" 404 111 "\xcf\xf2http://www.sfmir2.com\xbf\xaa\xbb\xf0" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 5.1)"
|||222.141.201.109 - - [19/Nov/2007:21:09:42 -0500] "GET http://pagead2.googlesyndication.com/pagead/show_ads.js HTTP/1.0" 200 12338 "http://www.teenbanking.info" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
|||61.139.106.232 - - [19/Nov/2007:21:09:42 -0500] "GET http://clickingagent.com/proxycheck.php?ip=69.70.73.102&port=80&loc= HTTP/1.0" 200 13 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"


lighttpd: 

124.234.65.116 code.qihoo.com - [29/Nov/2007:22:42:44 -0500] "GET http://code.qihoo.com/ad_bcast/html_show.js?a=2465&b=1003&p=2026&nt=&w=405&h=90&m=173020&refid=&css= HTTP/1.0" 404 345 "http://www.5i5art.com/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)"
90.15.7.51 - - [29/Nov/2007:22:42:44 -0500] "GET http://edit.vip.tpe.yahoo.com/config/pwtoken_get?login=hornydub&src=ygodgw&passwd=f6e1a5514b270c001c5aa6d7b6108232&challenge=rqgNyP.VFsyzHpUmdwDakGOydzqs&md5=1 HTTP/1.1" 400 349 "-" "MobileRunner-J2ME"
189.145.13.42 - - [29/Nov/2007:22:42:44 -0500] "GET http://m5.member.dcn.yahoo.com/config/login?.redir_from=PROFILES?&.tries=1&.src=jpg&.last=&promo=&.intl=us&.bypass=&.partner=&.chkP=Y&.done=http://jpager.yahoo.com/jpager/pager2.shtml&login=rashunj24&passwd=asshole HTTP/1.0" 404 345 "-" "-"
221.206.196.129 jsearch.vicp.net:39127 - [29/Nov/2007:22:42:47 -0500] "GET http://jsearch.vicp.net:39127/ps/prx.php?p=q1w2e3r4t5y6u7i8o9p0*a-b?hash=494922DA6CE4E29D454649660050BE7EC8AC066F128E HTTP/1.0" 404 345 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0)"
89.188.110.183 proxy.promo.lviv.ua - [29/Nov/2007:22:42:47 -0500] "POST http://proxy.promo.lviv.ua/check.php HTTP/1.1" 404 345 "http://e9ed9cad56/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)"
89.188.110.183 proxy.promo.lviv.ua - [29/Nov/2007:22:42:47 -0500] "POST http://proxy.promo.lviv.ua/check.php HTTP/1.1" 404 345 "http://024677efb8/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)"
219.150.243.107 www.0ads0.com - [29/Nov/2007:22:42:47 -0500] "GET http://www.0ads0.com/banner/661/47157%26dp=0 HTTP/1.0" 404 345 "http://www.321webspace.com" "Mozilla/4.0 (compatible; MSIE 5.02; Windows 95)"
85.176.151.148 www.autoscout24.de - [29/Nov/2007:22:42:49 -0500] "GET http://www.autoscout24.de/List.aspx?vis=1&state=A&make=74&fregfrom=01%2f01%2f1994+00%3a00%3a00&pricefrom=5494&priceto=5500&kmto300000&cy=deutschland&page=3&maxresults=500&results=80&ustate=N&ustate=U&um=True&sort=price&rfde=True&pool=9&zipc=D HTTP/1.1" 404 345 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; de-DE; rv:1.7.8) Gecko/20050511 Firefox/1.0.4"
125.45.82.51 banners.affiliatefuture.com - [29/Nov/2007:22:42:50 -0500] "GET http://banners.affiliatefuture.com/889/19179.gif HTTP/1.0" 404 345 "http://www.helengrace.co.uk/" "Mozilla/4.5 [en] (Win98; I)"
90.15.7.51 - - [29/Nov/2007:22:42:52 -0500] "GET http://n5.login.re3.yahoo.com/config/pwtoken_get?login=hornycat&src=ygodgw&passwd=f6e1a5514b270c001c5aa6d7b6108232&challenge=rqgNyP.VFsyzHpUmdwDakGOydzqs&md5=1 HTTP/1.1" 400 349 "-" "MobileRunner-J2ME"
194.186.94.110 - - [29/Nov/2007:22:42:54 -0500] "CONNECT 205.188.179.233:443 HTTP/1.0" 501 357 "-" "-"
84.16.252.79 89.149.241.191 - [29/Nov/2007:22:42:55 -0500] "POST http://89.149.241.191/d3sUpER3fg.php HTTP/1.1" 404 345 "-" "-"
194.67.32.2 - - [29/Nov/2007:22:42:57 -0500] "CONNECT 205.188.153.100:443 HTTP/1.0" 501 357 "-" "-"
121.35.240.108 www.allcombo.com - [29/Nov/2007:22:42:59 -0500] "GET http://www.allcombo.com/main/index.php?uid=24528 HTTP/1.1" 404 345 "-" "Mozilla/4.0 (compatible; MSIE 4.01; Windows 98)"
```

netstat -nat show me something like this :
```
tcp        0      0 69.70.73.102:80         208.74.174.162:57802    TIME_WAIT  
tcp        0      0 69.70.73.102:80         80.93.48.207:46348      TIME_WAIT  
tcp        0      0 69.70.73.102:80         90.15.7.51:1616         TIME_WAIT  
tcp        0      0 69.70.73.102:80         90.15.7.51:1086         TIME_WAIT  
tcp        0    503 69.70.73.102:80         124.234.65.116:2762     ESTABLISHED
tcp        0      0 69.70.73.102:80         80.92.110.19:48609      TIME_WAIT  
tcp        0      0 69.70.73.102:80         80.92.110.19:48322      TIME_WAIT  
tcp        0      0 69.70.73.102:80         219.150.243.107:4373    TIME_WAIT  
tcp        0      0 69.70.73.102:80         77.232.8.36:59619       TIME_WAIT  
tcp        0      0 69.70.73.102:80         84.16.252.79:43950      TIME_WAIT  
tcp        0      0 69.70.73.102:80         77.232.8.36:59573       TIME_WAIT  
tcp        0      0 69.70.73.102:80         90.15.7.51:1402         TIME_WAIT  
tcp        0      0 69.70.73.102:80         82.83.139.102:16638     TIME_WAIT 

```


How can I stop these connections?

---

### Post by rokclimb15 on 2007-11-30
Looks like a bunch of those IP addresses belong to APNIC or RIPE.  I'm thinking that your box either is or was exploited for some time to host ads.  These look like scanners trying to see if your machine is hosting this content.

You should do a thorough audit of your box for starters.  Check SSH logs and bash history.  Do you have tripwire installed?

You should do a reverse DNS lookup on your IP just to make sure none of those domains are actually pointing to your machine.  Assuming they are not, it is a malicious hosts file or DNS server pointing traffic to your box.

Depending on the nature of your site, you may want to consider a separate IDS/Firewall in front of your server.  I recommend using OpenBSD and Snort/PF for such a purpose.  If you don't run a site that's a high profile target, this is likely just the aftermath of your machine being exploited or someone trying to DoS your server.  Make sure you move those log files off your / partition!!!!

---

### Post by sanctus on 2007-11-30
It looks like my box was used as an anonymous proxy server.

 There's is a couple of site containing anonymous proxy list that show up my ip.

I test it and it doen't look to work anymore. Though, using my ip as an anonymous proxy, every request is reroute to my homepage .... weird .. 

One thing is certain, I will be flooded with request for some time.

---

### Post by MJN on 2007-11-30
> **sanctus said:**
> Hi, 
 
I'm getting a load of connections on my http/80 port.
 
The problem is that apache log it in the access file, and sometime it really load my bandwidth. 
 
I had a ubuntu server 7.04 (updated from 6.10) running apache 2.2.3 when I started to see these log. I did some reasearch and I found that there is a problem wih apache 2.2.2, 2.2.3 and 2.2.4 with mod_status and mod_proxy that enable other to hijack the server as an anonymous proxy. [http://www.securityfocus.com/bid/24645/info](http://www.securityfocus.com/bid/24645/info)
 
No, that vulnerability is related to mod_status only and has nothing to do with open proxying.
 
> First I tried to disable the proxy, rewrite and status module. The problem was still there.
 
Why do you have proxying enabled anyway? Do you need it?
 
There is nothing insecure about Apache proxying itself, the risk is only present if you configure it wrong (there are plenty of guides explaining how to do it right).
 
> How can I stop these connections?
 
Post your config and we can fix whatever hole(s) you might have. After this, unless these connections are causing you a denial of service then just ignore them and they will eventually trail off.
 
Mathew

---

### Post by sanctus on 2007-11-30
I used it to enable some turbogears(python) application.
I followed the instruction in the mailling list and docs at the time.
I'm using fastcgi now.

```

#	<Location />
#      		ProxyPass http://127.0.0.1:8080/
#		ProxyPassReverse  http://127.0.0.1:8080/
#    	</Location>

```

What was worring me, is even with proxy disable and with another web server, I was still getting all these log into the access.log. And netstat shows established connections.

But I look like as long as my ip show up on some wed site listing anonymous proxy , I will see a bunch of connections.

I remove all the proxy param from my config and change de proxy.conf (even if I remove it from mods-enable) to :
```
        ProxyRequests Off

        <Proxy *>
                Order allow,deny
                Deny from all
                #Allow from .example.com
        </Proxy>

        # Enable/disable the handling of HTTP/1.1 "Via:" headers.
        # ("Full" adds the server version; "Block" removes all outgoing Via: headers)
        # Set to one of: Off | On | Full | Block

        ProxyVia Off

```

I test it and the proxy doesn't work, it redirict to my homepage.

Thank you

---

### Post by MJN on 2007-11-30
Even with the proxy module removed, or merely 'de-configured' you'll still get the connections - you can't stop clients connecting as until they've submitted their request you don't know if they are friend or foe.
 
However, if you're not acting as a proxy you've not got anything to be worry about. Your IP will soon drop of the open-proxy lists (otherwise the lists would be next to useless if they didn't delete non-open proxies).
 
Mathew

---


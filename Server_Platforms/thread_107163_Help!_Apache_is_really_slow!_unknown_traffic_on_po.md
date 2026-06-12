---
title: "Help! Apache is really slow! unknown traffic on port 80"
date: 2005-12-22
forum: Server Platforms
---

### Post by vinjvinj on 2005-12-22
I have a web server which is running behind a netgear firewall which has port 80 open only. When I restart the web server it works fine for a few minutes before it becomes very slow. 

I have my netgear firewall forwarding all requests on port 80 to my ubuntu apache server on port 80. When the server becomes slow the load on the server is very low and the memory usage is fine. 

When I stop netgear from forwarding requests to my ubuntu box things work fine. 

I then did a tcpdump on port 80 I was shocked to see a bunch of traffic even though I was not opening the web site. I'm stumped now and don't know what to do next. Would upgrading to lighttpd help?

How do I figure what this other trafic on my ip is? and how do i stop that traffic. 

Thanks for your help

---

### Post by gruepig on 2005-12-23
That sounds strange.  A few things to try ....

Take a look at your apache logs (likely /var/log/apache2/*.log or /var/log/apache/*.log).

Use 'lsof -i' and/or 'netstat --inet' to see what network connections are open.

Also, what tcpdump filter did you use?  Try 'sudo tcpdump -nv dst <your IP> and port 80'.  And 'sudo tcpdump -nv src <your IP> and port 80' (just in case your computer is initiating outbound port 80 connections that it shouldn't be).

---

### Post by vinjvinj on 2005-12-23
Thanks for your valuable comments. I installed chkrootkit on my webserver and it said that I might have the:

Checking `scalper'... Warning: Possible Scalper Worm installed
Checking `slapper'... Warning: Possible Slapper Worm installed

I then went to a clean machine and installed apache and my applciation there. I ran chkrootkit on this machine and it did not show anything. After about an hour, I ran chkrootkit again and it was showing the same thing as my earlier machine

Checking `scalper'... Warning: Possible Scalper Worm installed
Checking `slapper'... Warning: Possible Slapper Worm installed

when I type tcpdump -nv src 192.168.0.10 and  port 80 I get a lot of data, does this mean my machine is infected?

I did an apt-get update and installed apache2 2.0.54. I'm also including a small part of the apache2 log and error file. It's showing a lot of activity when  I was doing nothing on my server and not accessing any pages. 

61.153.158.197 - - [23/Dec/2005:04:34:38 -0500] "GET [http://partners.mygeek.com/search.jsp?partnerid=98939&query=new+balance+shoes&ip=68.38.196.46](http://partners.mygeek.com/search.jsp?partnerid=98939&query=new+balance+shoes&ip=68.38.196.46) HTTP/1.0" 200 1083 "-" "lwp-trivial/1.41"
218.56.175.30 - - [23/Dec/2005:04:34:36 -0500] "GET [http://www.gms1.net/midas/?src=pub&site=146&adfmt=2&ccb=7736278152.718984](http://www.gms1.net/midas/?src=pub&site=146&adfmt=2&ccb=7736278152.718984) HTTP/1.1" 200 701 "http://www.teamboom.com/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
66.111.35.130 - - [23/Dec/2005:04:31:30 -0500] "GET [http://www.ericjamesstone.com:80/Events.php](http://www.ericjamesstone.com:80/Events.php) HTTP/1.0" 502 320 "http://www.incest-sex.1stok.com/" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.5) Gecko/20031007 Firebird/0.7"
58.51.170.27 - - [23/Dec/2005:04:34:43 -0500] "GET [http://t.trafficmp.com/j.t/i17644/762070308/?http://www.theusainfo.com/](http://t.trafficmp.com/j.t/i17644/762070308/?http://www.theusainfo.com/) HTTP/1.0" 200 230 "-" "Mozilla/4.0 (compatible; MSIE 5.5; Windows NT 5.0)"
66.111.35.130 - - [23/Dec/2005:04:34:31 -0500] "GET [http://imux.net:80/](http://imux.net:80/) HTTP/1.0" 200 17518 "http://www.incest-movie.fluo.net/" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.5) Gecko/20031007 Firebird/0.7"
218.75.96.254 - - [23/Dec/2005:04:34:27 -0500] "GET [http://partners.mygeek.com/search.jsp?partnerid=99028&query=oreck+air+purifier&ip=68.38.196.46](http://partners.mygeek.com/search.jsp?partnerid=99028&query=oreck+air+purifier&ip=68.38.196.46) HTTP/1.1" 200 208 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)"
66.111.35.130 - - [23/Dec/2005:04:34:42 -0500] "GET [http://weblog.tumkurinfo.com:80/](http://weblog.tumkurinfo.com:80/) HTTP/1.0" 200 14053 "http://www.incest-movie.fluo.net/" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.5) Gecko/20031007 Firebird/0.7"
61.233.154.72 - - [23/Dec/2005:04:34:37 -0500] "GET http://www.categoryclicks.com/exit.php?ccid=2640&cccat=1&nval='+thisclick+'&dom='+dom+'&ccad=0&refurl=http://www.athleticssport.net/ HTTP/1.0" 302 - "http://www.athleticssport.net/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
221.217.160.11 - - [23/Dec/2005:04:34:37 -0500] "GET [http://network.realmedia.com/RealMedia/ads/adstream_sx.ads/news2it/728x90/ron/tchnws/ss/a@Top1](http://network.realmedia.com/RealMedia/ads/adstream_sx.ads/news2it/728x90/ron/tchnws/ss/a@Top1) HTTP/1.1" 200 110 "http://www.news2it.com/default.htm" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
61.233.154.72 - - [23/Dec/2005:04:34:54 -0500] "GET http://www.categoryclicks.com/exit2.php?ccid=2640&cccat=1&ccad=0&refurl=http://www.athleticssport.net/&dom=\\'%20dom%20\\' HTTP/1.0" 200 570 "http://www.athleticssport.net/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
61.233.154.75 - - [23/Dec/2005:04:34:37 -0500] "GET [http://www.categoryclicks.com/exit.php?ccid=2640&cccat=6&nval=2300553893&dom=www.athleticssport.net&ccad=0&refurl=http://www.athleticssport.net/](http://www.categoryclicks.com/exit.php?ccid=2640&cccat=6&nval=2300553893&dom=www.athleticssport.net&ccad=0&refurl=http://www.athleticssport.net/) HTTP/1.0" 302 - "http://www.athleticssport.net/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
218.56.175.30 - - [23/Dec/2005:04:34:43 -0500] "GET [http://geo.gms1.net/ad/?typ=1&pub=1&site=146&adfmt=2&aid=0&sid=0&cat=0&sub=0&pop=&tloc=False&click=&ipr=&ref=819393893524249696962393787486758888862376888624&ccb=54883645](http://geo.gms1.net/ad/?typ=1&pub=1&site=146&adfmt=2&aid=0&sid=0&cat=0&sub=0&pop=&tloc=False&click=&ipr=&ref=819393893524249696962393787486758888862376888624&ccb=54883645) HTTP/1.1" 502 853 "http://www.teamboom.com/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
221.217.163.25 - - [23/Dec/2005:04:34:54 -0500] "GET [http://ad.trafficmp.com/tmpad/banner/ad/tmp.asp?poID=eMX8](http://ad.trafficmp.com/tmpad/banner/ad/tmp.asp?poID=eMX8) HTTP/1.0" 200 438 "http://www.alexgame.com/" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
66.111.35.130 - - [23/Dec/2005:04:35:00 -0500] "GET [http://www.metech.nl:80/](http://www.metech.nl:80/) HTTP/1.0" 200 10849 "http://www.incest-pictures.fluo.net/" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.5) Gecko/20031007 Firebird/0.7"
r


Apache error:


[Fri Dec 23 04:36:23 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/mod_proxy.c(418): Trying to run scheme_handler
[Fri Dec 23 04:36:23 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(1075): proxy: HTTP: serving URL [http://minutemanhq.com/b2/index.php/national](http://minutemanhq.com/b2/index.php/national)
[Fri Dec 23 04:36:23 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(186): proxy: HTTP connecting [http://minutemanhq.com/b2/index.php/national](http://minutemanhq.com/b2/index.php/national) to minutemanhq.com:80
[Fri Dec 23 04:36:23 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(67): proxy: HTTP: canonicalising URL //www.the-teen.com
[Fri Dec 23 04:36:23 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/mod_proxy.c(418): Trying to run scheme_handler
[Fri Dec 23 04:36:23 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(1075): proxy: HTTP: serving URL [http://www.the-teen.com/](http://www.the-teen.com/)
[Fri Dec 23 04:36:23 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(186): proxy: HTTP connecting [http://www.the-teen.com/](http://www.the-teen.com/) to [www.the-teen.com:80](www.the-teen.com:80)
[Fri Dec 23 04:36:25 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_util.c(1139): proxy: HTTP: fam 2 socket created to connect to [www.the-teen.com](www.the-teen.com)
[Fri Dec 23 04:36:25 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(336): proxy: socket is connected
[Fri Dec 23 04:36:25 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(370): proxy: connection complete to 64.255.162.106:80 ([www.the-teen.com](www.the-teen.com))
[Fri Dec 23 04:36:25 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(909): proxy: start body send
[Fri Dec 23 04:36:26 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_util.c(1139): proxy: HTTP: fam 2 socket created to connect to ad.trafficmp.com
[Fri Dec 23 04:36:26 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(336): proxy: socket is connected
[Fri Dec 23 04:36:26 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(370): proxy: connection complete to 65.216.123.144:80 (ad.trafficmp.com)
[Fri Dec 23 04:36:26 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(909): proxy: start body send
[Fri Dec 23 04:36:26 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(969): proxy: end body send
[Fri Dec 23 04:36:26 2005] [info] (104)Connection reset by peer: core_output_filter: writing data to the network
[Fri Dec 23 04:36:26 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(969): proxy: end body send
[Fri Dec 23 04:36:26 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(67): proxy: HTTP: canonicalising URL //www.the-teen.com/out.php
[Fri Dec 23 04:36:26 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/mod_proxy.c(418): Trying to run scheme_handler
[Fri Dec 23 04:36:26 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(1075): proxy: HTTP: serving URL [http://www.the-teen.com/out.php](http://www.the-teen.com/out.php)
[Fri Dec 23 04:36:26 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(186): proxy: HTTP connecting [http://www.the-teen.com/out.php](http://www.the-teen.com/out.php) to [www.the-teen.com:80](www.the-teen.com:80)
[Fri Dec 23 04:36:27 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_util.c(1139): proxy: HTTP: fam 2 socket created to connect to [www.the-teen.com](www.the-teen.com)
[Fri Dec 23 04:36:28 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(336): proxy: socket is connected
[Fri Dec 23 04:36:28 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(370): proxy: connection complete to 64.255.162.106:80 ([www.the-teen.com](www.the-teen.com))
[Fri Dec 23 04:36:28 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(909): proxy: start body send
[Fri Dec 23 04:36:28 2005] [debug] /build/buildd/apache2-2.0.54/build-tree/apache2/modules/proxy/proxy_http.c(969): proxy: end body send
r

---

### Post by Gandalf on 2005-12-23
What are you running on the server? i mean is your site running Mambo for example?

---

### Post by gruepig on 2005-12-23
It's hard to know for sure without knowing what you are trying to run, but it looks like you are being used as a proxy, so yes, you have quite likely been cracked.

Run 'ps auwwx' and look for anything weird.

Run 'lsof -i' to see open connections.  Also run 'lsof -i | grep LISTEN' to see if you have any unusual ports open.

Also, frequently (but not always) installed scripts/binaries end up in /tmp.  Take a look at 'ls -lat /tmp'.

If you're not sure what weird or unusual is, post the output here or send me a private message.

If your system is cracked, disconnect your system from the network entirely.  If you're really curious, you may want to poke around the logs and try to figure out what happened.  If the only port you had open was port 80, it's likely that got attacked through an apache exploit (if you're running php, there have been a number of vulnerabilities).  You should really wipe your machine and reinstall and consider all of your passwords compromised, etc.

---


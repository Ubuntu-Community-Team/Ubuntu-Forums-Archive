---
title: "[SOLVED] Is my server an open proxy?"
date: 2008-11-05
forum: Server Platforms
---

### Post by chris.zeman on 2008-11-05
I noticed some unusual network activity yesterday afternoon, and then some even stranger network activity this morning.

My network is behind an [Untangle]("http://untangle.com") box, and I have a server running Ubuntu 8.04.1. The Spyware Blocker event log in Untangle showed blocked connections in which the client IP address was on the internet, and the server IP address was that of my Ubuntu server. Here is a screenshot from this morning:

[IMG]http://n9xcr.com/Screenshots/Untangle/Spyware%20Blocker.png[/IMG]

I wasn't sure what to make of it, but I suspected that perhaps my server was somehow being used as a proxy. I looked again a short time later and saw that the roles and switched. My server was now the client, and it appears that my fairly simple LAMP server is attempting to open web sites.

[IMG]http://n9xcr.com/Screenshots/Untangle/Spyware%20Blocker%202.png[/IMG]

I do not have a GUI installed on the server. It's just a LAMP server with Webmin at the moment. The only ports being forwarded through Untangle to my server are ports 80 and 443. The activity stopped about a minute after I stopped Apache. 

I have one Reverse Proxy setup to enable HTTP access to another internal web server. Both the Ubuntu and other server need to be available on port 80. I created a sub-domain for the other server and created the configuration file shown below, following an example I found online.

```
ServerName http://sub.domain.net
ProxyPass / http://172.16.1.20/ 
ProxyPassReverse / http://172.16.1.20/ 
<Location /> 
ProxyPassReverse / 
    SetOutputFilter     proxy-html 
    RequestHeader      unset    Accept-Encoding 
</Location> 
ProxyRequests Off 
<Proxy *> 
Order deny,allow 
Allow from all 
</Proxy>
```

Thank you,
Chris

---

### Post by MJN on 2008-11-05
The configuration looks fine (secure).
 
Rather than rely on Spyware Blocker's interpretation check your Apache logs. Specifically, look at the requests (and responses) for the events in the second window and see who/why/how these requests were being made.
 
Mathew

---

### Post by chris.zeman on 2008-11-05
Hi MJN,

Thank you for the reply! :) I checked the logs as you suggested. My access.log is over 41MB. This particular server has only been up for a few days, and isn't really a publically accessed server.

```
204.13.98.133 - - [05/Nov/2008:10:18:55 -0600] "GET http://www.ticketmaster.com/event/1D004107BADF3A5A HTTP/1.1" 200 15986 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; .NET CLR 2.0.50727; InfoPath.1; .NET CLR 3.0.04506.30)"
221.224.78.233 - - [05/Nov/2008:10:31:19 -0600] "GET http://221.231.148.193/index.html?uip=221.224.78.233&dip=<My Public IP>&url=http://d3.zedo.comhttp://d3.zedo.com/jsc/d3/ff2.html?n=790;c=459/1;s=416;d=9;w=300;h=250 HTTP/1.0" 404 516 "http://www.sportsgoal.com/advertising.php/index.php" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98; DigExt)"
221.224.78.233 - - [05/Nov/2008:10:31:20 -0600] "GET http://221.231.148.193/index.html?uip=221.224.78.233&dip=<My Public IP>&url=http://h.zedo.comhttp://h.zedo.com/init/0.17765309081272484/g.gif HTTP/1.0" 404 493 "http://d3.zedo.com/jsc/d3/ff2.html?n=790;c=459/1;s=416;d=9;w=300;h=250" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR1.1.4322)"
221.224.78.233 - - [05/Nov/2008:10:31:22 -0600] "GET http://221.231.148.193/index.html?uip=221.224.78.233&dip=<My Public IP>&url=http://221.231.148.193http://221.231.148.193/index.html?uip=221.224.78.233&dip=<My Public IP>&url=http://simg.zedo.comhttp://simg.zedo.com/speed-test/10k.gif?1711 HTTP/1.0" 404 596 "http://d3.zedo.com/jsc/d3/ff2.html?n=790;c=459/1;s=416;d=9;w=300;h=250" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; Alexa Toolbar)"
221.224.78.253 - - [05/Nov/2008:10:31:22 -0600] "GET http://221.231.148.193/index.html?uip=221.224.78.253&dip=<My Public IP>&url=http://tags.expo9.exponential.comhttp://tags.expo9.exponential.com/tags/TheAutoBucketsWebMagazine/ROS/tags.js HTTP/1.0" 404 537 "http://www.autobuckets.com/boards/viewtopic.php/p=11160.php" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; Alexa Toolbar; SV1; .NET CLR 2.0.50727; .NET CLR 3.0.04506.30)"
221.224.78.253 - - [05/Nov/2008:10:31:44 -0600] "GET http://221.231.148.193/index.html?uip=221.224.78.253&dip=<My Public IP>&url=http://a.tribalfusion.comhttp://a.tribalfusion.com/jr.ad?site=theautobucketswebmagazine&adSpace=ros&tagKey=2034039707&size=160x600|120x600&p=17374529&a=1&flashVer=0&ver=1.14&center=1&url=http%3A%2F%2Fwww.autobuckets.com%2Fboards%2Fviewtopic.php%2Fp%3D14715.php&rnd=17376021 HTTP/1.0" 404 741 "http://www.autobuckets.com/boards/viewtopic.php/p=14715.php" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
221.224.78.254 - - [05/Nov/2008:10:31:53 -0600] "GET http://221.231.148.193/index.html?uip=221.224.78.254&dip=<My Public IP>&url=http://a.tribalfusion.comhttp://a.tribalfusion.com/j.ad?site=theautobucketswebmagazine&adSpace=ros&tagKey=1597481696&size=728x90&p=17024148&a=1&flashVer=9&ver=1.14&center=1&url=http%3A%2F%2Fwww.autobuckets.com%2Fboards%2Fprivmsg.php%2Fmode%3Dpost%26u%3D11532.php&rnd=17030848 HTTP/1.0" 404 743 "http://www.autobuckets.com/boards/privmsg.php/mode=post&u=11532.php" "Mozilla/4.0 (compatible; MSIE 5.0; AOL 6.0; Windows 98; DigExt)"
221.224.78.245 - - [05/Nov/2008:10:31:53 -0600] "GET http://221.231.148.193/index.html?uip=221.224.78.245&dip=<My Public IP>&url=http://d3.zedo.comhttp://d3.zedo.com/jsc/d3/ff2.js HTTP/1.0" 404 478 "http://www.sportsgoal.com/advertising.php/index.php" "Opera/8.50 (Windows NT 5.1; U; en)"
221.224.78.254 - - [05/Nov/2008:10:31:54 -0600] "GET http://221.231.148.193/index.html?uip=221.224.78.254&dip=<My Public IP>&url=http://ll.atdmt.comhttp://ll.atdmt.com/b/NMMRTUMAAUMA/STND_Search_feature_GreenLiving_general_728x90.jpg HTTP/1.0" 404 532 "http://www.autobuckets.com/boards/privmsg.php/mode=post&u=11428.php" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.1) Gecko/20061204 Firefox/2.0.0.1"
221.224.78.233 - - [05/Nov/2008:10:32:09 -0600] "GET http://221.231.148.193/index.html?uip=221.224.78.233&dip=<My Public IP>&url=http://d3.zedo.comhttp://d3.zedo.com/jsc/d3/ff2.html?n=790;c=459/1;s=416;d=9;w=300;h=250 HTTP/1.0" 404 516 "http://www.sportsgoal.com/advertising.php/index.php" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)"
```

Here is my error.log for the same time period as shown in access.log:
```
[Wed Nov 05 10:31:09 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 76.13.218.11:80 (*) failed
[Wed Nov 05 10:31:09 2008] [error] [client 204.13.98.140] (70007)The timeout specified has expired: proxy: error reading response
[Wed Nov 05 10:31:19 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 92.43.106.10:80 (*) failed
[Wed Nov 05 10:31:19 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 92.43.106.10:80 (*) failed
[Wed Nov 05 10:31:20 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 92.43.106.10:80 (*) failed
[Wed Nov 05 10:31:25 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 76.13.218.11:80 (*) failed
[Wed Nov 05 10:31:25 2008] [error] (111)Connection refused: proxy: HTTP: attempt to connect to 209.31.63.30:80 (*) failed
[Wed Nov 05 10:31:27 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 128.242.186.219:80 (*) failed
[Wed Nov 05 10:31:28 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 76.13.218.11:80 (*) failed
[Wed Nov 05 10:31:28 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 76.13.218.11:80 (*) failed
[Wed Nov 05 10:31:30 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 76.13.218.11:80 (*) failed
[Wed Nov 05 10:31:30 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 76.13.218.11:80 (*) failed
[Wed Nov 05 10:31:31 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 76.13.218.11:80 (*) failed
[Wed Nov 05 10:31:32 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 92.43.106.10:80 (*) failed
[Wed Nov 05 10:31:32 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 76.13.218.11:80 (*) failed
[Wed Nov 05 10:31:40 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 92.43.106.10:80 (*) failed
[Wed Nov 05 10:31:41 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 74.6.104.11:80 (*) failed
[Wed Nov 05 10:31:45 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 92.43.106.10:80 (*) failed
[Wed Nov 05 10:31:47 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 74.6.104.11:80 (*) failed
[Wed Nov 05 10:31:48 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 74.6.104.11:80 (*) failed
[Wed Nov 05 10:31:50 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 221.231.148.193:80 (*) failed
[Wed Nov 05 10:31:51 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 221.231.148.193:80 (*) failed
[Wed Nov 05 10:31:57 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 92.43.106.10:80 (*) failed
[Wed Nov 05 10:31:59 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 65.203.229.43:80 (*) failed
[Wed Nov 05 10:32:04 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 74.6.104.11:80 (*) failed
[Wed Nov 05 10:32:09 2008] [error] (110)Connection timed out: proxy: HTTP: attempt to connect to 92.43.106.10:80 (*) failed
```

The connections are, in fact, being made by outside sources. I am going to remove the configuration file for the site that requires a reverse proxy and start Apache again. I'll see what happens and start narrowing down the possible causes.

Thank you,
Chris

---

### Post by chris.zeman on 2008-11-05
I removed the configuration file, started apache, and the problems started again. I disabled all the proxy modules Apache needed for the reverse proxy to work, restarted Apache, and everything is running smoothly now.

Chris

---

### Post by MJN on 2008-11-05
I don't understand. Are you saying you don't have a problem? (not that you necessarily had one before) :confused:

Mathew

---

### Post by chris.zeman on 2008-11-05
Sorry, I used the wrong choice of words.

Users outside my network were using my server as a proxy to access other sites. It seems like quite a bit of traffic was being generated. The IP addresses the traffic was originating from was not on my LAN; they were on the internet. They were mainly accessing forums, and quite a lot of them at that.

Disabling the reverse proxy to the other server on my network did not stop it from happening. Yes, I restarted Apache. I disabled the various proxy modules Apache needs to implement a reverse proxy, restarted Apache, and the traffic has not returned. I believe we're going to just find a similar application to the one that runs on the other internal server (Windows), and run it on the Linux box instead.

---

### Post by MJN on 2008-11-05
You had specifically disabled forward proxying (ProxyRequests Off) and your ProxyPass target was an internal machine.

Hence, you were _not_ acting as an open proxy.

Sure - some bots on the Internet were giving you a go (they trawl the net trying their luck) but your server was effectively denying them access as the proxy requests were being mapped into your internal address space and thus failing (hence the 404 errors given the targets didn't exist).

You are only at risk if you specifically set ProxyRequests ***On***.

Mathew

---

### Post by chris.zeman on 2008-11-05
Ahhhhh.....I understand now. I feel much better now! :) Thank you for your help, Mathew! 

Chris

---

### Post by MJN on 2008-11-06
You're welcome!

---


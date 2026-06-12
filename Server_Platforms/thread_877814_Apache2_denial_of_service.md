---
title: "Apache2 denial of service?"
date: 2008-08-02
forum: Server Platforms
---

### Post by arkopII on 2008-08-02
Hello,

I have an Apache 2 server on Ubuntu Dapper and it is getting very slow. Looking the logs I found this in the error.log and in one of the access logs:
```

[Sat Aug 02 13:08:27 2008] [error] server reached MaxClients setting, consider raising the MaxClients setting
[Sat Aug 02 13:09:15 2008] [notice] child pid 9329 exit signal Segmentation fault (11)
[Sat Aug 02 13:15:19 2008] [notice] child pid 9340 exit signal Segmentation fault (11)
[Sat Aug 02 13:16:03 2008] [notice] child pid 9319 exit signal Segmentation fault (11)
[Sat Aug 02 13:16:13 2008] [notice] child pid 9336 exit signal Segmentation fault (11)
[Sat Aug 02 13:29:52 2008] [notice] child pid 9320 exit signal Segmentation fault (11)
[Sat Aug 02 13:39:42 2008] [notice] child pid 9332 exit signal Segmentation fault (11)
[Sat Aug 02 13:51:17 2008] [notice] child pid 9353 exit signal Segmentation fault (11)
[Sat Aug 02 13:55:11 2008] [notice] child pid 9379 exit signal Segmentation fault (11)
```

```
58.62.142.230 - - [02/Aug/2008:13:54:35 +0200] "GET http://www.vueling.com/skylights/js/dateValidation.js HTTP/1.0" 200 4964 "http://www.vueling.com/index.php?language=ES&utm_source=zan&utm_medium=cpv&utm_campaign=es&cid=174&zanpid=1136626135489064960" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"
87.118.70.19 - - [02/Aug/2008:13:54:34 +0200] "GET http://cyberworksgy.com/cyberworksgy/yabb/YaBB.pl?board=general/20 HTTP/1.0" 200 16264 "http://cyberworksgy.com/cyberworksgy/yabb/YaBB.pl?board=general/20" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)"
202.101.62.9 - - [02/Aug/2008:13:54:35 +0200] "GET http://ads.widgetbucks.com/www/delivery/ajs.php?zoneid=415&cb=71229712326&loc=http%3A//www.dietorganizer.com/ HTTP/1.0" 200 54 "http://www.dietorganizer.com" "Mozilla/4.0 (compatible; MSIE 5.01; Windows 98)"
202.101.62.9 - - [02/Aug/2008:13:54:35 +0200] "GET http://ad.yieldmanager.com/imp?Z=300x250&s=373959&_salt=1866117180&B=12&m=2&u=http%3A%2F%2Fwww.cinemadesktopthemes.com%2F&r=1 HTTP/1.0" 200 656 "http://www.cinemadesktopthemes.com/" "Mozilla/4.0 (compatible; MSIE 5.0; Mac_PowerPC)"
209.67.215.82 - - [02/Aug/2008:13:54:35 +0200] "POST http://niklassolar.ni.funpic.de/wm/guestbook.add.php HTTP/1.0" 200 9 "http://niklassolar.ni.funpic.de/wm/guestbook.add.php" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)"
87.118.70.19 - - [02/Aug/2008:13:54:34 +0200] "GET http://www.uniport.com.ua/forum/index.php?act=Reg&CODE=image&rc=26cc8374c4f92ce3bae8ad28674dee68&p=1 HTTP/1.0" 200 67 "http://www.uniport.com.ua/forum/index.php?act=Reg&CODE=00&coppa_pass=1" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322; XMPP Tiscali Communicator v.10.0.2; .NET CLR 2.0.50727)"
87.118.70.19 - - [02/Aug/2008:13:54:35 +0200] "GET http://santafe-club.ru/forum/login.php?redirect=posting.php&mode=newtopic&f=30 HTTP/1.0" 200 15362 "http://santafe-club.ru/forum/login.php?redirect=posting.php&mode=newtopic&f=30" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; Q312461)"
```

Is this a denial of service attack, can anyone give me an idea of how to avoid it?

Thank you very much.

---

### Post by windependence on 2008-08-02
People tend to get excited when they see this but on a web facing server it's quite normal. I can't tell from just the log you posted how many users were hitting your site, but remember, normal users, script kiddies, and bots will be hitting anything on the net all the time. 

What is your MaxClients setting anyway? How much RAM is on this box. Even when the max is reached, the box should not be segfaulting.

-Tim

---

### Post by arkopII on 2008-08-02
Actually MaxClients in my server is 20 (the default value), what is a usual value for a production server?. 

However I have noticed that there are too much "dummy" queries to my server. Some clients repeat thousands of queries which makes me think of a DoS.

I have tried to add the IPs that are disturbing to hosts.deny but that doesn't work. Do you know how to make apache aware of hosts.deny configuration?

Thanks!

---

### Post by Dedoimedo on 2008-08-02
Hello,

Did you try or consider using the mod_security module?
[http://www.modsecurity.org/](http://www.modsecurity.org/)

Dedoimedo

---

### Post by windependence on 2008-08-02
You really shouldn't do this with a web server unless you want to limit your traffic and deny people seeing your site. This kind of thing is not a ddos, you will know it if and when you get one, and they are usually not random, and most certainly not directed at a small site like yourself. 

Just FYI, on my production server, MaxClients is set to 150.

-Tim

---

### Post by arkopII on 2008-08-02
Well, thank you very much for your information I set MaxClient to 100 and it seems that the server runs better now. I will keep monitoring it to see how it evolves.

Dedoimedo I will consider mod_security, by the way, good Guide about Apache!

Thanks a lot!

---

### Post by arkopII on 2008-08-03
Hello again,

After increasing MaxClients my server runs better but today I have notice that there are more than one hundred IPs making thounsands of request to a server that should be almost idle.

In the log I have found that the GET and POST requests have URLs that don't belong to my server like:

"GET [http://www.python.org](http://www.python.org) HTTP/1.1"
"GET http://forum.skunksworks.net//forum.skunkswo"GET [http://www.ams-net.org//www.ams-net.org/usage/usage_200803.html](http://www.ams-net.org//www.ams-net.org/usage/usage_200803.html) HTTP/1.0"rks.net/Forum9/HTML/main.cgi?action=agree HTTP/1.0"
"GET [http://www.clickboothlnk.com/e/?enc=bngvykfggklq&optionalinfo=&deployid=0&land=0&pid=0](http://www.clickboothlnk.com/e/?enc=bngvykfggklq&optionalinfo=&deployid=0&land=0&pid=0) HTTP/1.0"

I have installed mod_security which is blocking requests with invalid URL encoding or with errors normalizing paremeters values, but I don't have idea if mod_security can help me with this problem.

I tried to add a SecRule to mod_security to filter all requests that don't use the domain of my site, but apache doesn't like "SecRule" and doesn't starts.

The rule I use is: "SecRule REQUEST_URI_RAW "!@rx ^http://mydomain"

Does anyone of you resolved this problem before?

Thank you very much

---

### Post by windependence on 2008-08-03
Only 100? You're doing good!

You're gonna drive yourself nuts trying to eliminate what is normal web traffic. If your server is open to the web (and it has to be to serve pages), you are gonna see this all day and all night every day and every night. 

On my FreeBSD boxes, I can literally set the log to echo on the screen and watch it scroll. It has been doing this for 4 years, and the server has never been compromised. Chill. :)

-Tim

---

### Post by arkopII on 2008-08-04
Ok, windependence... I have not many experience with this and I was seeing that my server was busy doing things that I don't understand...

However, if it is normal web traffic, why the hell the requests go to domains that don't belong to my server?

Thank you very much for your help! ;-)

---

### Post by StickyStyle on 2008-08-04
> **arkopII said:**
> Ok, windependence... I have not many experience with this and I was seeing that my server was busy doing things that I don't understand...

However, if it is normal web traffic, why the hell the requests go to domains that don't belong to my server?

Thank you very much for your help! ;-)

Do you have mod_proxy enabled and configured properly?  GET requests in your log are often people testing if your server is an open proxy (normally making GET's to a page hosting azenv.php), you will see them all the time but they are normally not to the point where you would have to up your MaxClients.  If your seeing a constant stream of these from a single IP (your log looks like someone browsing the internet) you may be an open proxy.

See [http://httpd.apache.org/docs/2.0/mod/mod_proxy.html#access](http://httpd.apache.org/docs/2.0/mod/mod_proxy.html#access)

Also see [http://httpd.apache.org/docs/1.3/misc/FAQ.html#proxyscan](http://httpd.apache.org/docs/1.3/misc/FAQ.html#proxyscan)

---

### Post by MJN on 2008-08-04
As StickyStyle says, it looks like you are running an open proxy hence it is little surprise that your server is receiving abnormal levels of interest.

The key to identifying this is by looking at your logs - you can see that your server is responding with HTTP code 200 - 'OK' - hence it is responding to the request. It doesn't end here though because it might just be responding with your default page....

So, in order to see whether you've anything to worry about you then have to go on to the byte count of the supplied page e.g.
```
58.62.142.230 - - [02/Aug/2008:13:54:35 +0200] "GET http://www.vueling.com/skylights/js/dateValidation.js HTTP/1.0" 200 4964 "http://www.vueling.com/index.php?language=ES&utm_source=zan&utm_medium=cpv&utm_campaign=es&cid=174&zanpid=1136626135489064960" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"
```..shows that in this case the byte count was 4964 bytes. If we take a look at a HTTP request for that page in a packet sniffer:

```
HTTP/1.1 200 OK\r\n
    Request Version: HTTP/1.1
    Response Code: 200
    Date: Mon, 04 Aug 2008 15:48:17 GMT\r\n
    Server: Apache/2.2.3 (Red Hat) PHP/5.1.6\r\n
    Last-Modified: Tue, 13 Nov 2007 15:02:29 GMT\r\n
    ETag: "ca1009-1364-bcd46b40"\r\n
    Accept-Ranges: bytes\r\n
    Content-Length: 4964\r\n
    Keep-Alive: timeout=5, max=100\r\n
    Connection: Keep-Alive\r\n
    Content-Type: application/x-javascript\r\n
    \r\n
```...we see 4964 bytes.

So, your server is running as an open proxy - providing a springboard to others whilst hiding their identity. You need to close it asap - post your config it if you need further help.

Mathew

---

### Post by arkopII on 2008-08-04
Hi,

That was exactly my problem, I had misconfigured the proxy module with "ProxyRequests On"!! :-(

After I changed it to "ProxyRequests Off" all that traffic has stopped.

Thank you very much to all of you.

---

### Post by windependence on 2008-08-04
Sorry arkop, didn't see the 200 codes.

In the future you can use an open proxy detector to check. There are also good open relay detectors for e-mail.

[http://www.proxyserverprivacy.com/free-proxy-detector.shtml](http://www.proxyserverprivacy.com/free-proxy-detector.shtml)

[http://spamlinks.net/prevent-secure-proxy-test.htm#web](http://spamlinks.net/prevent-secure-proxy-test.htm#web)

Note that you will still be getting tons of requests of people testing you for open proxy, mail relay, open ssh connection, etc, so don't be alarmed by that.

-Tim

---


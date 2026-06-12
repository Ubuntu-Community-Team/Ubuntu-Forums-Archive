---
title: "Help! My server is eating all my bandwidth!"
date: 2008-06-06
forum: Server Platforms
---

### Post by zachtib on 2008-06-06
So, i have a 64bit hardy server, if port 80 is forwarding to it (which is the desired setup) then it uses up almost all of my bandwidth, but without port 80 opened, the network is fine.  This is a near fresh-install, with only apache running.

iftop shows a ton of incoming connections on port 80...

what should I do?

---

### Post by Monicker on 2008-06-06
Do your apache access logs show what all these connections are doing?

I would run tcpdump or wireshark and investigate what data is being passed in these connections.

---

### Post by zachtib on 2008-06-06
> **Monicker said:**
> Do your apache access logs show what all these connections are doing?

I would run tcpdump or wireshark and investigate what data is being passed in these connections.

well, I reformatted this server and re set it up less than a month ago, and...


my apache access log is ~286MB! So something is definately going on

here's a random chunk:
```

A%2F%2Fwww.proxy365.biz%2Findex.html" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; MyIE2; TencentT"
207.70.162.165 - - [06/Jun/2008:17:14:53 -0400] "GET http://ad.media-servers.net/rw?title=New%20offer%21&qs=iframe3%3F%2EwggAA2sAwAMewgAWcIDAAIAAAAAAP8AAAAGEgICAAOPNgQALiwDAJaqBQAAAAAAAAAAAAAAAAAAAAAAAAAAAM7MpIacivU%2EAADUWlc3AEDOzKSGnIoFQAAA1FpXNxBAAAAAAAAAAAAAANDGrfIYQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAVMlG5QyNkgTF9IycGmJwc38JwxgUWXwwm7ozfwAAAAA%3D%2C%2Chttp%3A%2F%2Fwww%2Eproxy365%2Ebiz%2Findex%2Ehtml HTTP/1.1" 200 556 "http%3A%2F%2Fwww.proxy365.biz%2Findex.html" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; .NET CLR 1.1.43"
207.70.162.165 - - [06/Jun/2008:17:15:35 -0400] "GET http://ad.media-servers.net/st?ad_type=pop&ad_size=0x0&section=240653&banned_pop_types=29&pop_times=1&pop_frequency=0 HTTP/1.1" 200 4221 "http%3A%2F%2Fwww.proxy365.biz%2Findex.html" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"
207.70.162.165 - - [06/Jun/2008:17:15:35 -0400] "GET http://ad.yieldmanager.com/imp?Z=0x0&y=29&s=240653&_salt=3625657865&B=2&u=http%3A%2F%2Fwww.proxy365.biz%2Findex.html HTTP/1.1" 200 6670 "http%3A%2F%2Fwww.proxy365.biz%2Findex.html" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"
207.70.162.165 - - [06/Jun/2008:17:15:36 -0400] "GET http://ad.media-servers.net/rw?title=New%20offer%21&qs=iframe3%3F%2EwggAA2sAwAMewgAWTwDAAIAAAAAAP8AAAAGEgICAAOPNgQALiwDAFnvBAAAAAAAAAAAAAAAAAAAAAAAAAAAAM7MpIacivU%2EAADAq8tG%2DD%2EOzKSGnIoFQAAAwKvLRghAAAAAAAAAAAAAAICrnKwSQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAZGc1Rj6NkgRxGTHguTisDL4jc5RyiyxXoRf9LgAAAAA%3D%2C%2Chttp%3A%2F%2Fwww%2Eproxy365%2Ebiz%2Findex%2Ehtml HTTP/1.1" 200 556 "http%3A%2F%2Fwww.proxy365.biz%2Findex.html" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"
207.70.162.165 - - [06/Jun/2008:17:24:40 -0400] "GET http://ad.media-servers.net/st?ad_type=pop&ad_size=0x0&section=240653&banned_pop_types=29&pop_times=1&pop_frequency=0 HTTP/1.1" 200 4221 "http%3A%2F%2Fwww.proxy365.biz%2Findex.html" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; .NET CLR 1.1.43"
207.70.162.165 - - [06/Jun/2008:17:24:41 -0400] "GET http://ad.yieldmanager.com/imp?Z=0x0&y=29&s=240653&_salt=4181714763&B=2&u=http%3A%2F%2Fwww.proxy365.biz%2Findex.html HTTP/1.1" 200 6670 "http%3A%2F%2Fwww.proxy365.biz%2Findex.html" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; .NET CLR 1.1.43"
207.70.162.165 - - [06/Jun/2008:17:24:42 -0400] "GET http://ad.media-servers.net/rw?title=New%20offer%21&qs=iframe3%3F%2EwggAA2sAwAMewgAWcIDAAIAAAAAAP8AAAAGEgICAAOPNgQALiwDAJaqBQAAAAAAAAAAAAAAAAAAAAAAAAAAAM7MpIacivU%2EAADUWlc3AEDOzKSGnIoFQAAA1FpXNxBAAAAAAAAAAAAAANDGrfIYQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAJUcyS1%2DPkgSmKJvo1LyXsWBv6TJOrx%2E7iww7ygAAAAA%3D%2C%2Chttp%3A%2F%2Fwww%2Eproxy365%2Ebiz%2Findex%2Ehtml HTTP/1.1" 200 556 "http%3A%2F%2Fwww.proxy365.biz%2Findex.html" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; .NET CLR 1.1.43"
192.168.1.82 - - [06/Jun/2008:19:07:40 -0400] "GET / HTTP/1.1" 301 - "-" "ELinks/0.11.3-5ubuntu2 (textmode; Debian; Linux 2.6.24-16-server x86_64; 222x24-2)"
127.0.0.1 - - [06/Jun/2008:19:07:58 -0400] "GET /collegegeek HTTP/1.1" 404 323 "-" "ELinks/0.11.3-5ubuntu2 (textmode; Debian; Linux 2.6.24-16-server x86_64; 222x24-2)"
127.0.0.1 - - [06/Jun/2008:19:08:07 -0400] "GET / HTTP/1.1" 301 - "-" "ELinks/0.11.3-5ubuntu2 (textmode; Debian; Linux 2.6.24-16-server x86_64; 222x24-2)"
127.0.0.1 - - [06/Jun/2008:19:08:14 -0400] "GET / HTTP/1.1" 301 - "-" "ELinks/0.11.3-5ubuntu2 (textmode; Debian; Linux 2.6.24-16-server x86_64; 222x24-2)"
```

---

### Post by osjak on 2008-06-07
It seems like your server is being used as a proxy. See if you have mod_proxy installed and loading. Just a thought.

---

### Post by zachtib on 2008-06-07
> **osjak said:**
> It seems like your server is being used as a proxy. See if you have mod_proxy installed and loading. Just a thought.

Yes, I do have mod_proxy loaded, but that's only because there are two servers on the network, so it redirects incoming traffic for the second server.

Is this causing a problem?

edit: and can I restrict mod_proxy to only that one site that I need it for?

---

### Post by Monicker on 2008-06-07
> **zachtib said:**
> Yes, I do have mod_proxy loaded, but that's only because there are two servers on the network, so it redirects incoming traffic for the second server.

Is this causing a problem?

edit: and can I restrict mod_proxy to only that one site that I need it for?

Check out the following link.  I believe it has the information you want.

[http://httpd.apache.org/docs/2.0/mod/mod_proxy.html#access](http://httpd.apache.org/docs/2.0/mod/mod_proxy.html#access)

---

### Post by zachtib on 2008-06-07
> **Monicker said:**
> Check out the following link.  I believe it has the information you want.

[http://httpd.apache.org/docs/2.0/mod/mod_proxy.html#access](http://httpd.apache.org/docs/2.0/mod/mod_proxy.html#access)

Ok, I've got the server locked down (I hope) lets see how this works

---

### Post by zachtib on 2008-06-08
Yeah, it worked!

---

### Post by fjkaauw on 2009-04-17
what do you mean with lock down the server, i can not get rid of these get attacks on mij ubuntu 8.10 32bit webserver.
I use a reverse proxy because i use more then one server with only one outside ip address.
Can someone tell me how to lock the server down with the reverse proxy functionality and without the unwanted proxy attemts.
This is a list of my access.log.

----------------------
61.139.105.162 - - [18/Apr/2009:00:42:00 +0200] "GET [http://ad.yieldmanager.com/imp?z=0&Z=0x0&s=529628&y=30](http://ad.yieldmanager.com/imp?z=0&Z=0x0&s=529628&y=30) HTTP/1.1" 302 - "http%3A%2F%2Fwww.onlineea.com%2Findex.html" "Mozilla/4.0 (compatible; MSIE 5.0; W$
61.139.105.162 - - [18/Apr/2009:00:42:13 +0200] "GET [http://ad.yieldmanager.com/imp?z=0&Z=0x0&s=514109&y=30](http://ad.yieldmanager.com/imp?z=0&Z=0x0&s=514109&y=30) HTTP/1.1" 302 - "http%3A%2F%2Fwww.7788.tv%2Findex.html" "Mozilla/4.0 (compatible; MSIE 6.0; Window$
61.139.105.162 - - [18/Apr/2009:00:42:14 +0200] "GET [http://ad.yieldmanager.com/imp?z=0&Z=0x0&s=514109&y=30&B=1](http://ad.yieldmanager.com/imp?z=0&Z=0x0&s=514109&y=30&B=1) HTTP/1.1" 200 6640 "http%3A%2F%2Fwww.7788.tv%2Findex.html" "Mozilla/4.0 (compatible; MSIE 6.0;$
----------------------

Regards, Fred Kaauw

---

### Post by Thirtysixway on 2009-04-19
> **fjkaauw said:**
> what do you mean with lock down the server, i can not get rid of these get attacks on mij ubuntu 8.10 32bit webserver.
I use a reverse proxy because i use more then one server with only one outside ip address.
Can someone tell me how to lock the server down with the reverse proxy functionality and without the unwanted proxy attemts.
This is a list of my access.log.

----------------------
61.139.105.162 - - [18/Apr/2009:00:42:00 +0200] "GET [http://ad.yieldmanager.com/imp?z=0&Z=0x0&s=529628&y=30](http://ad.yieldmanager.com/imp?z=0&Z=0x0&s=529628&y=30) HTTP/1.1" 302 - "http%3A%2F%2Fwww.onlineea.com%2Findex.html" "Mozilla/4.0 (compatible; MSIE 5.0; W$
61.139.105.162 - - [18/Apr/2009:00:42:13 +0200] "GET [http://ad.yieldmanager.com/imp?z=0&Z=0x0&s=514109&y=30](http://ad.yieldmanager.com/imp?z=0&Z=0x0&s=514109&y=30) HTTP/1.1" 302 - "http%3A%2F%2Fwww.7788.tv%2Findex.html" "Mozilla/4.0 (compatible; MSIE 6.0; Window$
61.139.105.162 - - [18/Apr/2009:00:42:14 +0200] "GET [http://ad.yieldmanager.com/imp?z=0&Z=0x0&s=514109&y=30&B=1](http://ad.yieldmanager.com/imp?z=0&Z=0x0&s=514109&y=30&B=1) HTTP/1.1" 200 6640 "http%3A%2F%2Fwww.7788.tv%2Findex.html" "Mozilla/4.0 (compatible; MSIE 6.0;$
----------------------

Regards, Fred Kaauw

Unless you lock it down, anyone can add your website address as a proxy and use it.  See this site for details on securing your system
[http://httpd.apache.org/docs/2.0/mod/mod_proxy.html#access](http://httpd.apache.org/docs/2.0/mod/mod_proxy.html#access)

---


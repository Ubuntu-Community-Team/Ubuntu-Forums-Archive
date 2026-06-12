---
title: "apache2/access.log"
date: 2007-01-15
forum: Server Platforms
---

### Post by WolfJay_83 on 2007-01-15
```
> cat /var/log/apache2/access.log grep -v 192.168

207.210.117.* - - [15/Jan/2007:00:35:57 -0500] "GET [http://www.ougo.com/proxytest.php](http://www.ougo.com/proxytest.php) HTTP/1.0" 404 299 "-" "-"
207.210.117.* - - [15/Jan/2007:00:37:58 -0500] "GET [http://www.ougo.com/proxytest.php](http://www.ougo.com/proxytest.php) HTTP/1.0" 404 299 "-" "-"
207.210.117.* - - [15/Jan/2007:00:50:14 -0500] "GET [http://www.ougo.com/proxytest.php](http://www.ougo.com/proxytest.php) HTTP/1.0" 404 299 "-" "-"
207.210.117.* - - [15/Jan/2007:00:51:38 -0500] "GET [http://www.ougo.com/proxytest.php](http://www.ougo.com/proxytest.php) HTTP/1.0" 404 299 "-" "-"
65.110.11.* - - [15/Jan/2007:00:53:49 -0500] "GET / HTTP/1.0" 200 4143 "-" "-"
207.210.117.* - - [15/Jan/2007:01:02:02 -0500] "GET [http://www.ougo.com/proxytest.php](http://www.ougo.com/proxytest.php) HTTP/1.0" 404 299 "-" "-"
207.210.117.* - - [15/Jan/2007:01:03:23 -0500] "GET [http://www.ougo.com/proxytest.php](http://www.ougo.com/proxytest.php) HTTP/1.0" 404 299 "-" "-"
69.25.135.* - - [15/Jan/2007:04:29:12 -0500] "GET http://www.goclick.com/gcpxy.mod?65.93.12.80" 404 298 "-" "-"
67.29.139.* - - [15/Jan/2007:08:21:52 -0500] "GET [http://www.abcsearch.com/index.html](http://www.abcsearch.com/index.html) HTTP/1.0" 404 301 "-" "Mozilla/4.0 (compatible; MSIE 5.01; Windows NT 5.0)"
```

auth.log.1 has more of the same.

I'm confused why apache is accessing remote sites.  Can anyone shed some light on this issue? Is it possible that someone has managed to use my server to attempt to brute force another host?  I'm not all that knowlegable about apache, so I'm not sure what exactly is going on here.

---

### Post by Biggus on 2007-01-15
I've been trying to work this out too, and from this page : [http://httpd.apache.org/docs/2.0/logs.html](http://httpd.apache.org/docs/2.0/logs.html) , I think it means that someone is trying to see if your Apache setup is configured to act as a proxy.

I don't think it means that you are actually being used as a proxy, simply that someone is trying to.

I may be wrong though.

---


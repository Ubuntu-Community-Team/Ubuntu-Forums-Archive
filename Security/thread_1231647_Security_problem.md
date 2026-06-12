---
title: "Security problem?"
date: 2009-08-04
forum: Security
---

### Post by animuson on 2009-08-04
I was browsing my Apache logs for something specific and noticed this stuff in the access log, it seems kind of odd.

> 
222.215.230.49 - - [02/Aug/2009:01:10:55 -0500] "GET [http://pv.wantsfly.com/prx.php?hash=6FB6773B0DB71A0D45A2756700502A5B99A7A705F7D3](http://pv.wantsfly.com/prx.php?hash=6FB6773B0DB71A0D45A2756700502A5B99A7A705F7D3) HTTP/1.0" 404 326 "-" "Moz$
190.196.23.170 - - [02/Aug/2009:03:11:45 -0500] "GET HTTP/1.1 HTTP/1.1" 400 271 "-" "Toata dragostea mea pentru diavola"
190.196.23.170 - - [02/Aug/2009:03:11:45 -0500] "GET /install.txt HTTP/1.1" 404 267 "-" "Toata dragostea mea pentru diavola"
190.196.23.170 - - [02/Aug/2009:03:11:46 -0500] "GET / HTTP/1.1" 200 477 "-" "Toata dragostea mea pentru diavola"
190.196.23.170 - - [02/Aug/2009:03:11:47 -0500] "GET /cart/ HTTP/1.1" 404 263 "-" "Toata dragostea mea pentru diavola"
190.196.23.170 - - [02/Aug/2009:03:11:47 -0500] "GET /zencart/ HTTP/1.1" 404 265 "-" "Toata dragostea mea pentru diavola"
190.196.23.170 - - [02/Aug/2009:03:11:48 -0500] "GET /zen-cart/ HTTP/1.1" 404 266 "-" "Toata dragostea mea pentru diavola"
190.196.23.170 - - [02/Aug/2009:03:11:48 -0500] "GET /zen/ HTTP/1.1" 404 263 "-" "Toata dragostea mea pentru diavola"
190.196.23.170 - - [02/Aug/2009:03:11:48 -0500] "GET /shop/ HTTP/1.1" 404 263 "-" "Toata dragostea mea pentru diavola"
69.162.70.148 - - [02/Aug/2009:06:49:18 -0500] "GET /w00tw00t.at.ISC.SANS.DFind:) HTTP/1.1" 400 351 "-" "-"
61.156.31.45 - - [02/Aug/2009:12:42:07 -0500] "GET /manager/html HTTP/1.1" 404 330 "-" "Mozilla/3.0 (compatible; Indy Library)"
122.227.164.96 - - [02/Aug/2009:16:56:52 -0500] "GET [http://proxyjudge1.proxyfire.net/fastenv](http://proxyjudge1.proxyfire.net/fastenv) HTTP/1.1" 404 336 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows $
118.171.130.12 - - [02/Aug/2009:18:41:37 -0500] "GET [http://www.zshare.net/](http://www.zshare.net/) HTTP/1.1" 200 1122 "-" "Mozilla/4.0 (compatible; MSIE 4.01; Windows 98)"
81.137.6.81 - - [03/Aug/2009:09:29:23 -0500] "GET [http://www.google.com/imghp?hl=en](http://www.google.com/imghp?hl=en) HTTP/1.1" 404 323 "-" "Internet Explorer 4.01"
122.227.164.96 - - [03/Aug/2009:16:41:43 -0500] "GET [http://proxyjudge2.proxyfire.net/fastenv](http://proxyjudge2.proxyfire.net/fastenv) HTTP/1.1" 404 336 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows $
79.120.177.34 - - [03/Aug/2009:21:31:39 -0500] "GET /phpmyadmin/config/config.inc.php?c=id;uname%20-a HTTP/1.1" 404 350 "-" "crimscanner/1.0"
211.95.78.70 - - [03/Aug/2009:22:34:26 -0500] "POST [http://www.dormaster.com/cgi-bin/textenv.pl](http://www.dormaster.com/cgi-bin/textenv.pl) HTTP/1.1" 404 339 "-" "-"
211.95.78.70 - - [03/Aug/2009:22:34:26 -0500] "POST [http://www.dormaster.com/cgi-bin/textenv.pl](http://www.dormaster.com/cgi-bin/textenv.pl) HTTP/1.1" 404 339 "-" "-"
190.196.23.170 - - [04/Aug/2009:00:41:11 -0500] "GET //user/templates/footer.tpl HTTP/1.1" 404 275 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"
122.227.164.96 - - [04/Aug/2009:01:16:54 -0500] "GET [http://proxyjudge1.proxyfire.net/fastenv](http://proxyjudge1.proxyfire.net/fastenv) HTTP/1.1" 404 336 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows $
64.9.195.251 - - [04/Aug/2009:02:21:33 -0500] "GET //roundcube/ HTTP/1.1" 404 265 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.5) Gecko/2008120$
64.9.195.251 - - [04/Aug/2009:02:21:33 -0500] "GET //webmail/ HTTP/1.1" 404 265 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.5) Gecko/200812012$


I don't run any webmail clients from my server and my phpMyAdmin scripts are located elsewhere on the server, kind of hidden, for specifically that purpose. Should I be concerned?

---

### Post by dragos2 on 2009-08-05
> **animuson said:**
> I was browsing my Apache logs for something specific and noticed this stuff in the access log, it seems kind of odd.



I don't run any webmail clients from my server and my phpMyAdmin scripts are located elsewhere on the server, kind of hidden, for specifically that purpose. Should I be concerned?

"Toata dragostea mea pentru diavola" translates to "All my love to devil(woman)"

---

### Post by wojox on 2009-08-05
I wouldn't worry, a majority of the status codes are 404 - Not Found.
Here's a link to status codes:

[http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)

---

### Post by cdenley on 2009-08-05
> **wojox said:**
> I wouldn't worry, a majority of the status codes are 404 - Not Found.
Here's a link to status codes:

[http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)

I second that. Scripts are always going to be checking random web servers for known vulnerabilities. These kind of "attacks" are common. I don't see anything you should be concerned about.

---

### Post by modmadmike on 2009-10-20
> **cdenley said:**
> I second that. Scripts are always going to be checking random web servers for known vulnerabilities. These kind of "attacks" are common. I don't see anything you should be concerned about.

Same exact IP [122.227.164.96] trying to do port scans on my laptop with a 3G card but thankfully fire-starter blocks them.

---

### Post by cdenley on 2009-10-20
> **modmadmike said:**
> Same exact IP [122.227.164.96] trying to do port scans on my laptop with a 3G card but thankfully fire-starter blocks them.

Because you wouldn't want to get exploited by a vulnerability that would only exist if you were running some outdated web application. You would probably be safer dropping firestarter unless you misconfigured your system. If you have no services listening for connections, port scans (or the "attack" in this thread) can't compromise your security

---

### Post by witeshark17 on 2009-10-21
IMO, the current majority of "attacks" are based on auto scripts running off servers and individual PC's with the most efficient possible bandwidth use. In this light, a trend should begin to emerge showing a tendency of attempted intrusions to be using outdated methods that try to max the biggest possible "cookie cutter" patterns of exposed computers and ports. I think the logs you posted are possibly an example of this idea.

---


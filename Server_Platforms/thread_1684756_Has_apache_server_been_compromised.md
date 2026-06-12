---
title: "Has apache server been compromised?"
date: 2011-02-09
forum: Server Platforms
---

### Post by Melpomene on 2011-02-09
Hello, I recently installed Apache2 on my ubuntu server and as I was looking in the logfiles I noticed some strange entries. Could it be that my server has been compromixed or that my apache is proxying traffic by some fault of mine?

I am also running an internal TOR node on my computer with exit policy *:* so it should not be an exitnode.  

> 
173.11.73.211 - - [08/Feb/2011:16:56:05 +0100] "GET [http://zerg.helllabs.net/cgi-bin/textenv.pl?a=80&b=83.233.147.121](http://zerg.helllabs.net/cgi-bin/textenv.pl?a=80&b=83.233.147.121) HTTP/1.0" 404 502 "-" "Mozilla/4.0 (compatible; MSIE 5.5; Windows NT 4.0)"
212.26.193.118 - - [08/Feb/2011:18:48:03 +0100] "GET [http://www.pr0.net/deny2/azenv.php](http://www.pr0.net/deny2/azenv.php) HTTP/1.1" 404 493 "-" "-"
212.26.193.118 - - [08/Feb/2011:18:48:03 +0100] "CONNECT [www.donniepinkston.net:80](www.donniepinkston.net:80) HTTP/1.1" 405 546 "-" "-"
71.130.111.195 - - [08/Feb/2011:19:34:14 +0100] "GET [http://www.donniepinkston.net/pr0x/azenv.php](http://www.donniepinkston.net/pr0x/azenv.php) HTTP/1.1" 404 503 "-" "-"
71.130.111.195 - - [08/Feb/2011:19:34:14 +0100] "CONNECT [www.anonymitytest.com:80](www.anonymitytest.com:80) HTTP/1.1" 405 545 "-" "-"
216.104.15.142 - - [08/Feb/2011:23:30:28 +0100] "GET /tor/status-vote/current/consensus/14C131+27B6B5+585769+805509+D586D1+E8A9C4+ED03BB.z HTTP/1.0" 404 565 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
173.11.73.211 - - [09/Feb/2011:00:18:42 +0100] "GET [http://zerg.helllabs.net/cgi-bin/textenv.pl?a=80&b=83.233.147.121](http://zerg.helllabs.net/cgi-bin/textenv.pl?a=80&b=83.233.147.121) HTTP/1.0" 404 502 "-" "Mozilla/4.0 (compatible; MSIE 5.5; Windows NT 4.0)"
208.80.194.35 - - [09/Feb/2011:00:56:44 +0100] "GET / HTTP/1.0" 200 7018 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; FunWebProducts; .NET CLR 1.1.4322; ZangoToolbar 4.8.2; .NET CLR 2.0.50727)"


---

### Post by wojox on 2011-02-09
No. 

404 means Document not found — the requested file was not found on the server. Possibly because it was deleted, or never existed before. Often caused by misspellings of URLs.

405 means The method you are using to access the file is not allowed.

Just script kiddies acting like kiddies.


This one I'm not sure about:

```
208.80.194.35 - - [09/Feb/2011:00:56:44 +0100] "GET / HTTP/1.0" 200 7018 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; FunWebProducts; .NET CLR 1.1.4322; ZangoToolbar 4.8.2; .NET CLR 2.0.50727)" 
```

200 means Ok — the file which the client requested is available for transfer. This is the response code you want to see all of your users receiving.

---

### Post by Melpomene on 2011-02-09
So basically it's just someone who has tired to use the GET and CONNECT command and my webserver have told them that they can't? 

That's a relief, thanks for the quick reply!

---

### Post by wojox on 2011-02-09
> **Melpomene said:**
> So basically it's just someone who has tired to use the GET and CONNECT command and my webserver have told them that they can't? 

That's right. :p

---


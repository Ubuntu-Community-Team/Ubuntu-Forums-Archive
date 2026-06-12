---
title: "Interesting entry in Apache Log"
date: 2009-02-13
forum: Security
---

### Post by punx45 on 2009-02-13
i noticed this recently:

```

22.208.183.147 - - [08/Feb/2009:18:25:45 -0500] "GET http://www.graduateszone.com/prx1.php?hash=E5874D1E25C9C37362D81EF4005001F25DD18ACE0FCB HTTP/1.0" 404 277 "-" "Mozilla/4.0 (compati
ble; MSIE 6.0; Windows NT 5.0)"

```

i found it odd because graduateszone isnt my domain.   since the server is mostly for tinkering and sharing a few things with friends, most of the traffic is dubious, so i visited the URL.   the contents of the page was 

```

HTTP_PROXY_CONNECTION: 
HTTP_X_FORWARDED_FOR: 
HTTP_VIA: 
HTTP_MAX_FORWARDS: 
REMOTE_ADDR=[COLOR="Red"]<an acutal IP>[/COLOR]
REMOTE_HOST=
HTTP_PC_REMOTE_ADDR=
HTTP_X_FWD_IP_ADDR=
HTTP_CONNECTION=
VIA: 
HTTP_FORWARDED: 
FORWARDED: 
HTTP_X_BLUECOAT_VIA: 
HTTP_PROXY____: 
HTTP_PROXY___________: 
HTTP_X_HOST: 
HTTP_X_REFERER: 
HTTP_X_SERVER_HOSTNAME: 
PROXY_HOST: 
PROXY_PORT: 
PROXY_REQUEST: 
HTTP_CLIENT_IP: 
HTTP_PRAGMA: 
super or gateway or noproxy
Level:1
´úÀí¼¶±ð=³¬¼¶´úÀí
³¬¼¶´úÀí1=³¬¼¶´úÀí
´úÀí¼¶±ð=³¬¼¶´úÀí

```

the IP listed was my current public IP address.   it appears to be some sort of tool to gather information about the server.   im not too worried since none of the other fields were filled in.   i have been getting requests for things related to roundcube php mail (which I don't use)   so i am guessing this is some sort of recon for the eventual exploit attempt to the roundcube php flaw.

i searched the forum and google for any discussions on this and didn't find much (other than a yahoo answers thread where the given advice was "ignore it, someone probably just put the wrong ip in the browser" ](*,))  so i figured i would start a thread for discussion if any is warranted.

even more interesting, is that this HTTP request originated from 22.208.183.147, the Department of Defense Network Information Center, according to whois.

---

### Post by madnak on 2009-02-15
I would say it was an attempt to exploit a misconfiguration in a web proxy (Apache mod_proxy for example) to forward requests through your machine. Possibly someone scanning for open proxies.

I'm not certain but that's what I think it is.
If that helps?

---

### Post by punx45 on 2009-02-16
yeah, thats what i figured.   im also guessing that the originating IP is spoofed, since the same request has been coming from other domains as well.   unless a computer at the DOD caught a trojan and is a botnet zombie?

---

### Post by cb951303 on 2009-02-16
Here are some from my server running debian 4.0

> 
140.125.81.110 - - [14/Feb/2009:18:47:25 +0000] "GET /w00tw00t.at.ISC.SANS.DFind:) HTTP/1.1" 400 322 "-" "-"
65.41.197.86 - - [14/Feb/2009:20:16:20 +0000] "GET [http://www.yahoo.com/](http://www.yahoo.com/) HTTP/1.1" 302 318 "-" "Mozilla/4.0 (compatible; MSIE 4.01; Windows NT)"
140.125.81.110 - - [15/Feb/2009:14:20:20 +0000] "GET /w00tw00t.at.ISC.SANS.DFind:) HTTP/1.1" 400 322 "-" "-"
196.200.138.134 - - [15/Feb/2009:20:50:10 +0000] "GET //roundcube/ HTTP/1.1" 404 304 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.5) Gecko/2008120122 Firefox/3.0.5"
196.200.138.134 - - [15/Feb/2009:20:50:10 +0000] "GET //webmail/ HTTP/1.1" 404 302 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.5) Gecko/2008120122 Firefox/3.0.5"
213.77.105.229 - - [15/Feb/2009:21:16:02 +0000] "GET /w00tw00t.at.ISC.SANS.DFind:) HTTP/1.1" 400 322 "-" "-"
206.156.254.100 - - [16/Feb/2009:13:01:31 +0000] "GET HTTP/1.1 HTTP/1.1" 400 322 "-" "Toata dragostea mea pentru diavola"
206.156.254.100 - - [16/Feb/2009:13:01:31 +0000] "GET /roundcube//bin/msgimport HTTP/1.1" 404 318 "-" "Toata dragostea mea pentru diavola"


and it's been only 4 days since I paid for this VPS :D

EDIT: it think it looks for roundcube(webmail software) and webmail to exploit.

---

### Post by punx45 on 2009-02-16
yeah i have been seeing the "Toata dragostea mea pentru diavola" alot too.

---


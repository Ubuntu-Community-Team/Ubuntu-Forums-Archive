---
title: "apache2 dns oddity?"
date: 2008-06-10
forum: Server Platforms
---

### Post by narghile on 2008-06-10
hello everyone..

I'm having problems setting up my webserver. Ive searched the forums and google relentlessly to figure this out.

I've just installed the server edition, and have everything working correctly. i can browse my site on the local network, php, mysql., everything works locally... 

But if i enter my external ip or dynamic dns address.. i get forwarded to my servers local ip address. this of course doesn't work from the internet(502 bad gateway). If i enter the local hostname [http://nargserv.lan](http://nargserv.lan) it goes straight to 192.133...

i cant seem to figure out why this is happening...

---

### Post by hyper_ch on 2008-06-10
I don't get the problem where what works and where not...

---

### Post by narghile on 2008-06-10
if i enter my external ip or dynamic dns address, i get fowarded to my internal ip. even if im on an computer outside my local network.

edit!

---

### Post by hyper_ch on 2008-06-10
seems you didn't setup a port forward on the router but a IP redirect

---

### Post by narghile on 2008-06-10
hmm. pretty sure i did, i use a clark connect gateway, and ive never set it up to redirect the ip, just a standard port foward... dont think i can even do that with CC

---

### Post by narghile on 2008-06-10
ok well i have to sleep now. ill check this thread in the morning...

---

### Post by osjak on 2008-06-10
Here's what happens when I try to connect:

```

myhost:~# telnet 96.3.83.251 80
Trying 96.3.83.251...
Connected to 96.3.83.251.
Escape character is '^]'.
GET /index.htm HTTP/1.1 host:96.3.83.251

HTTP/1.1 400 Bad Request
Date: Tue, 10 Jun 2008 10:17:51 GMT
Server: Apache/2.2.3 (Ubuntu) PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c
Content-Length: 342
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>400 Bad Request</title>
</head><body>
<h1>Bad Request</h1>
<p>Your browser sent a request that this server could not understand.<br />
</p>
<hr>
<address>Apache/2.2.3 (Ubuntu) PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c Server at nargserv.lan Port 80</address>
</body></html>
Connection closed by foreign host.
```
That tells me that my request got to your Apache. Nothing wrong with DNS per se. Check if you have any rewrite rules set that would redirect somewhere else. WordPress has its own rewrite rules, if I'm not mistaken, so check for those as well.

---

### Post by cdenley on 2008-06-10
```

cdenley@ubuntu:~$ wget http://nargnet.pointclark.net/
--08:56:24--  http://nargnet.pointclark.net/
           => `index.html'
Resolving nargnet.pointclark.net... 96.3.83.251
Connecting to nargnet.pointclark.net|96.3.83.251|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: wp/ [following]
--08:56:25--  http://nargnet.pointclark.net/wp/
           => `index.html'
Reusing existing connection to nargnet.pointclark.net:80.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://192.133.7.2/wp/ [following]
--08:56:25--  http://192.133.7.2/wp/
           => `index.html'
Connecting to 192.133.7.2:80...

```
Apache is sending a redirect back to the client. Judging from the "wp" directory, osjak is probably right about wordpress.

---

### Post by stoneybroke on 2008-06-10
Well I am having the same problem. I can see the website on localhost but I can't access it from the web. I have a registered domain name and when I enter the url I am sent to the company I registered my domain name with. If I use ping or dig it also goes to the same company and not my website.

Like narghile I followed every instruction in the Ubuntu installation file, so any help for narghile would also help me.

Thanks.

---

### Post by cdenley on 2008-06-10
> **stoneybroke said:**
> Well I am having the same problem. I can see the website on localhost but I can't access it from the web. I have a registered domain name and when I enter the url I am sent to the company I registered my domain name with. If I use ping or dig it also goes to the same company and not my website.

Like narghile I followed every instruction in the Ubuntu installation file, so any help for narghile would also help me.

Thanks.

Sounds like a completely different problem. The OP has his domain name resolving correctly, but wordpress is redirecting clients to a LAN IP. You are having DNS issues. Try contacting the company you purchased the domain from.

---

### Post by narghile on 2008-06-10
well i checked to see if my php redirect was wierd in the document root. i changed it from 

<?php
header( 'Location: wp/ ) ;
?>

to

<?php
header( 'Location: [http://nargnet.pointclark.net/wp](http://nargnet.pointclark.net/wp)' ) ;
?>

no avail.

---

### Post by cdenley on 2008-06-10
As you can see from the wget output I posted, there are 2 redirects. You found the first.

---

### Post by narghile on 2008-06-10
you guys are right i can connect to my gallery just fine.. i prolly got the wordpress configuration wrong.. :KS :KS: KS

---


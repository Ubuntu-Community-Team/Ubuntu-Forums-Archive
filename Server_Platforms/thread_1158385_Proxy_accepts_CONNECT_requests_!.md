---
title: "Proxy accepts CONNECT requests ?!"
date: 2009-05-13
forum: Server Platforms
---

### Post by wattaman on 2009-05-13
Hi!
I used a web vulnerability scanner recently to test my server and (among other threads) it says that **Proxy accepts CONNECT requests**
The only advice they're giving in *Restrict proxy access to valid users and/or hosts. Deny CONNECT requests.*
Does anyone knows how to do it? And also, what do they mean?

---

### Post by cdenley on 2009-05-13
> **wattaman said:**
> Hi!
I used a web vulnerability scanner recently to test my server and (among other threads) it says that **Proxy accepts CONNECT requests**
The only advice they're giving in *Restrict proxy access to valid users and/or hosts. Deny CONNECT requests.*
Does anyone knows how to do it? And also, what do they mean?

In hardy, if somebody sends a proxy request like:
```

CONNECT www.google.com:80 HTTP/1.0

```
then for some reason, apache treats the CONNECT command like a GET, ignores [www.google.com:80](www.google.com:80) as it should, and returns the equivalent of
```

GET / HTTP/1.0

```
This appears to be fixed in jaunty, but doesn't pose a security risk. I guess the scanner you're using sees your web server doesn't respond with a "405 Method Not Allowed", and assumes your server allows proxy connections, which probably is not the case.

---

### Post by wattaman on 2009-05-14
Thanks for clarifing this for me.
However, to feel myself better, is there a way to do what they said, e.g. "*Restrict proxy access to valid users and/or hosts*" :)
I have Ubuntu 8.04, BTW.
Thanks again!



_So I won't start another thread:_
I come back with another thing the scanner revealed, not related to this. It found a lot of pages (with forms) on the site vulnerable to XSS attacs, they say, and the solution they provide is *"Your script should filter metacharacters from user input"*. Now, I'm not a coder and have no idea how to do it, besides I update the scripts at regular times and don't want to modify their files.
So, the question is: if there a script or something I can install on the server side to filter these user input/output so it will block the XSS attacks? Something simple, easy to use, for noobs :)
Thanks!

---

### Post by cdenley on 2009-05-14
> **wattaman said:**
> Thanks for clarifing this for me.
However, to feel myself better, is there a way to do what they said, e.g. "*Restrict proxy access to valid users and/or hosts*" :)

Are you running a proxy server? If not, it may be difficult to restrict access to a non-existent service.

> **wattaman said:**
> 
I come back with another thing the scanner revealed, not related to this. It found a lot of pages (with forms) on the site vulnerable to XSS attacs, they say, and the solution they provide is *"Your script should filter metacharacters from user input"*. Now, I'm not a coder and have no idea how to do it, besides I update the scripts at regular times and don't want to modify their files.
So, the question is: if there a script or something I can install on the server side to filter these user input/output so it will block the XSS attacks? Something simple, easy to use, for noobs :)
Thanks!
Probably another false positive. I would have to see your scripts to be sure. Sometimes scripts need to sanitize data for certain input fields to prevent XSS attacks. However, not all input fields can be used for XSS attacks, and I'm not sure how that scanner is even testing for whether your scripts filter metacharacters. If the scripts you're using were installed from the ubuntu repos and you've installed security updates, I'd say there isn't a problem with the scripts.

---

### Post by justatemptest on 2009-05-14
CONNECT is a verb that open a TCP connection through your server. It is used in order to proxy SSL connections. It's abusable. If you don't know what you're doing and don't need it, disable it.

---

### Post by cdenley on 2009-05-14
> **justatemptest said:**
> CONNECT is a verb that open a TCP connection through your server. It is used in order to proxy SSL connections. It's abusable. If you don't know what you're doing and don't need it, disable it.
He probably doesn't have it enabled, as I explained. Hardy did not return a 405 error for CONNECT requests when it was disabled. You can test it with this command.
```

echo -e "CONNECT google.com:443 HTTP/1.0\n"|nc localhost 80

```
If you get output like:
```

HTTP/1.0 200 Connection Established
Proxy-agent: Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch mod_python/3.3.1 Python/2.6.2 mod_ssl/2.2.11 OpenSSL/0.9.8g

```
then it's enabled. If you get the same thing as this output:
```

echo -e "GET / HTTP/1.0\n"|nc localhost 80

```
then it's disabled.

---

### Post by wattaman on 2009-05-15
Thanks, guys!
So, in order:
First of all, you've probably already realised I'm a noob, so... I might not be able to give all the technical details even if I want to :) But what I know for sure is:
- I've rented my own server running Ubuntu 8.04
- As far as I know, there's no proxy installed by me, unless it come by default with the Ubuntu, when the hosting company installed it
- I've tried > echo -e "CONNECT google.com:443 HTTP/1.0\n"|nc localhost 80 in putty and it displays this > localhost: forward host lookup failed: Unknown host. I don't know if I understood it right. Anyway, I've also tried > echo -e "CONNECT google.com:443 HTTP/1.0\n"|nc 223.123.321.43 80 and it shows this:
> HTTP/1.1 405 Method Not Allowed
Date: Fri, 15 May 2009 08:37:39 GMT
Server: Apache
Allow: GET,HEAD,POST,OPTIONS
Vary: Accept-Encoding
Content-Length: 234
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>405 Method Not Allowed</title>
</head><body>
<h1>Method Not Allowed</h1>
<p>The requested method CONNECT is not allowed for the URL /index.htm.</p>
</body></html>

... _is it OK?_ justatemptest, I'd like to disable it, but don't know how. *BTW, the IP above is just an example, I used my server's primer IP. A have also a second IP.*

_As for the XSS testing:_
- the software I use to test the site is Acunetix Web Vulnerability Scanner and the site is a E107 - it shows those XSS warning for the comment pages, login pages, sign up (user forms); the program shows me examples of what script codes it tried to input in the forms and the response. The report page is huge, but here's an example:
> /comment-n55.html 
Details 
The POST variable comment has been set to <DIV+STYLE="width:expression(alert(884210140174))%3B"> . 
Request 
POST /comment-n55.html HTTP/1.0
Accept: */*
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; .NET CLR 1.1.4322)
Host: atat.ro
Content-Length: 249
Cookie: PHPSESSID=1fa5d3f26401de957806ad76abd2a1ce;sid=e7bd9f6a09b973bb117557fdc6493889;counter_unique=pub;__utma=177195445.1373808749.1242247523.1242247523.1242247523.1;__utmb=177195445.0.10.1242247523;__utmc=177195445;__utmz=177195445.1242247524.1.1.utmcsr=(direct)|utmccn=(direct)|utmcmd=(none);e107_tdOffset=318;e107_tdSetTime=1242247205;e107_tzOffset=-180;GoogleAdServingTest=Good;t123v=1
Connection: Close
Pragma: no-cache
Acunetix-Product: WVS/5.1 (Acunetix Web Vulnerability Scanner - NORMAL)
Acunetix-Scanning-agreement: Third Party Scanning PROHIBITED
Acunetix-User-agreement: [http://www.acunetix.com/wvs/disc.htm](http://www.acunetix.com/wvs/disc.htm)

subject=Felicitari%20virtuale&author_name=111-222-1933email@address.tst&comment=<DIV+STYLE="width:expression(alert(884210140174))%3B">&helpb=111-222-1933email@address.tst&preimageselect=%5Bsize%3D7%5D%5B%2Fsize%5D&commentsubmit=Adaugati%20comentariu 
Response 
HTTP/1.1 200 OK
Date: Wed, 13 May 2009 21:20:11 GMT
Server: Apache
X-Powered-By: PHP/5.2.4-2ubuntu5.6
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
Pragma: no-cache
Vary: Accept-Encoding
Content-Length: 1462
Connection: close
Content-Type: text/html 


Anyway, like I've said, I'm not thinking to modify the site scripts, because I update them all the time. I'm hoping to find an easier sollution to filter those metachars, if it exists; maybe there's a php.ini trock or .htaccess that can do it, or another script that can be installed on the server side

---


---
title: "Apache gives me html ..."
date: 2005-10-21
forum: Server Platforms
---

### Post by dbee on 2005-10-21
Does anyone know why my apache sends out html files that aren't parsed by my browser ?

The browser works fine. It must be an apache problem. 

Thanks

---

### Post by LordHunter317 on 2005-10-21
You probably are having mime type issues.  What are the extensions on the file?

---

### Post by Psy-Q on 2005-10-21
Can you telnet into your webserver and get a page manually to see what the "Content-type part" of the header looks like?

```
rca@vanity:~$ telnet (undisclosed host) 80
Trying (some IP address)...
Connected to (undisclosed host).
Escape character is '^]'.
GET / HTTP/1.0

HTTP/1.1 200 OK
Date: Fri, 21 Oct 2005 05:16:31 GMT
Server: Apache/2.0.54 (Debian GNU/Linux) PHP/4.3.10-16
X-Powered-By: PHP/4.3.10-16
Connection: close
**Content-Type: text/html; charset=ISO-8859-1**

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
... more HTML here ...

```

Does it say "text/plain" with your server? If so:

[LIST]
[*]Does /etc/mime.types exist on your server and does it contain the text/html type for files ending in .html, .htm etc.? 
[*]Is MIME Magic enabled in your Apache configuration (for Apache 2, load the module mod_mime_magic.so, which should be loaded by default).
[/LIST]

Can't think of anything else off-hand.

---

### Post by LordHunter317 on 2005-10-21
FWIW, he doesn't have to have mime_magic loaded, and it may/may not reliably detect anyway.

---

### Post by dbee on 2005-10-21
I have telnet disabled on my system unfortunately.

The file I'm trying to serve is a .html

I have this in my conf/mime.types

text/html                       html htm
text/parityfec
text/plain                      asc txt

---

### Post by heimo on 2005-10-21
[quote=dbee]I have telnet disabled on my system unfortunately.
[/quote]

Psy-Q meant telnetting to the http port (80). You don't need to have telnet server running. Just telnet localhost 80 (if you're on that machine) and type:
 ```
GET / HTTP/1.0
```
hit enter couple times and you should see the front page of your default site and the headers. You could use some browser plugin to do this too. Check those other suggestions, it sure sounds like mime-type problem.

---

### Post by dbee on 2005-10-21
cool, thanks guys

root@ubuntu:/usr/lib # telnet 127.0.0.1 80
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
GET / HTTP/1.0

HTTP/1.1 200 OK
Date: Fri, 21 Oct 2005 06:37:48 GMT
Server: Microsoft-IIS/5.0
Last-Modified: Sun, 21 Nov 2004 14:35:21 GMT
ETag: "64eaf-5b0-a64a7c40"
Accept-Ranges: bytes
Content-Length: 1456
Connection: close
Content-Type: text/plain

... btw I have server sig replacement working, so it's not actually an IIS server.

---

### Post by LordHunter317 on 2005-10-21
Server sig replacement is retarded.  Turn that crap off.

Anyway, as I suspected, you're sending the wrong content type.  Post your httpd.conf, sites-enabled/000-default (if you're still using it) and ls -l on /var/www/

---


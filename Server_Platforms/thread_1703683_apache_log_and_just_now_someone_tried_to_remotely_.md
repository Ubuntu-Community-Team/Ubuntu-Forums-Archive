---
title: "apache log and just now someone tried to remotely access desktop"
date: 2011-03-09
forum: Server Platforms
---

### Post by sdowney717 on 2011-03-09
came back to see on the screen a message requesting remote desktop control.
So I said no and went into remote desktop and said never allow connection.
I had recently hosted a PHP app on the home pc for testing purposes using apache.

here are some of the last logs entries

```
127.0.0.1 - - [08/Mar/2011:18:26:34 -0500] "POST /z3950search.php HTTP/1.1" 200 1731 "http://localhost/z3950search.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.15) Gecko/20110303 Ubuntu/10.10 (maverick) Firefox/3.6.15"
127.0.0.1 - - [08/Mar/2011:18:26:37 -0500] "GET /favicon.ico HTTP/1.1" 404 500 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.15) Gecko/20110303 Ubuntu/10.10 (maverick) Firefox/3.6.15"
127.0.0.1 - - [08/Mar/2011:18:26:38 -0500] "GET /favicon.ico HTTP/1.1" 404 500 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.15) Gecko/20110303 Ubuntu/10.10 (maverick) Firefox/3.6.15"
58.218.204.110 - - [08/Mar/2011:19:19:31 -0500] "GET http://www.seektwo.com/proxy-1.php HTTP/1.1" 404 533 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
58.218.204.110 - - [08/Mar/2011:23:27:23 -0500] "GET http://www.shopsline.com/proxyheader.php HTTP/1.1" 404 539 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
58.218.199.147 - - [09/Mar/2011:03:19:50 -0500] "GET http://www.travelimgusa.com/ip.php HTTP/1.1" 404 533 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
58.218.199.147 - - [09/Mar/2011:05:48:58 -0500] "GET http://ppcfinder.net/judge.php HTTP/1.1" 404 529 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
217.155.196.113 - - [09/Mar/2011:06:49:52 -0500] "GET / HTTP/1.1" 200 357 "http://ubuntuforums.org/showthread.php?t=1701976&page=3" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.2.15) Gecko/20110303 Firefox/3.6.15"
217.155.196.113 - - [09/Mar/2011:06:49:52 -0500] "GET /favicon.ico HTTP/1.1" 404 506 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.2.15) Gecko/20110303 Firefox/3.6.15"
217.155.196.113 - - [09/Mar/2011:06:49:55 -0500] "GET /favicon.ico HTTP/1.1" 404 506 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.2.15) Gecko/20110303 Firefox/3.6.15"
58.218.204.110 - - [09/Mar/2011:07:39:04 -0500] "GET http://ppcfinder.net/judge.php HTTP/1.1" 404 529 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
58.218.204.110 - - [09/Mar/2011:15:59:48 -0500] "GET http://piceducation.com/proxyheader.php HTTP/1.1" 404 538 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
58.218.199.147 - - [09/Mar/2011:16:10:05 -0500] "GET http://www.cjpjp.com/proxyheader.php HTTP/1.1" 404 535 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
```

---

### Post by elliotbeken on 2011-03-09
i am not quite sure what you are saying but if you want to block those IP address from accessing your server/network you could creaye am access list on your router/gateway or even create a simple .htaccess file on your server to deny them access hope this helps

---

### Post by sdowney717 on 2011-03-09
I thought it interesting to see someone trying to break in.

I dont see much point of blocking those as I think more different ones will just keep knocking on the door

---


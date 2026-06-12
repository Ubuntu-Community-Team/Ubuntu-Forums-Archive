---
title: "Why/how? Entries in apache2 logs, not vhost logs? Invalid method in request \x16\x03\"
date: 2013-06-08
forum: Security
---

### Post by Lido on 2013-06-08
I'm running a production LAMP server with 12.04 LTS and the sites seem to be running fine, SSL seems to be configured right and working ok. The vhosts are logging both regular and secure access and errors in their correct directories and things appear to be mostly ok. The problem is that in /var/log/apache2, I've got fairly regular lines like the ones below BUT: these same ip addresses are NOWHERE in any of the vhost log files - neither access nor error. What does it mean, how are they doing it? I've searched the web quite a bit about this and most of the information talks about faulty SSL configuration (i.e. people having trouble setting up ssl and getting these errors when they try to connect). There's one thread on webmasterworld talking about security scanners creating these entries, but I still can't figure out how they'd connect to the server and only hit the main apache logs without getting to the regular vhost logs for the site. When I telnet to port 443, I get a 400 error saying something about you can't talk plain html to an ssl port (including a line stating that I'm running Ubuntu and which version of apache I'm on unfortunately), but THOSE connections show up in the vhost log, not the apache2 logs. What's the deal?

```
$ tail /var/log/apache2/error.log
[Fri Jun 07 20:05:18 2013] [error] [client 157.#.#.#] Invalid method in request \x16\x03\x01
[Fri Jun 07 20:39:13 2013] [error] [client 157.#.#.#] Invalid method in request \x16\x03\x01
[Fri Jun 07 20:43:22 2013] [error] [client 157.#.#.#] Invalid method in request \x16\x03\x01
[Fri Jun 07 20:44:51 2013] [error] [client 157.#.#.#] Invalid method in request \x16\x03\x01
[Fri Jun 07 21:45:20 2013] [error] [client 157.#.#.#] Invalid method in request \x16\x03\x01
[Fri Jun 07 23:48:34 2013] [error] [client 109.#.#.#] Invalid method in request \x16\x03\x01
[Sat Jun 08 02:58:46 2013] [error] [client 66.#.#.#] Invalid method in request \x16\x03\x01
[Sat Jun 08 02:58:46 2013] [error] [client 66.#.#.#] Invalid method in request \x16\x03
[Sat Jun 08 02:58:47 2013] [error] [client 66.#.#.#] Invalid method in request \x16\x03\x01
[Sat Jun 08 02:58:47 2013] [error] [client 66.#.#.#] Invalid method in request \x16\x03
```

```
$ tail /var/log/apache2/other_vhosts_access.log
mydomain.com:80 157.#.#.# - - [07/Jun/2013:20:05:18 -0700] "\x16\x03\x01" 501 280 "-" "-"
mydomain.com:80 157.#.#.# - - [07/Jun/2013:20:39:13 -0700] "\x16\x03\x01" 501 280 "-" "-"
mydomain.com:80 157.#.#.# - - [07/Jun/2013:20:43:22 -0700] "\x16\x03\x01" 501 280 "-" "-"
mydomain.com:80 157.#.#.# - - [07/Jun/2013:20:44:51 -0700] "\x16\x03\x01" 501 280 "-" "-"
mydomain.com:80 157.#.#.# - - [07/Jun/2013:21:45:20 -0700] "\x16\x03\x01" 501 280 "-" "-"
mydomain.com:80 109.#.#.# - - [07/Jun/2013:23:48:34 -0700] "\x16\x03\x01" 501 280 "-" "-"
mydomain.com:80 66.#.#.# - - [08/Jun/2013:02:58:46 -0700] "\x16\x03\x01" 501 280 "-" "-"
mydomain.com:80 66.#.#.# - - [08/Jun/2013:02:58:46 -0700] "\x16\x03" 501 279 "-" "-"
mydomain.com:80 66.#.#.# - - [08/Jun/2013:02:58:47 -0700] "\x16\x03\x01" 501 280 "-" "-"
mydomain.com:80 66.#.#.# - - [08/Jun/2013:02:58:47 -0700] "\x16\x03" 501 279 "-" "-"
```

---

### Post by CharlesA on 2013-06-08
Things that make you go "hmmmm"

[http://www.noah.org/wiki/Apache2_Invalid_method_in_request_%5Cx16%5Cx03%5Cx01](http://www.noah.org/wiki/Apache2_Invalid_method_in_request_%5Cx16%5Cx03%5Cx01)
[http://ubuntuforums.org/showthread.php?t=806884](http://ubuntuforums.org/showthread.php?t=806884)

What's the exact message you are getting when you trying to telnet to 443?

---

### Post by Lido on 2013-06-08
Yeah, those two threads are/are similar to the ones I looked at before posting. Don't *think* that's the problem here. SSL does seem to work ok. Browsers would complain if the address was [https://something](https://something) and the server gave back unencrypted data right? Here's the telnet session:
```
$ telnet 45.#.#.# 443
Trying 45.#.#.#...
Connected to mydomain.com.
Escape character is '^]'.
GET /


<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>400 Bad Request</title>
</head><body>
<h1>Bad Request</h1>
<p>Your browser sent a request that this server could not understand.<br />
Reason: You're speaking plain HTTP to an SSL-enabled server port.<br />
Instead use the HTTPS scheme to access this URL, please.<br />
<blockquote>Hint: <a href="https://mydomain.com/"><b>https://mydomain.com/</b></a></blockquote></p>
<hr>
<address>Apache/2.2.22 (Ubuntu) Server at mydomain.com Port 443</address>
</body></html>
Connection closed by foreign host.
$
```

FWIW, a couple of ip lookup/whois type sites say that the last two ip addresses that show up in the error and other_vhosts logs belong to googlebot.

---

### Post by CharlesA on 2013-06-08
It should be configured correctly...

I tested it on my local machine and it threw back the exact same message:

```
telnet 192.168.1.2 443
Trying 192.168.1.2...
Connected to 192.168.1.2.
Escape character is '^]'.
GET /phpvirtualbox
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>400 Bad Request</title>
</head><body>
<h1>Bad Request</h1>
<p>Your browser sent a request that this server could not understand.<br />
Reason: You're speaking plain HTTP to an SSL-enabled server port.<br />
Instead use the HTTPS scheme to access this URL, please.<br />
<blockquote>Hint: <a href="https://Thor/"><b>https://Thor/</b></a></blockquote></p>
<hr>
<address>Apache/2.2.22 (Ubuntu) Server at Thor Port 443</address>
</body></html>
Connection closed by foreign host.

```

---


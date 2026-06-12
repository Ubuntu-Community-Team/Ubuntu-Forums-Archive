---
title: "What to do about attempts to get at /var/www/myadmin"
date: 2014-01-28
forum: Security
---

### Post by dkardell on 2014-01-28
I've noticed that I am recently getting more and more of the following in my error log.  Should I ban those ip's with iptables?  Thoughts?


```
[Sun Jan 26 07:48:58 2014] [error] [client 59.127.182.55] File does not exist: /var/www/myadmin
[Sun Jan 26 08:20:41 2014] [error] [client 95.123.36.249] File does not exist: /var/www/myadmin
[Sun Jan 26 12:13:59 2014] [error] [client 81.198.38.231] File does not exist: /var/www/myadmin
[Sun Jan 26 19:11:20 2014] [error] [client 69.70.242.242] File does not exist: /var/www/myadmin
[Sun Jan 26 21:16:16 2014] [error] [client 186.1.11.34] File does not exist: /var/www/myadmin
[Mon Jan 27 00:13:26 2014] [error] [client 94.102.53.231] File does not exist: /usr/share/phpmyadmin/scripts
[Mon Jan 27 00:13:26 2014] [error] [client 94.102.53.231] File does not exist: /var/www/myadmin
[Mon Jan 27 02:06:03 2014] [error] [client 116.193.73.62] File does not exist: /var/www/myadmin
[Mon Jan 27 02:16:29 2014] [error] [client 174.136.43.233] File does not exist: /var/www/myadmin
[Mon Jan 27 03:01:20 2014] [error] [client 120.127.10.41] File does not exist: /var/www/myadmin
[Mon Jan 27 03:39:38 2014] [error] [client 119.59.122.164] File does not exist: /var/www/myadmin
[Mon Jan 27 09:47:49 2014] [error] [client 203.158.221.74] File does not exist: /var/www/myadmin
[Mon Jan 27 10:10:49 2014] [error] [client 122.118.9.229] File does not exist: /var/www/myadmin
[Mon Jan 27 12:10:57 2014] [error] [client 200.87.98.139] File does not exist: /var/www/myadmin
[Mon Jan 27 12:57:14 2014] [error] [client 186.90.31.67] File does not exist: /var/www/myadmin
[Mon Jan 27 18:01:23 2014] [error] [client 218.241.167.179] File does not exist: /usr/share/phpmyadmin/scripts
[Tue Jan 28 02:25:58 2014] [error] [client 118.166.245.84] File does not exist: /var/www/myadmin
[Tue Jan 28 02:34:41 2014] [error] [client 101.77.117.3] File does not exist: /var/www/myadmin
[Tue Jan 28 06:56:02 2014] [error] [client 175.180.101.66] File does not exist: /var/www/myadmin
```

---

### Post by TheFu on 2014-01-28
This is common for every web server. Remote scripts hit all of us all the time looking for vulnerable services to access - anything written in PHP seems to be the primary target, so either not installing those things, using rules to only allow access from know, good, networks or redirecting the requests to somewhere else are really all you can do.

I use a reverse proxy that looks for anything like .*php in the request and drops those into a much slower server pool or just rejects them with a 403 - can't recall exactly what now.  Yep 403.  Here is a typical line:
```
 [19/Jan/2014:13:13:05 -0500] "GET /myadmin/scripts/setup.php HTTP/1.1" 403 134 "-" "ZmEu"
```

Looks like someone put out a new script, ZmEu, that looks for "setup.php" in web directories for commonly used tools.
I'll be blocking that user-agent shortly. Done.

Abuse is abuse and shouldn't be tolerated.

---

### Post by Habitual on 2014-01-28
> **dkardell said:**
> I've noticed that I am recently getting more and more of the following in my error log.  Should I ban those ip's with iptables?  Thoughts?
I did using
```
iptables -I INPUT -p tcp --dport 80 -m string --algo bm --string "ZmEu" --to 1000 -j DROP
```

---


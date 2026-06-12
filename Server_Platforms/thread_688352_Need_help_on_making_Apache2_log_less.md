---
title: "Need help on making Apache2 log less"
date: 2008-02-05
forum: Server Platforms
---

### Post by inf0c0m on 2008-02-05
Myself and a co-worker developed a rudimentary chat system that we use at work, and long story short, it logs way too much. My /var/log/apache2 folder is over 1.7 gb in size, and the mysql one is ~700mb in size (which I can fix). What options do I have for reducing the logging amount (or at least disable it for access to a specific directory). Here is a sample

```

172.20.117.215 - - [03/Feb/2008:07:36:33 -0600] "POST /chatv2/chatfetch.php HTTP/1.1" 200 62 "http://XXX/chatv2/chatv2.swf" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322; .NET CLR 2.0.50727)"
172.20.117.5 - - [03/Feb/2008:07:36:33 -0600] "POST /chatv2/chatp2list.php HTTP/1.1" 200 184 "http://XXXchatv2/chatv2.swf" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322; .NET CLR 2.0.50727)"
172.20.117.47 - - [03/Feb/2008:07:36:33 -0600] "POST /chatv2/chatuserlist.php HTTP/1.1" 200 248 "http://XXX/chatv2/chatv2.swf" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322; .NET CLR 2.0.50727)"
172.27.90.170 - - [03/Feb/2008:07:36:33 -0600] "POST /chatv2/chatfetch.php HTTP/1.1" 200 62 "http://XXX/chatv2/chatv2.swf" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322; .NET CLR 2.0.50727)"
172.20.117.33 - - [03/Feb/2008:07:36:33 -0600] "POST /chatv2/chatfetch.php HTTP/1.1" 200 62 "http://XXX/chatv2/chatv2.swf" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322; .NET CLR 2.0.50727)"
172.27.90.170 - - [03/Feb/2008:07:36:34 -0600] "POST /chatv2/chatuserlist.php HTTP/1.1" 200 248 "http://XXX/chatv2/chatv2.swf" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322; .NET CLR 2.0.50727)"
172.20.117.47 - - [03/Feb/2008:07:36:34 -0600] "POST /chatv2/chatfetch.php HTTP/1.1" 200 62 "http://XXX/chatv2/chatv2.swf" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322; .NET CLR 2.0.50727)"
172.20.117.42 - - [03/Feb/2008:07:36:34 -0600] "POST /chatv2/chatfetch.php HTTP/1.1" 200 62 "http://XXX/chatv2/chatv2.swf" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322; .NET CLR 2.0.50727)"
172.20.117.5 - - [03/Feb/2008:07:36:35 -0600] "POST /chatv2/chatfetch.php HTTP/1.1" 200 62 "http://XXX/chatv2/chatv2.swf" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322; .NET CLR 2.0.50727)"
172.20.117.186 - - [03/Feb/2008:07:36:35 -0600] "POST /chatv2/chatfetch.php HTTP/1.1" 200 62 "http://XXX/chatv2/chatv2.swf" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322; .NET CLR 2.0.50727)"
172.20.117.197 - - [03/Feb/2008:07:36:35 -0600] "POST /chatv2/chatfetch.php HTTP/1.1" 200 62 "http://XXX/chatv2/chatv2.swf" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322; .NET CLR 2.0.50727)"
172.20.117.42 - - [03/Feb/2008:07:36:35 -0600] "POST /chatv2/chatp2list.php HTTP/1.1" 200 184 "http://XXX/chatv2/chatv2.swf" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322; .NET CLR 2.0.50727)"
172.20.117.85 - - [03/Feb/2008:07:36:36 -0600] "POST /chatv2/chatfetch.php HTTP/1.1" 200 62 "http://XXX/chatv2/chatv2.swf" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322; .NET CLR 2.0.50727)"

```

Any thoughts?

---

### Post by jakommo on 2008-02-05
search for loglevel in you apache2 config.
```
cd /etc/apache2 (not sure if this is the same directory on ubuntu, could only check on my gentoo box ATM)
grep -ri loglevel *
```

and set it to something like error or whatever you like.

or you could configure logrotate for your apache log, that saves alot of diskspace.

---

### Post by MJN on 2008-02-06
See [this thread](http://ubuntuforums.org/showthread.php?t=678374) from last week.
 
Mathew

---


---
title: "Blocking (header) string from apache2 log - iptables or fail2ba"
date: 2013-09-29
forum: Server Platforms
---

### Post by nupex on 2013-09-29
Hello. It exist way to block access to the www server with use some string logged into apache2 log?

Example from apache2 access log:

218.XX.XX.5 * - - [29/Sep/2013:18:02:03 +0200] "HEAD / HTTP/1.1" 200 0 "[http://www.hysper.com/monitor-test](http://www.hysper.com/monitor-test)" "Mozilla/4.0 (compatible; MSIE 6.0; [www.hysper.com]("http://www.hysper.com") bla bla)"

* IP address changing, string HEAD / HTTP/1.1" 200 0 "[http://www.hy]("http://www.hysper.com/monitor-test").. stay allways the same..

I would like to make rule to block all packet contains referer **hysper.com**.

Count of GET/POST/HEAD is not so intensive to process this by DOS filter..

Thank you.

---

### Post by Doug S on 2013-09-29
Hi and welcome to ubuntu forums.

There is a string module for iptables, but it uses extra resources. Myself, I try not to use it.

Just recently, I did manage [to restrict access based on referrer]("http://ubuntuforums.org/showthread.php?t=2174433") using .htaccess and mod-rewrite.

---

### Post by nupex on 2013-09-30
Mine .htaccess is not working :confused:

> RewriteEngine On 
SetEnvIfNoCase User-Agent "^Hysper" dos_http

Order Allow,Deny
Allow from All
Deny from env=dos_http

> SetEnvIfNoCase Referer "^http://.*(poker|hysper|pingdom|uptime|cash|video|liftmaster|fillbest|pharma|.info/)" spam_ref=1

Order Allow,Deny
Allow from all
Deny from env=spam_ref

Before it look like

> RewriteEngine On
RewriteCond %{HTTP_USER_AGENT} ^Hysper
RewriteRule ^.* - [F,L]


No work..

---

### Post by nupex on 2013-09-30
Thx for your time The solutions for me is bad_bots contains filter directly at gateway unit (at network where the server is).. that means bad packet can´t  touch the server now..

.htaccess was working (blind man not seen code 500 in the apache log). But it writes a alot of lines to the logs (need another no log configuration).. so gateway unit filter is better solution. Thx again.

---


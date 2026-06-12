---
title: "Connection to localhost refused..Apache2 error messages"
date: 2005-11-22
forum: Server Platforms
---

### Post by exkalibur on 2005-11-22
I don't know what I did.....Was trying to resolve connectivity issues with the WAN side (incoming to server) and now I lost Apache.........
1- Can't connect to localhost anymore....connection refused
2- ps aux  shows that Apache2 isn't running.
3- this is what I get when trying to start it...
"apache2 -k start
(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs"

Running Ubuntu
webmin (I played in there;could be what caused it)
AAaaarrrgggg !!!!!


Edit : I tried the other command and this is what I got.....

merlin@server:~$ sudo /etc/init.d/apache2 start
Password:
 * Starting web server (Apache2)... (98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

What next ????

---

### Post by cactus on 2005-11-22
try:
apachectl -t
see if there are any errors in your config file..

---

### Post by grendelkhan on 2005-11-23
Do a netstat -a|grep 80 - it sounds like there is something running on that port that's stopping apache from starting up.

---

### Post by herrpoon on 2005-11-23
What does "ps ax | grep apache" say?

---

### Post by exkalibur on 2005-11-23
I'm at work right now so I'll try these when I get back home....in about 6 hrs.

Thanks

---

### Post by exkalibur on 2005-11-23
OK. Here are some results : 

Command : apache2ctl -t
Result : Syntax OK

Command : netstat -a|grep 80
Result : unix  2      [ ACC ]     STREAM     LISTENING     10180   /tmp/orbit-merlin/lin c-1bad-0-5db0a8329865f
unix  3      [ ]         STREAM     CONNECTED     10480
unix  3      [ ]         STREAM     CONNECTED     9980

Command : ps ax | grep apache2
Result :  7320 pts/0    S+     0:00 grep apache2

I'll figure out how to post in a text box and I'll post more results

Regards

---

### Post by exkalibur on 2005-11-23
Mmmmmhhhhh ! Permission on VAR is set to root and the WWW is also set to root. The HTML files in the WWW directory used to be set to me as owner. Now it say it can't determine.
Boy ! I really messed things up !!!!

---

### Post by exkalibur on 2005-11-23
I think I got it......The ports.conf file had * listen :80. I rem it out and fixed permissions on the www directory (root=owner, other read and execute )

Was that the right thing to do ??
I can now open localhost in browser.
Regards

---


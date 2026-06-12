---
title: "Apache Weirdness (or just possibly operator)"
date: 2009-10-05
forum: Server Platforms
---

### Post by bezoar on 2009-10-05
Just the facts.

Ubuntu 9.04

1. On my local home network I have a panasonic web camera with its own web server. Runs on port 80. [www.seemyport](www.seemyport) sees port 80 open when this is up. So my ISP does allow port 80.

2. Apache installed on ubuntu box. [http://localhost](http://localhost) and lan ip address (192.168.1.230) on another computer within my home lan shows "It Works!" Apache IP is outside my dhcp range. I.E. static.

3. Linksys wrt54gl - port forwarding for port 80 for ip 192.168.1.230 enabled. AND the camera 192.168.1.253 is disabled. 

4. [www.seemyport.com](www.seemyport.com) will not see port 80 if I have the camera off. Only when it is on. (Even with port forwarding disabled for ip 253). Router has been powered on/off any number of times as well. Settings are as stated
 
5. [www.no-ip.com](www.no-ip.com) keeping my ip straight with my url external to my lan. 

lsof -i :80
COMMAND  PID     USER   FD   TYPE  DEVICE SIZE NODE NAME
apache2 7606     root    3u  IPv4 1971155       TCP *:www (LISTEN)
apache2 7610 www-data    3u  IPv4 1971155       TCP *:www (LISTEN)
apache2 7612 www-data    3u  IPv4 1971155       TCP *:www (LISTEN)

ports.conf
Listen 80

httpd.conf
0 bytes

ps -ef | grep http 
returns nothing

ps -ef | grep apache
root      7606     1  0 18:31 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  7608  7606  0 18:31 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  7610  7606  0 18:31 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  7612  7606  0 18:31 ?        00:00:00 /usr/sbin/apache2 -k start
root      8102  6745  0 18:54 pts/0    00:00:00 grep apache

apache2ctl -v
Server version: Apache/2.2.11 (Ubuntu)
Server built:   Aug 18 2009 14:28:29

External to my network my my [www.domain.com](www.domain.com) "page cannot be displayed".

Did I forget anything? Or should I ask, what did I forget?

Thank you.

---

### Post by bezoar on 2009-10-06
Did I make a forum faux pas? After 24 hours no one has anything to say or direction to point me?

Any assistance would be greatly appreciated.

---

### Post by cariboo on 2009-10-07
If you are seeing the port open when running the web cam, but not apache, it sounds like a misconfigured router, eg port 80 is not being forwarded from 192.168.1.230.

---

### Post by bezoar on 2009-10-08
I know it looks like that port 80 is not being forwarded, but as I said, I have power cycled the router and the attached picture is what I show. 

If I am having router issues (would surprise me), I would like to know. If I am having a failure in logic, I would like to know that as well. 

[IMG]http://www.butterflyfx.com/Junk/port80.jpg[/IMG]

Thanks for any assistance.

My list of "facts" still stands as true. They reflect what I have, what I have done and what I have seen.

---

### Post by wojox on 2009-10-08
Set Apache 80 to a different port. You only have one external ip. So you can only have one port 80 being forwarded.Try changing it to port 85 or something and restart apache.

---

### Post by bezoar on 2009-10-09
wojox,

Thank you so much for your reply.

I made a change to ports.conf. Port 80 to 85

I do not know why I should have to do this if I have turned off the device that uses port 80. But this DOES work. I just want to understand why. I still do not understand why this is necessary if I turn off the other device that uses port 80.

What is the difference between the listen directives in httpd.conf and ports.conf?

When I make the change, Apache tells me that my page cannot be found. If I leave it at port 80, I get the "It Works" message.

I am really only just starting with Apache (no surprise there).

Google is our friend. I find things on how to change the port, most reference httpd.conf. And all say "...then just restart Apache". I don't think there is any "just" to it.

Also another confusion, "ps -ef | grep httpd" returns nothing. All of my instances are "Apache2". 

Apache 2.2.11 is what I show loaded. 

Thanks to all my responders (both of you :) )

---

### Post by wojox on 2009-10-09
Yes it is weird bezoar if the device was of why it would do that. The only thing I could think of was because the web camera was listed before Apache. I have the same router and run apache on my server machine so I've been down this road before. I know it gets frustrating at times.  :P

---

### Post by bezoar on 2009-10-11
I appreciate the reply. I do have port 85 open. Says seemyport.com, still having issues getting to my system from the outside and, now, from the inside. If I change Listen 85 to 80, localhost works "It Works", if I add :85 - Apache says he can't find the file. 

Still can't get to it from the outside. "...cannot display the webpage".

I really want my router to act rationally. If I turn off a port, the port should be off. If I forward a port, it should be forwarded. 

Again, thanks for your response. 

I am making progress, it's just that I know this is SO simple, and I am having all these issues. Sigh.

Later,

---


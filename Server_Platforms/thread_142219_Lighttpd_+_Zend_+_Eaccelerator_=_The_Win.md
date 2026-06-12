---
title: "Lighttpd + Zend + Eaccelerator = The Win"
date: 2006-03-10
forum: Server Platforms
---

### Post by dermotti on 2006-03-10
After trying multiple webservers, I have finally  decided on Lighttpd. Its very fast  and easy to administier.

Now this weekend i discovered Zend optimizer and Eaccelerator. Zend made my php just a hair faster, but Eaccelerator is FAST AS HELL. My pages come up like 30% faster and produce less load on my system.

Lighttpd + Zend + Eaccelerator = The Win

I have some generic benchmarks on my site [http://www.xorg.us](http://www.xorg.us) if you wanna see.

Also if anyone has some REAL website benchamrking software they can reccomend that would be great.

---

### Post by dermotti on 2006-03-10
Currently the site is running the Lighttpd + Zend + Eaccelerator combo, so feel free to beat on my server, attack it, whatever. Let me know what you think!

---

### Post by dk_pa on 2006-03-10
Looks interesting, any more details on pros/cons over apache or anything like that.  I, honestly, just took a quick glance.

---

### Post by dermotti on 2006-03-10
VS apache, feature wise, I don't think it has as many features, just the most important ones. Meant to run lean, use less resources, run faster. It does a much better job at load balancing system resources then vanilla apache in my opinion. When i hammer my server cpu usage rarely goes over 35% and the webpages consistantly load the the same exact speed. When i hammer Apache the same way the cpu usage goes up to around 65% and page loading isnt consistant at all, some times the page loads take .2 seconds and other times up to 2 seconds.

Granted im a newb when it comes to webserver software. Im sure you can tweak Apache  to run pretty lean. Just out of the box, lighttpd seems much faster.

---

### Post by dermotti on 2006-03-10
[http://litespeedtech.com/benchmark.html](http://litespeedtech.com/benchmark.html)

Some interesting benchmarks, shows Lighttpd kickin some arse again.

[http://paul.querna.org/journal/articles/2005/06/24/debunking-lighttpd?postid=82](http://paul.querna.org/journal/articles/2005/06/24/debunking-lighttpd?postid=82)

Shows an Apache developer with a super tweaked apache going as fast as lighttpd...

---

### Post by dieffel on 2006-03-20
Do you have any how-to to installing & administrating these apps in Dapper?

---

### Post by dermotti on 2006-04-21
Yes, [http://www.xorg.us](http://www.xorg.us)

---


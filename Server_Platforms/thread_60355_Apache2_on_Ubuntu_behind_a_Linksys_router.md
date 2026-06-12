---
title: "Apache2 on Ubuntu behind a Linksys router"
date: 2005-08-27
forum: Server Platforms
---

### Post by theQmaster on 2005-08-27
Alright, I will try to be short

I'm trying to move a current Windows based Apache+Tomcat to a new Linux(Ubuntu 5.04) box within same sub-net.

Internet->Router->Windows Box (192.162.1.100)
                          ->Linux Box(192.162.1.200)


Currently I have Apache 2.0.53+Tomcat 5.5.7 running great on Windows XP behing a router. In the router I have configured to have all incoming requests on 80 to be served by the Windows Box. (192.168.1.100)

I configured Linux box ( 192.168.1.200) the way I wanted and that works perfectly. I can see my mirrored application on the Linux server. Configuration on this one is Apache2.0.53+Tomcat.5.5.9. So from within the network works great.


1st Problem
When I flip the IP address from *.100 to *.200 the outside-of-my-network requests are still going to Windows Box - that is very strange or I'm missing somethig here. Then, if I do shutdown the windows box the requests seems to be server by the Linux and that is 2nd Problem

2nd Problem
Those requests mentionned above are not served by the Linux machine.  I only have on domain and I keep my default virtual host.

Looked in the router log the request are getting to the router but the access.log is not showing them. 

My conclusions are that either the router doesnt' forward the requests to the Linux box ( it does when I have the Windows though) or the Apache is not configured right to handle the outside-of-my-network requests(that is bizzare since localhost works fine)

Can UPnP(enabled) mess the things up ? I have a Linksys WRT54GS router that worked fine in tandem with the Windows Box.


Any idea, flaws you can thing about it ?
Q

---

### Post by theQmaster on 2005-08-27
It was  the UPnP - once I've disabled it started to work like a charm.

Hope this will be usefull for others...

Q
[http://www.goodstockimages.com](http://www.goodstockimages.com)

---

### Post by marvlus on 2005-08-29
Is this website running on apache2 webserver under the Ubuntu Linux OS?

---


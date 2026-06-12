---
title: "Setting Up Two Ubuntu LAMP Servers With Only One External IP Address"
date: 2010-12-10
forum: Server Platforms
---

### Post by garryconn on 2010-12-10
I have two LAMP servers running 10.04 32bit Server and only one external IP address. I would like to be able to host multiple websites using each server. I don't want to have to use the :8080 in the address bar for the sites that are hosted on the second server. I have searched most of the day for writeups or tutorials on how to set this up and can't find anything specific. From what I have researched, it seems I'll have to setup a reverse proxy with Apache on the main server. Would someone mind offering some advice on this. I don't quite know how to set this up. 

Here's my setup.

[CENTER]
WAN IP = 71.87.xx.xx
.
.
AIRPORT EXTREME
192.168.0.1
.                               .
.                               .
.                               .
.                               .
SERVER1                 SERVER2
192.168.0.10      192.168.0.100
.                               .
.                               .
- [www.domain1.tld](www.domain1.tld)                  - [www.domain2.tld](www.domain2.tld)
- [www.domain3.tld](www.domain3.tld)                  - [www.domain4.tld](www.domain4.tld)
- [www.domain5.tld](www.domain5.tld)                 - [www.domain6.tld](www.domain6.tld)[/CENTER]

---

### Post by TheGadgetCat on 2011-01-01
Far from impossible.
You need to make sure that each connection uses a different port.
You then need to bind a host name to each IP and it's port.
Im not sure where this would be done, but that's the theory to it. Someone can correct me if I am wrong.

---

### Post by SeijiSensei on 2011-01-01
> **garryconn said:**
> From what I have researched, it seems I'll have to setup a reverse proxy with Apache on the main server. Would someone mind offering some advice on this. I don't quite know how to set this up.

Forward all the HTTP traffic to the main server.  In Apache create <VirtualHost> containers for each site, including those hosted on the second server.  In the containers for these sites, you would use a reverse proxy as explained [here](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html).

---

### Post by perspectoff on 2011-01-01
Sure. Here's the instructions:

On Ubuntuguide:
[http://ubuntuguide.org/wiki/Apache2_reverse_proxies](http://ubuntuguide.org/wiki/Apache2_reverse_proxies)

On Kubuntuguide:
[http://kubuntuguide.org/Apache2_reverse_proxies](http://kubuntuguide.org/Apache2_reverse_proxies)

---

### Post by R.Bucky on 2011-01-01
I had the same conundrum last month when I started hosting my Ubuntu Lucid Mirror. One of my boxes was used to host my domains, while the other was my mirror. I was unable to properly configure Apache reverse proxy or Pound Proxy with my  hardware configuration. The problem seemed to be that I needed a box or embedded device in front of my two servers that would route traffic appropriately. Someone set me straight if I am incorrect on that one. 

In the end, I paid another $5/month for 4 additional static IP's from Comcast and simply used 1-to-1 NAT on the router.

---

### Post by perspectoff on 2011-01-01
> **R.Bucky said:**
> I had the same conundrum last month when I started hosting my Ubuntu Lucid Mirror. One of my boxes was used to host my domains, while the other was my mirror. I was unable to properly configure Apache reverse proxy or Pound Proxy with my  hardware configuration. The problem seemed to be that I needed a box or embedded device in front of my two servers that would route traffic appropriately. Someone set me straight if I am incorrect on that one. 

In the end, I paid another $5/month for 4 additional static IP's from Comcast and simply used 1-to-1 NAT on the router.

I'm sorry you didn't see my instructions last month. You don't need 5 IP addresses and you don't need another box to be a proxy.

You merely have to enable one of your servers to forward the traffic to the other server (using the reverse proxy method). It works for me on all versions of Ubuntu and Kubuntu in which I have installed Apache2 (alone or as part of a LAMP server).

---

### Post by R.Bucky on 2011-01-01
I tried Apache rev_proxy and it did not seem to work for me. Also, I was not too hip on passing all of my Lucid Mirror requests through my primary HTTP server for routing. In the end, this is a better configuration for me and allows for more efficient scaling.

---

### Post by perspectoff on 2011-01-01
No problem. Not everyone runs a high volume software mirror, though. Heck, I know people who buy an extra Internet connection or even set up datacenters with many virtual machines in order to host lots and lots of servers, too. There are lots of ways to skin a cat, from very expensive to very inexpensive.

---

### Post by garryconn on 2011-01-07
Everyone, I wanted to thank you for all your support. In combination with the responses received here on this thread with this [article]("http://www.classhelper.org/articles/reverse-proxy-server-squid-debian/reverse-proxy-introduction.shtml") written by Philip C. Paradis, I was finally able to setup the network exactly how I wanted. If anyone else wants to do the same, be sure to check out Phillip's article here: [http://www.classhelper.org/articles/reverse-proxy-server-squid-debian/reverse-proxy-introduction.shtml]("http://www.classhelper.org/articles/reverse-proxy-server-squid-debian/reverse-proxy-introduction.shtml")

Thanks again to everyone who replied. Moments like this remind me why I am continually motivated to use and learn more about Linux. :)

---


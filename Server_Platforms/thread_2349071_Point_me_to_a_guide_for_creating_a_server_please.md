---
title: "Point me to a guide for creating a server please"
date: 2017-01-10
forum: Server Platforms
---

### Post by barons on 2017-01-10
Hello,

I'm new to all this and i'm overwhelmed here on the forums. I wanted to make a server and i found this guide but it seems to be really old.

[http://www.instructables.com/id/Turn-an-old-Computer-into-a-web-server/step3/Install-the-Operating-System/](http://www.instructables.com/id/Turn-an-old-Computer-into-a-web-server/step3/Install-the-Operating-System/)

I'm running into an issue when i get to the network auto configuration part of the installation. The message appears after it tries to configure the network with DHCP. 

```
Network autoconfiguration failed Your network is probably not using the DHCP protocol. Alternatively, the DHCP server may be slow or some network hardware is not working properly.

```

I would appreciate it if someone could point me to a beginner friendly guide that might help me get around this. I'm not sure if I need DHCP or if I can just do a manual configuration? I've tried it but wasn't sure which IP address it wanted me to use. 

Thanks!

---

### Post by barons on 2017-01-10
I've seen posts where other users run into this same issue but none have said how/if it was fixed. I guess i'll try Amahi or FreeNas to see if those are easier to use.

---

### Post by lisati on 2017-01-10
An "official" guide to Ubuntu Server edition can be found [here]("https://help.ubuntu.com/lts/serverguide/"). Another guide can be found [here]("https://www.ubuntu.com/download/server/install-ubuntu-server").

---

### Post by bearlake on 2017-01-11
With the above links you should be under way.

I can give you a few links but you really need to know what its all about or when the first thing goes wrong your done.

These links help me off the start and with the help of a few people on here I came a long way.

Also added a link from one of the the very good folks on here. Credit goes to TheFu for this [link]("http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server").

---------------------------

How to Secure Ubuntu Server 16.04 Utube Viedo.

[https://www.youtube.com/watch?v=2991xIqmK3A](https://www.youtube.com/watch?v=2991xIqmK3A)


Setup Guide and great info

[https://www.thefanclub.co.za/how-to/how-secure-ubuntu-1604-lts-server-part-1-basics](https://www.thefanclub.co.za/how-to/how-secure-ubuntu-1604-lts-server-part-1-basics)


OpenVPN install and setup for Sever and Client.

[https://www.youtube.com/watch?v=2991xIqmK3A](https://www.youtube.com/watch?v=2991xIqmK3A)


How do I set up SSH authentication keys

[http://askubuntu.com/questions/61557/how-do-i-set-up-ssh-authentication-keys](http://askubuntu.com/questions/61557/how-do-i-set-up-ssh-authentication-keys)


These are just a few I read and watch over time.

---

### Post by HermanAB on 2017-01-11
Alternatively, just install Xubuntu.  Done.

---

### Post by barons on 2017-01-11
Thanks for all the help guys!

I installed Xubuntu and I love it! I also managed to get all the server stuff installed and my site now shows up on localhost. However i'm running into some trouble getting it to actually show up online. Could someone point me to the best place to ask for help in getting it working?

I've got port 80 open on the server and in the router. I've also set the server to have a static ip address. Then I pointed my domain to my external ip/routers ip. However when I try to navigate to my ip address or the domain name I get a site can't be reached time out error. 

I'm sure there is a step i've missed somewhere and I would appreciate an help i could get to figure out where i went wrong.

---

### Post by slickymaster on 2017-01-11
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2017-01-11
> **barons said:**
> I've got port 80 open on the server and in the router. I've also set the server to have a static ip address. Then I pointed my domain to my external ip/routers ip. However when I try to navigate to my ip address or the domain name I get a site can't be reached time out error. 
You need to use port-forwarding to connect the external port 80 on the router to port 80 on the server.  How to do this varies from router to router, so you'll need to consult the documentation for yours.

If you have already configured port-forwarding, and it still doesn't work, chances are that your ISP has blocked inbound port 80 connections.  This is a common policy on residential connections to force people to use business-class connections for web and email hosting.

---

### Post by darkod on 2017-01-11
Just to add to what Sensei wrote, and since you have Xubuntu running as a server which has a GUI... After you configure the port forwarding on the router, to check if port 80 is working correctly you can visit [www.canyouseeme.org](www.canyouseeme.org) and test for port 80. That should tell you if it is blocked by the ISP.

---

### Post by geeksmith on 2017-01-11
If your ISP is like mine, your router doesn't receive a public routed IP address, but an internal IP address that goes through one or more NAT gateways before hitting the public Internet. They do this because they don't have enough public IPs to give one to each customer.

If this is the case, you must request a public IP assignment from your ISP. To check it, install traceroute and run a command like "traceroute 8.8.8.8". It will look something like this (I sanitized a couple of lines for privacy):
[FONT=Courier New]traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  192.168.9.1 (192.168.9.1)  17.861 ms  18.007 ms  18.131 ms
 2  10.22.10.1 (10.22.10.1)  93.536 ms  93.660 ms  93.354 ms
 3  10.20.10.1 (10.20.10.1)  98.455 ms  98.598 ms  103.814 ms
 4  10.30.170.1 (10.30.170.1)  103.897 ms  104.054 ms  104.201 ms
 5  10.10.10.254 (10.10.10.254)  108.527 ms  106.489 ms  106.729 ms
 6  xxx.mpr1.sea1.us.above.net (xxx.xxx.109.169)  117.287 ms  90.707 ms  84.552 ms
 7  72.14.208.172 (72.14.208.172)  84.675 ms  94.936 ms  95.073 ms
 8  108.170.245.97 (108.170.245.97)  94.786 ms 108.170.245.113 (108.170.245.113)  99.943 ms  99.824 ms
 9  209.85.250.17 (209.85.250.17)  100.076 ms 209.85.250.101 (209.85.250.101)  105.514 ms 209.85.250.59 (209.85.250.59)  105.783 ms
10  google-public-dns-a.google.com (8.8.8.8)  105.652 ms  110.419 ms  110.550 ms[/FONT]

Line 1 is my local router's LAN interface, line 2 is the upstream router. Note that both are assigned unrouted IP addresses designated for use in NAT networks (see [https://en.wikipedia.org/wiki/Private_network]("https://en.wikipedia.org/wiki/Private_network")).

If line 2 of your output is a NAT address, then you're most likely going to need help from the ISP. This usually means paying an extra fee for a public IP address.

---


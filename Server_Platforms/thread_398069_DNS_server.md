---
title: "DNS server?"
date: 2007-03-31
forum: Server Platforms
---

### Post by asdf29 on 2007-03-31
Hi,

I have installed something in the last couple days on my experimental server.  There isn't very much on it, but something I have installed has started to mess with my home network.  Once the server is on for about 30 mins (sometimes less), other computers on the network can't access the internet properly.  You can happily ping anything you have an ip address for, but you can't reach anything with a domain name (i.e. ping google.com).  As soon as I unplug the server, the problem goes away.

I have no idea what I could've installed that does that...

Anyone got any ideas?

/asdf29

---

### Post by victorbrca on 2007-03-31
Not sure if this would be the case, but I had a similar problem wen I installed my Ubuntu Server the first time... 

I resolved it by using an external DNS on my resolv.conf instead of my gw.

I had to play around with it for a while till I got it working...

> webm@pluto:/etc$ cat resolv.conf 
# search resolver1.opendns.com
# nameserver 192.168.1.1
nameserver 208.67.222.222


The address I'm using is from OpenDNS.com


Vic.

---

### Post by Mr. C. on 2007-03-31
It is possible that IPv6 is disturbing your router's DNS cache.  Disable IPv6:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

The previous poster's advice may also be effective.

MrC

---

### Post by asdf29 on 2007-04-01
I actually ended up changing the DNS on my router and it all seems to work brilliantly now.

Many thanks.

/asdf29

---


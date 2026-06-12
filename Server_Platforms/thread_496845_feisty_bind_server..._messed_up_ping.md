---
title: "feisty bind server... messed up ping"
date: 2007-07-09
forum: Server Platforms
---

### Post by inphektion on 2007-07-09
I have a feisty bind server whose IP is 10.20.1.10.  I have it on a different vlan than our main network which is 10.5.20.x
If I have this box ping itself by name, or IP etc everything comes back in .00x seconds as you can see here:
PING asterisk.voip.mydomain.com (127.0.1.1) 56(84) bytes of data.
64 bytes from asterisk.voip.mydomain.com (127.0.1.1): icmp_seq=1 ttl=64 time=0.022 ms
64 bytes from asterisk.voip.mydomain.com (127.0.1.1): icmp_seq=2 ttl=64 time=0.008 ms
64 bytes from asterisk.voip.mydomain.com (127.0.1.1): icmp_seq=3 ttl=64 time=0.008 ms
64 bytes from asterisk.voip.mydomain.com (127.0.1.1): icmp_seq=4 ttl=64 time=0.007 ms

However when I try pinging something on my main network, although the ping times say .1xx which is really fast I waited about 5 seconds for each of those lines to print out as you can tell by the total time of 19999ms.

root@asterisk:/etc# ping rohan.mydomain.com
PING rohan.mydomain.com (10.5.20.8) 56(84) bytes of data.
64 bytes from 10.5.20.8: icmp_seq=1 ttl=127 time=0.163 ms
64 bytes from 10.5.20.8: icmp_seq=2 ttl=127 time=0.191 ms
64 bytes from 10.5.20.8: icmp_seq=3 ttl=127 time=0.178 ms

--- rohan.mydomain.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 19999ms
rtt min/avg/max/mdev = 0.163/0.177/0.191/0.015 ms

What could be going on here?
This is a bind server for the voip.mydomain.com network and a slave dns server for mydomain.com.
all the vlan config is done on the cisco switch and routers so the interface itself here doesn't have the vlan configured he just has normal static IP and the cisco switches handle vlan tagging etc.

Also I'd like to be able to just ping rohan without the .mydomain.com suffix but not sure how to make the dns search order since it is a bind server and not a dns client per se.

---

### Post by Mr. C. on 2007-07-09
You are confusing several concepts.

First, pinging the loopback interface serves very little purpose, except to see that the loopback interface is up (which it virtually always is).  Packets do not go onto the wire for this interface, ever.

Bind is not slowing down those pings - once the name is translated into an IP address, no further name lookups need occur for that ping.  Bind has nothing to do with packet flow - it is simply a name / IP lookup service.

This type of delay is likely a routing loop, duplicate IP address, or switch/router configuration problem.

To be able to address your hosts with non-fully qualified (i.e. simple) names, place your domain name in your /etc/resolv.conf file as:
```

domain mydomain.com
```

Then, usage of simple host names such as rohan will get translated into fully qualified names.  Note, this will not occur if rohan is listed in /etc/hosts as the first hostname (as opposed to aliases), and your nsswitch.conf file indicates that the hosts file should be used first.

There are two parts to DNS - a resolver and a server.  Your server is also a DNS client of some DNS server; its system libraries use /etc/resolv.conf and /etc/nsswitch.conf to determine name resolution.

MrC

---

### Post by inphektion on 2007-07-09
thanks.  I actually know what you said I just posted in a really confusing way.  
But yes I figured to use resolv.conf to put in search domain.com voip.domain.com etc but everytime I reboot it gets overwritten.  I thought maybe it was because of bind which is why I mentioned that.  I'm using a static IP, so why is resolve conf getting overwritten?  it says something about glibc resolver but besides making it a readonly file what is the real solution to that?
I do have a hosts file but just the master dns server that this server is a slave to I have in there, not rohan.

I'll hunt down the ping issue, does seem like it could be some sort of weird loop going on maybe something I did wrong in vlan config.

---

### Post by Mr. C. on 2007-07-09
The Network Manager needs to be configured with the appropriate domain if you use it to configure your network.  Bind has no part in configuring resolv.conf.

MrC

---

### Post by inphektion on 2007-07-09
damn... I hate when I don't understand someone when they are being helpful but what network manager??
This is feisty server so no gui is running.  I went through the dhclient script and named.conf.options but didn't notice anything...
I really can't tell who the hell is overwritting resolv.conf.  I mean makes sense if I was running dhcp ( I am running dhcp server) but not the client...

---

### Post by Mr. C. on 2007-07-09
Sorry, I didn't realize this was a server install.

How about the avahi-daemon -  is it running ?  Or pppd ?  Or nscd ? 

There are a number of things that want to manage /etc/resolv.conf for you.

MrC

---


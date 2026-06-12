---
title: "Dividing websites between different Internet connections"
date: 2011-04-12
forum: Server Platforms
---

### Post by Nessaja on 2011-04-12
Hi All,

I know Ubuntu can do amazing things, but I was wondering if it can use different Internet connections for different websites.

The Setup:
We have 1x unshaped ADSL connection  at 4MBPS (fastest available) that's used for office related things, Skype, General browsing etc.
We have another ADSL connection, this time shaped and running at 4MBPS, I want to send all requests to facebook, twitter and downloading sites like fileserve, filesonic, hotfile etc. to the shaped connection.

Can iptables be used to do this?

The unshaped ADSL router is connected to eth0 and has an IP of 192.168.0.1
the shaped ADSL router is connected to eth2 and has an IP of 10.0.2.1

Local lan is connected to eth1 and has a range of 192.168.1.0/24

Can iptables send a certain webpage (*.facebook.*) to eth2 and other pages (*.google.*) to eth0 ?

---

### Post by HermanAB on 2011-04-12
Howdy,

You need to use the route2 command.

Go to [http://www.tldp.org](http://www.tldp.org) and read the Advanced Routing Howto.

---

### Post by Nessaja on 2011-04-13
Hi,

thanks for the reply, I've read through the advanced routing guide, but this splits connections from different pcs on the network to different routers, this is more or less what I need, but instead of having certain computers use certain or random routers, I just want to send certain webpages through the shaped router.

Isn't there an iptables command for this? using -s facebook.com and maybe a combination of dnat or snat commands passed to iptables?

---

### Post by BkkBonanza on 2011-04-13
You should be able to add rules using the **route** command to force destination networks to use a particular gateway.

eg.

sudo route add -net x.x.x.x netmask 255.255.255.0 gw y.y.y.y 

Easy enough to test. Add a test rule and then use **netstat-nat -SN** to view the NAT table and see which way a test connect got routed.

I'm not sure how much of a burden that would put on the routing as you would presumably have a lot of matching going on for every packet.

You may be able to do it in iptables with the SNAT target forcing it to go out a certain IP but I'm not sure about that as according to the docs behaviour changed after kernel 2.6.10 to not support multiple SNAT rules.

---


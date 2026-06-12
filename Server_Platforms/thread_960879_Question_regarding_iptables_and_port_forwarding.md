---
title: "Question regarding iptables and port forwarding"
date: 2008-10-27
forum: Server Platforms
---

### Post by Aeros84 on 2008-10-27
I've set up my Ubuntu server as a router/gateway plus a transparent squid proxy. How it works:

- Network interface eth0 connected to the WAN (ADSL router).
- Network interface eth1 connected to the LAN.
- eth1's IP is 10.0.0.1.
- eth0's IP is 192.168.0.1.
- ADSL router's IP is 192.168.0.2.
- Squid listening on port 3128.
- LAN pc's gateway are set to the Ubuntu server's eth1 IP (10.0.0.1).
- The gateway/routing is set up via Shorewall and works just fine.

This all works fine, but I have a question:

When I set it up, I found a how-to on the net, telling me to use the following 2 iptable rules to make squid truly transparent:

```

iptables -t nat -A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 10.0.0.1:3128
iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 80 -j REDIRECT --to-port 3128

```

This way, the LAN users don't need to set the proxy in their browsers, but will still go through the proxy. This works fine at the moment, btw.

But:

Are both these rules really required? I'm a bit stumped here.. it makes sense to me that the first rule would forward all port 80 traffic inbound from eth1 to port 3128 on the Ubuntu server.

So what is the second rule for? To forward inbound port 80 traffic from eth0 to the squidproxy as well? Why? And why is it using REDIRECT instead of DNAT? I tried it with only the first rule (as in, I removed the second rule completely), and the LAN browsers still go through the proxy as they should - so once again, what's the second rule for? :P

SECOND QUESTION:

Also, I need to forward a particular port (81) from the outside to one of the LAN pc's (10.0.0.3 to be specific). On the ADSL router I set port 81 to forward to the Ubuntu server, and on the Ubuntu server I set the following iptable:

```

iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 81 -j DNAT --to-destination 10.0.0.3:81

```

This seems to work. But since I'm a stubborn perfectionist - is that enough? Will that rule suffice, or am I missing something that APPEARS obsolete but is in fact necessary?

---

### Post by jennifer.ayag on 2008-10-28
hello sir!

i'm new here in ubuntu, i noticed that you have configured your firewall correctly....can you please help with mine.

here's the details:

eth0 - proxy card (192.168.1.99)
eth1 - internet card (192.168.1.98)
PROXY PORT - 8000
broadband router - 192.168.1.1
client's gateway - 192.168.1.1

please advice if my rules are correct.....

i'm really having a hard time with this...

input chain rules

Accept 	If input interface is lo 		
Accept 	If input interface is eth0 		
Accept 	If state of connection is ESTABLISHED,RELATED 		
Accept 	If protocol is ICMP 		
Accept 	If protocol is TCP and source and destination ports are 80,22,465,995,110,25,8000,10000 		
Accept 	If protocol is TCP and source is pop3.mrm.net and input interface is eth1 and source port is 995 		
Accept 	If protocol is TCP and destination port is 443 		
Drop 	Always

forward chain rules - accept all
output chain rules - accept all

THANKS!!

---

### Post by jennifer.ayag on 2008-10-28
note: i'm using webmin in configuring my iptables

---

### Post by Aeros84 on 2008-10-28
Hi Jennifer,

I used this site:

[http://www.howtoforge.com/ubuntu6.10_firewall_gateway_p2](http://www.howtoforge.com/ubuntu6.10_firewall_gateway_p2)

I found it very helpful to set up the routing/gateway/firewall - it explains everything step-by-step :) It uses Shorewall as a front-end instead of the default Linux firewall in Webmin.

---

### Post by jennifer.ayag on 2008-11-02
thanks....

---


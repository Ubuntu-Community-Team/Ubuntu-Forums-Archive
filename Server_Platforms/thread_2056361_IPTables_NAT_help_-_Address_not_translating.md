---
title: "IPTables NAT help - Address not translating"
date: 2012-09-11
forum: Server Platforms
---

### Post by pieterlouw on 2012-09-11
Hi

I have a server that I want to use as a firewall/router (Ubuntu 11.10 Server) between the internet and LAN. I have 2 network interfaces, eth0 will be used as the interface to the internet and eth1 will be used as the interface to the LAN.

Basically I have everything setup already, however I have a problem with NAT from one interface (eth0 - 192.168.100.223) to the other (eth1 192.168.0.223). I tested it the other way around (from eth1 to eth0) and it works fine.

I've used the following script as starting point: [https://help.ubuntu.com/community/Router/Firewall](https://help.ubuntu.com/community/Router/Firewall)

So currently I'm testing with 2 LAN's, eth0 192.168.100.0 on range and eth1 on 192.168.0.0 range
The setup is to forward tcp on port 11500 incoming on eth0 to destination of 192.168.0.212:11500. I have a TCP server listening on port 11500. When I do a 'telnet 192.168.100.223 11500' from PC with IP 192.168.100.20 on the eth0 range (192.168.100.0), I get the following response on the TCP Server:
```
09/11 14:28:56.765 > SOURCE: ClientConnect - 192.168.100.20
09/11 14:28:56.765 > SOURCE: Server Exception, Socket Error # 10054
Connection reset by peer.
```So a connection is happening, but disconnected immediately. What is strange is that it shows the IP address as the actual IP address, and not a translated address (which should be 192.168.0.223)

If I do the same scenario from the eth1 range to the eth0 range, then it works fine., example if I do 'telnet 192.168.0.223 11290', the TCP server listening on 192.168.100.20 accepts the connection and the IP address show as 192,168.100.223

See below my current firewall setup

```
*nat
:PREROUTING ACCEPT [2:146]
:INPUT ACCEPT [2:146]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
-A PREROUTING -i eth0 -p tcp -m tcp --dport 11500 -m conntrack --ctstate NEW,RELATED,ESTABLISHED -j DNAT --to-destination 192.168.0.212:11500
-A PREROUTING -i eth1 -p tcp -m tcp --dport 11290 -m conntrack --ctstate NEW,RELATED,ESTABLISHED -j DNAT --to-destination 192.168.100.20:11910
-A POSTROUTING -o eth0 -j MASQUERADE
COMMIT

*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]
-A INPUT -i lo -j ACCEPT
-A INPUT -s 192.168.0.0/24 -i eth1 -j ACCEPT
-A INPUT -d 192.168.100.0/24 -i eth0 -p icmp -j ACCEPT
-A INPUT -d 192.168.100.0/24 -i eth0 -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -d 192.168.100.0/24 -i eth0 -p tcp -m conntrack --ctstate NEW,RELATED,ESTABLISHED -m tcp --dport 22 -j ACCEPT
-A INPUT -j REJECT --reject-with icmp-port-unreachable
-A FORWARD -p tcp -m tcp --dport 11500 -m conntrack --ctstate NEW,RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -p tcp -m tcp --dport 11290 -m conntrack --ctstate NEW,RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -i eth0 -o eth1 -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -i eth1 -o eth1 -j ACCEPT
-A FORWARD -i eth1 -o eth0 -j ACCEPT
-A FORWARD -j REJECT --reject-with icmp-port-unreachable
-A OUTPUT -p icmp -m conntrack --ctstate INVALID -j DROP
-A OUTPUT -o lo -j ACCEPT
-A OUTPUT -s 192.168.100.0/24 -d 192.168.0.0/24 -o eth1 -j ACCEPT
-A OUTPUT -s 192.168.0.0/24 -d 192.168.0.0/24 -o eth1 -j ACCEPT
-A OUTPUT -d 192.168.0.0/24 -o eth0 -j REJECT --reject-with icmp-port-unreachable
-A OUTPUT -s 192.168.100.0/24 -o eth0 -j ACCEPT
-A OUTPUT -j REJECT --reject-with icmp-port-unreachable
COMMIT

```

I do have ip_forwarding set to 1 (echo 1 > /proc/sys/net/ipv4/ip_forward)

---

### Post by darkod on 2012-09-11
It looks good, and I don't know iptables in details, but why don't you try with simpler rules for a start. For example, if you want the connection allowed, why adding the state filtering?

See if something like this would work:
```
-A PREROUTING -i eth0 -p tcp --dport 11500 -j DNAT --to 192.168.0.212
```

Change accordingly for the FORWARD chain too.

---

### Post by SeijiSensei on 2012-09-11
> **pieterlouw said:**
> What is strange is that it shows the IP address as the actual IP address, and not a translated address (which should be 192.168.0.223)

If I do the same scenario from the eth1 range to the eth0 range, then it works fine., example if I do 'telnet 192.168.0.223 11290', the TCP server listening on 192.168.100.20 accepts the connection and the IP address show as 192,168.100.223

Your masquerading rule only applies to traffic sent out eth0.  That's what the "-o eth0" parameter means.  So traffic arriving on eth1 is sent out eth0 with the IP address of eth0, but traffic arriving on eth0 is not masqueraded at all.

I'm not sure what happens if you masquerade in both directions since it's not clear to me what would happen to replies to outbound packets.  Is there any reason why the inbound traffic needs to be masqueraded?  Is it not possible to have the server you are trying to reach accept traffic from the 192.168.0.0/24 network as well as traffic from 192.168.100.0/24?

If not, then you might write a narrow rule to masquerade only traffic intended for the server.  Something like this:

```
iptables -t nat -A PREROUTING -i eth0 --dport 11500 -j DNAT --to-destination 192.168.0.212
```

If that doesn't work, try replacing "PREROUTING" with "OUTPUT".

---

### Post by pieterlouw on 2012-09-12
Thanks for your input and help

I got it working now. 

Firstly I made the changes you guys suggested. Then when I tested it, it still didn't work. But after some discussion with a colleague of mine it dawned on me that it is working fine if the IP Address did not change. So I changed my setup to the external interface going to the internet, and all is 100%, meaning if I come in from outside the NATting works 100%

---


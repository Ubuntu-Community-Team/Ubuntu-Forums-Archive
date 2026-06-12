---
title: "Openvpn Problem"
date: 2009-01-09
forum: Server Platforms
---

### Post by xinel on 2009-01-09
Hello,

I have made a server using 8.10. 
The server allows all traffic from the inside network to the Internet.
The server allows traffic from the Internet to the inside network as long as its established and related.

Without Openvpn running my server works and I can use irc, websurf, check my e-mail etc on computers on the inside (safe) network.

Once I start openvpn on my server I connect to a different server on the internet that hides my ip etc and allows me to be anonymous. 

When I just had openvpn running on my home machine (no server) I could use irc, surf, check email etc anonymously.

Now when I start openvpn on my server all I can do from the inside (safe) network is web surf. I would like to be able to do everything.

Anyone have any ideas?

Cheers

- xinel

---

### Post by xinel on 2009-01-11
Ok I've changed my firewall settings and I can now surf but I cannot use other programs like IRC, pigeon etc. I believe the problem is with my firewall rules. Some online web pages say my IP is my internal LAN 192.168.3.0 other web pages say its the IP of the external VPN server. I would like the outside world to believe I have only one IP and thats the external VPN server IP

My new firewall rules are: 

INCOMING: default action DROP

Accept 	If protocol is ICMP 		

Accept 	If input interface is lo 		

Accept 	If input interface is eth0 		

Accept 	If input interface is eth2 and state of connection is ESTABLISHED,RELATED 		

Accept 	If input interface is tun0 and state of connection is ESTABLISHED,RELATED


FORWARDING: default action DROP
Accept 	If input interface is eth0 and output interface is eth2 		

Accept 	If input interface is eth2 and output interface is eth0 and state of connection is ESTABLISHED,RELATED 		

Accept 	If input interface is eth0 and output interface is tun0 		

Accept 	If input interface is tun0 and output interface is eth0 and state of connection is ESTABLISHED,RELATED

OUTGOING: default action ACCEPT

Could anyone please offer suggestions on how to fix my problem.

Cheers

xin

---

### Post by xinel on 2009-01-11
I fixed it !!!!!! :) :) :)

Needed to masquerade tun0 

Thanx to everyone who looked.

---


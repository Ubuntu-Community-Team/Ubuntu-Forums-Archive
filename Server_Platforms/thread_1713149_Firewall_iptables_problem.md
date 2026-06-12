---
title: "Firewall iptables problem"
date: 2011-03-23
forum: Server Platforms
---

### Post by coolburnmx on 2011-03-23
I have a problem

I need to do a captive portal, but, without the packages that already  exist, because i have diferent needs, because I'm not gonna give  internet to the clients, that why i don't need to put a webpage with  user and password, just need that no mather what page they want to  search always brings my webpage.

i need to modify the destination ip address from any network call to my  dns server and redirect it to an a webpage in the same server.

I already have

[I]sudo iptables -t mangle -A INPUT -p 53 -j DNAT --to-destination 192.168.2.2

[/I]the curious thing is that i tried without the ip address, and the server tells that i need the argument for "*--to-destination", *so, the commands before have a good syntax.

Can someone knows where is the problem? or gave me another solution?[-o<

			 		   		 		 		By the way the error that appears is

"*iptables: No Chain/target/match by that name."*

thanks

---

### Post by BkkBonanza on 2011-03-23
It seems the error message tells you what's wrong. No table/chain by that name.
ie. there is no table named "mangle".

I usually add such rules to the **nat** table, **PREROUTING** chain.
Read the **man iptables** page on the differences between the tables. 

I'm not sure why it says you don't have mangle, INPUT but it is giving that msg. Perhaps you are on an old version of the kernel that doesn't have the INPUT chain on mangle? That chain was added in 2.4.18, so it would have to be real old.

You could use iptables -vnL -t mangle to see what chains are there.

---

### Post by coolburnmx on 2011-03-25
thanks for replaying...

the core that i use in this server is 2.6.32-30 

i read the manual before, and because i want to change the destination of the dns call (udp 53 port), that's why i chose mangle

the command that you gave me says i have the mangle table, responde this:

Chain PREROUTING (policy ACCEPT 111 packets, 11876 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 111 packets, 11876 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 77 packets, 11080 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 77 packets, 11080 bytes)
 pkts bytes target     prot opt in     out     source               destination         
as you said, neither do i know the reason of why the server can't take the command.

do you think that in the nat / prerouting chain can accept the command

i tried that, but, the firewall do not redirect the every search to my server and webpage :S

---

### Post by BkkBonanza on 2011-03-25
Try adding a **-i eth0** (or whatever your interface name is) to the match criteria before **-p 53**. 

The error msg says "no chain/table/match" so if not table or chain, that leaves match. It could be it cannot match port 53 on "any" interface so it needs an IP target or interface target to match on.

---


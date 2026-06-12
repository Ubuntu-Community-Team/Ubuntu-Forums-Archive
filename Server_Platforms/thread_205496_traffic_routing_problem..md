---
title: "traffic routing problem."
date: 2006-06-28
forum: Server Platforms
---

### Post by mushr00m on 2006-06-28
I have a cheap second-hand router/firewall that I got going with an AC adapter with a lower amperage rating.  Under heavy traffic the router starts to misroute the ip packets that should be destined to my server:80 to my desktop:80 instead.

The port forwarding rules in the firewall are clearly set... 

Preset apps:HTTP, External port:80, Protocol: TCP, internal port:80, forward to:192.168.1.xxx, enabled.  (xxx being my server LAN IP)

Also SSL is also opened at 443, tcp and udp, is also forwarded to server:443

What can I do to make sure these HTTP packets get to the server in the short term while I dig around the closets for enough parts to build a PC-based firewall/router?

My ideas:
- iptables rule (PREROUTING?) on desktop pc to forward HTTP packets to server?  <-- I'm not sure how to implement this rule....

- dmz server and rely on iptables on server for local firewall functionability  <--- not sure this will work, as the router is part of the problem and this alters my local NFS shares for some reason.
[I]
edit[/I] - SSH port forwarding ( somthing like ssh -u user -p * -someoptions 80:desktop:server:80 ) *- I think this would hijack all port 80 traffic and is huge security risk.... so what worked for VNC via ssh won't work here.

Any other ideas?

mushr00m

---

### Post by mips on 2006-06-28
I don't think the under rated PSU has anything to do with this.
Why do you mask out a private IP address ???

I'll think about this a bit more later on.

---

### Post by mushr00m on 2006-06-28
I never want to reveal any more than I need to. :)  both computers are static addressed IP's, so the above IP rule's "xxx" would be 100.

**Server:** LAMP(apache2,mysql,perl/PHP, nfs, ssh, vnc via ssh)
Network device:	eth0
Hardware address:	00:13:d3:97:95:21
IP address:	192.168.1.100
Netmask:	255.255.255.0
Broadcast:	192.168.1.255
Multicast:	Enabled

**Workstation:**
Network device:	eth0
Hardware address:	00:11:2f:94:87:2c
IP address:	192.168.1.101
Netmask:	255.255.255.0
Broadcast:	192.168.1.255
Multicast:	Enabled

**Firewall/router:**
LAN (MAC Address: 00-06-25-08-bc-ee)
 	
   IP Address: 	192.168.1.1
   Subnet Mask: 	255.255.255.0
   DHCP server: 	Disable

WAN:   	
   (MAC Address: 00-06-25-08-bc-ef)
 	
   IP Address: 	xx.xxx.xx.xxx
   Subnet Mask: 	255.255.255.0
   Default Gateway: 	xx.xxx.xx.1

---

### Post by mushr00m on 2006-06-29
[QUOTE=mushr00m]I have a cheap second-hand router/firewall that I got going with an AC adapter with a lower amperage rating.  Under heavy traffic the router starts to misroute the ip packets that should be destined to my server:80 to my desktop:80 instead.[/QUOTE] I hunted around some thrift stores for a better AC adapter and my diligent work paid off when I found a correctly rated PSU(5V,2A), if that was the problem then I shouldn't have anymore "brown-outs".  I haven't started my bt client on the workstation yet, which is generally when I start getting incorrectly routed http traffic .


[QUOTE=mushr00m]
- iptables rule (PREROUTING?) on desktop pc to forward HTTP packets to server?  <-- I'm not sure how to implement this rule....
[/QUOTE]
I don't know if this is my friend yet, I usually use firestarter to build my rules and then I cut down the chains manually if needed.  

[QUOTE=mushr00m]
- dmz server and rely on iptables on server for local firewall functionability  <--- not sure this will work, as the router is part of the problem and this alters my local NFS shares for some reason.
[/QUOTE]

dmz didn't help at all, in fact, it made things worse by stealthing WAN:80 instead giving it up to the dmz'd server ...  untill I changed my server's ip from *.100 to *.102.  That opened my port 80, and it has been open overnight.
[QUOTE=mushr00m]
[I]
edit[/I] - SSH port forwarding ( somthing like ssh -u user -p * -someoptions 80:desktop:server:80 ) *- I think this would hijack all port 80 traffic and is huge security risk.... so what worked for VNC via ssh won't work here.
[/QUOTE]
This still seems like a security risk, and having slept on it I have decided that it would be in bad taste to hack it this way :)

So thats where I am now.  **Anyone have Comments? Suggestions? Ideas?**

mushr00m

---

### Post by mips on 2006-06-30
Have you had a look at Firewall Builder to do your rules ?

The easiest way to eliminate the problem is to stress test the router without any of the firewall stuff enabled anywhere. The slowly start adding the security one layer upon the other.

---


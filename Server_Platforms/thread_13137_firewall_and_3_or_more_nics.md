---
title: "firewall and 3 or more nics"
date: 2005-01-29
forum: Server Platforms
---

### Post by flade on 2005-01-29
Hi,

Don't know if I posted this question, but i have some probles regarding more nics on ubuntu.

I have situation like this:

3 network segments using public IPs (not private), I have a intranet server that all segmets need access to.

How to use Firestarter to open access to server from 3 nics (segments)

Is this have to do with NAT ? And if Firewall capable of doing this ?
 

----------
+ Fladë

---

### Post by alastair on 2005-01-31
I'm not familiar with Firestarter (sorry) and you might be better off asking in Firestarter mailing list. I assume the mailing list is available here :

[http://www.fs-security.com/list.php](http://www.fs-security.com/list.php)

---

### Post by kagou on 2005-02-01
I think that shorewall will be more usefull for this.
[HERE](http://shorewall.net/)

---

### Post by flade on 2005-07-14
Can someone please send me their shorewall config or even iptables. 
As mentioned above, I  use 3 network cards on our server that uses public IP's. After running firestarter nics are not responsing and no traffic is sent in or out of server. Why ?

Previously I've installed Fedora core 2 and it worket great. No need for firewall.


help.



regards,

---

### Post by LordHunter317 on 2005-07-14
Post some actual networking details (IP addresses, iface names, etc) and exactly what you need to do, and I can write you a firewall script to do it.

 A picture of your network topology would be nice as well, but not required as long as you give lots of details.  

Based on your scant information, I can't even tell what you really want to do besides push packets, much less how to do it.

---

### Post by flade on 2005-07-14
Here goes.

- server with 3 network cards
- 3 network segments that can not see each other, but can access same server. 
- Server has to be able to communicate to them and to internet.
- Services that has to be open to local use
   HTTP,
   SSH,
   FTP,
   SAMBA,
   VNC, 
   mail protocols,

- I use public IPs but let say the following will just do.
   exmpl:
   eth0 = 192.168.0.1 (this one uses internet access as well)
   eth1 = 192.168.1.1
   eth2 = 192.168.2.1


Hope this helps

---

### Post by relix42 on 2005-07-15
There is an essential thing here to understand:

You **do not** need a iptables or a firewall distribution to pass packets between networks cards.  This is simple routing any any Linux distro will do this as it's mostly handled by the kernel.  The difference between routing and firewalling: essentially, a firewall is a router that does more in depth packet analysis (i.e. NATing, tagging, mangling, denying, etc) versus a router - a router simply looks at the available networks and gateways, makes a decision and sends the packet on.

With that being said, in order to route packets between your interfaces, do the following:

1) Make sure that the ethernet adapters and their respective IP addresses and netmasks are correct.
2) Verify that value of /proc/sys/net/ipv4/ip_forward is 1 not 0 (cat the file).  If it's 0 this tells the kernel to **not** forward packets between interfaces.  To change this flag:
```
sudo echo "1" > /proc/sys/net/ipv4/ip_forward
```

To make the change permanent after a reboot, edit the file /etc/sysctl.conf and add:
```
net/ipv4/ip_forward = 1
```

If you want/need to do more, such as NATing or logging the packets, then you will need to venture into IPTables, however, the above will still need to be done first.

Feel free to post again if you need IPTables help.

---

### Post by flade on 2005-07-28
I've added the code in /etc/sysctl.conf as you written but after reboot I have to manually add 1 to .../ip_forward

Is there any other way or file that is read during the bootup.




Flade

---

### Post by flade on 2005-07-28
I think I solved the problem.

I removed the firestarter as I think he was the one that cause me a lot of trouble. Allways was deleting number 1 from ip_forward (or was blocking sysctl) dunno really. 

But now I discovered that If u have more than 1 nic in /etc/network/interfaces gateway has to be set just for primary interface. 

Am I right with my conclusions ?

Fladé

---

### Post by relix42 on 2005-07-29
[QUOTE=flade]I think I solved the problem.
But now I discovered that If u have more than 1 nic in /etc/network/interfaces gateway has to be set just for primary interface. 

Am I right with my conclusions ?
[/QUOTE]

In a way, yes.  This has more to do with TCP/IP then Ubuntu specifics.  And, I believe, you mean deafult gateway, not just gateway.  (Again, using TCP/IP verbage not config file verbage.)

The most basic of routing decisions are handled as such:
[INDENT]Is the destination address for this packet local or not?[/INDENT] 
When the answer is yes, the packet is sent directly to the desitnation address.  If not, the packet is sent to the gateway for that network for routing.  When a packet is destined for an address that is not local and is not for a local gateway, it is sent to the default gateway for handling.  

Essentially, the system looks to see if a specific route is available for the packet, if not the gateway of last resort (the default gateway) is used for the packet.

So. no matter how many NICs you have, you should have only one default gateway.  Although there are ways and protocols available to change this (i.e. having more then one default gateway for load balancing/fail over puposes) they are way out of the scope of this discussion.

Consider the following examples:

1)
Machine with two NICs
eth0 connected to a private network = IP: 10.0.0.1 NetMask:255.255.255.0
eth1 connected to the internet = IP: 200.200.200.200 netmask 255.255.255.0
Default gateway is set to 200.200.200.1

The machine wants to send traffic to the machine with the ip address of 10.0.0.121.

In this example, 
* the combination of IP/NetMask of 10.0.0.1/255.255.255.0 tells the machine that all addresses, 10.0.0.1 through 10.0.0.254 (.0 network address and .255 broadcast address - are local but reserved) are routed through the interface with the IP address of 10.0.0.1 (eth0).  
* the combination of 200.200.200.200/255.255.255.0 tells the machine that all addresses 200.200.200.1 through 200.200.200.254 (.0 network address and .255 broadcast - are local but reserved) are routed through the interface with the IP address of 200.200.200.200 (eth1).
* the default gateway address of 200.200.200.1 tells that machine should any traffic not qualify for either of the above, route that traffic through the machine (gateway through) with the address of 200.200.200.1.  And, with the routing table above, the machine know that the machine with the address of 200.200.200.1 is sent through the interface with the address of 200.200.200.200 because it is local (i.e. on the same network) as the machine with the address of 200.200.200.1.  (This explains why your default gateway has to be on a local network.)

Machine with 5 NICs 
(Shorter on explanations - refer above should something seem funny)

eth0 30.3.3.3 netmask 255.255.255.248
eth1 192.168.1.10 netmask 255.255.255.0
eth2 172.16.30.23 netmask 255.255.255.0
eth3 10.0.1.18 netmask 255.255.254.0
eth4 192.168.10.18 netmask 255.255.255.128
Default gatewat set to 30.3.3.1


What's local to each interface?
eth0 30.3.3.0 - 30.3.3.7
eth1 192.168.1.0 - 192.168.1.255
eth2 172.16.30.0 - 172.16.30.255
eth3 10.0.0.0 - 10.0.1.255
eth4 192.168.10.0 - 192.168.10.127

With that information, which interface would be the gateways for the following destination addresses?

1) 30.3.3.1
2) 192.168.10.121
3) 10.0.0.228
4) 10.0.3.18
5) 172.16.30.121
6) 192.168.10.251
7) 64.121.17.221
8) 10.0.1.255

Which and why
1) eth0 - local to this interface
2) eth4 - local to this interface
3) eth3 - local to this interface
4) eth0 - not local to any interface, sent through the gateway
5) eth2 - local to this interface
6) eth0 - not local to any interface, sent through the gateway
7) eth0 - not local to any interface, sent through the gateway
8) eth3 - local to this interface

This same logic is extensible to a machine with 8, 24, 100 NICs.  The same analysis is done.  Many problems come into play for people when the gateway to which they are pointing isn't correctly configured or when people assume that the netmask is always 255.255.255.0.  Whenever you have problems getting packets to where they go, 'traceroute' and 'route'/'ip' are you best friends.  They will reveal where the machine is attempting to direct packets.

Hope this helps, post back if anything I've said is unclear - trying to do two things at once this morning.

---

### Post by BuntuHung on 2005-08-11
thanks a lot relix42! that was a big help for me too!

---

### Post by relix42 on 2005-08-11
Glad I could help.  I've seen enough of these questions that I think it may be time to write a guide on routing and firewalling that answers a lot of the commonly seen questions.

What do you think?

---

### Post by flade on 2005-08-13
[QUOTE=relix42]Glad I could help.  I've seen enough of these questions that I think it may be time to write a guide on routing and firewalling that answers a lot of the commonly seen questions.

What do you think?[/QUOTE]

That would be great.

I still have some difficulties setting up my server with 3 nics. It seems that when I connect all nics to network, server stops responding on all 3 IP's, but from server you can browse internet. I belive this is firewall problem afterall. 

Could you point me to some directions.


regards,

flade

---

### Post by relix42 on 2005-08-17
[QUOTE=flade]That would be great.
Could you point me to some directions.
[/QUOTE]

What is the current output of:
   ifconfig
   route -n
   iptables -L -n
   iptables -t nat -L -n
   cat /proc/sys/net/ipv4/ip_forward

---

### Post by flade on 2005-09-17
Was very bussy at work.

Thing is that I reinstalled my ubuntu box, configured it like you said and voila... It works.


Thanks for help.

regards,

---


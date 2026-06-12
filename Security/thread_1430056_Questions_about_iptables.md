---
title: "Questions about iptables"
date: 2010-03-14
forum: Security
---

### Post by cyphaw on 2010-03-14
Hi everybody,

I've got some questions about iptables that google wasn't able to answer, so if you can, even if partially, thank you!

I just focus on the filter table:

First  : What is the meaning of the "opt" parameter?

Second : What is the aim of the "destination" for the INPUT chain ? The destination must be the ip of machine, isn't it ? I must put anywhere (except if my ip is fixed), right?

Third : The same : What is the aim of "source" for the OUTPUT chain?

Fourth : What are the following rules?
```
target     prot opt in     out     source               destination
ACCEPT     udp  --  eth1   any     anywhere             anywhere            udp dpt:bootps 
ACCEPT     tcp  --  eth1   any     anywhere             anywhere            tcp dpt:bootps 
ACCEPT     udp  --  eth1   any     anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  eth1   any     anywhere             anywhere            tcp dpt:domain
```eth1 is my wireless interface and I use it on a local network, my comp being the gateway.
I suppose that "domain" is linked to the dns and it must be open if the devices on the lan specified my comp as their dns, right? But what about bootps?


Thanks a lot!

cyphaw

---

### Post by cdenley on 2010-03-15
1. I'm not sure. I don't recall ever seeing that column used.

2. The destination is an IP address. Not specifying a destination implies anywhere. The destination IP can vary if you're creating rules for a router, gateway, firewall, or bridge.

3. To filter based on source IP.

4. Those rules allow all traffic on port 53 TCP or UDP and port 67 TCP or UDP. It prints the service commonly associated with the port instead of the port number because you didn't use the "-n" argument.

```

sudo iptables -L -n

```

Port 53 would be used for DNS, and I believe port 67 would be for DHCP.

---

### Post by cyphaw on 2010-03-15
Thanks cdenley,

I knew about the "-n" argument and the port numbers, I just didn't knew what it was for, but the dhcp seems logical.

But for the INPUT and OUTPUT chains: are you meaning that a packet can go through those chains in a forwarding process?

I thought that a packet could go through OUTPUT only if it comes from my machine and thus if its source ip was the ip of my machine.


From what I've seen, a packet that is forwarded by a router or a gateway goes through PREROUTING, FORWARD and POSTROUTING, not through INPUT and OUTPUT. Am I wrong?

---

### Post by cdenley on 2010-03-15
> **cyphaw said:**
> 
But for the INPUT and OUTPUT chains: are you meaning that a packet can go through those chains in a forwarding process?

I thought that a packet could go through OUTPUT only if it comes from my machine and thus if its source ip was the ip of my machine.


From what I've seen, a packet that is forwarded by a router or a gateway goes through PREROUTING, FORWARD and POSTROUTING, not through INPUT and OUTPUT. Am I wrong?

That is correct. I was explaining what the columns mean for all chains, since they are all displayed with that format when using the "iptables" command.

---

### Post by cyphaw on 2010-03-15
Alright, so source for OUTPUT and destination for INPUT are useless, that's what I wanted to know.

Thanks a lot, problem solved! :smile:

---

### Post by cdenley on 2010-03-15
> **cyphaw said:**
> Alright, so source for OUTPUT and destination for INPUT are useless, that's what I wanted to know.

Thanks a lot, problem solved! :smile:


Edit: the question now is "how do I put the tag [solved] instead of [all variants]?" :S

Not quite useless. Many servers have multiple IP's, even on a single interface.

You should be able to mark it as solved by clicking "thread tools" above your first post.

---

### Post by cyphaw on 2010-03-15
> **cdenley said:**
> Not quite useless. Many servers have multiple IP's, even on a single interface.

Ok, I didn't think about this, you're right.
Anyway, in my case, I'll just let anywhere, that will be enough.
(in fact, I can't connect my itouch on my wireless lan with a wep or wpa security, thus I made an open network but I saw some people connecting on it and accessing Internet through my computer. So I made iptables so that only one ip can go through FORWARD, and when the network is up, my itouch has this ip. That's a bit dirty but it works)

---

### Post by cdenley on 2010-03-15
> **cyphaw said:**
> Ok, I didn't think about this, you're right.
Anyway, in my case, I'll just let anywhere, that will be enough.
(in fact, I can't connect my itouch on my wireless lan with a wep or wpa security, thus I made an open network but I saw some people connecting on it and accessing Internet through my computer. So I made iptables so that only one ip can go through FORWARD, and when the network is up, my itouch has this ip. That's a bit dirty but it works)

Still not fool-proof, but you would probably be better off filtering by mac address, or even both.

---

### Post by cyphaw on 2010-03-15
I didn't know about the MAC module of iptables, now that's fool proof :

```
Chain INPUT (policy DROP)
target     prot opt in     out     source               destination         
ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22 
ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
ACCEPT     udp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
ACCEPT     tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:67 
ACCEPT     udp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 
ACCEPT     tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53 

Chain FORWARD (policy DROP)
target     prot opt in     out     source               destination         
ACCEPT     all  --  *      *       0.0.0.0/0            10.42.43.10         state RELATED,ESTABLISHED 
ACCEPT     all  --  *      *       10.42.43.10          0.0.0.0/0           MAC 00:25:BC:XX:YY:ZZ 
```I just need to remember that I did that to avoid being stuck in the future if I try to connect another device!

Thanks again!

---

### Post by cdenley on 2010-03-15
> **cyphaw said:**
> I didn't know about the MAC module of iptables, now that's fool proof

Not fool-proof, as someone can still monitor your wireless traffic to determine your MAC address, then change theirs to match. Typically, people know how to change their IP but not their MAC, though it is possible.

---

### Post by cyphaw on 2010-03-15
> **cdenley said:**
> Not fool-proof, as someone can still monitor your wireless traffic to determine your MAC address, then change theirs to match. Typically, people know how to change their IP but not their MAC, though it is possible.

Yeah, I did this one time to bypass an identification process on a network: changed mac, the dhcp gave me the ip he associated with this mac and that's it (it seems that you needed to log in one single time and that the gateway remembered the ip/mac associated with the login/pass and filtered on the ip/mac without needing to login ever after. Reaaally secure...).

But I do not think that I can do anything else, and if someone do that there will be conflicts with two devices with the same ip and mac, since when my itouch is not connected, the network is shut down, and I should see it.

---


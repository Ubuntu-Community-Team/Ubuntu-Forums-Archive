---
title: "is ip_forward masquerading?"
date: 2010-09-13
forum: Server Platforms
---

### Post by horacv on 2010-09-13
Hi all,
        first of all, this is my first post. Even though i am not a complete GNU/Linux newbie, each day i discover how little i know of this wonderful OS. 
        The title of this post is actually a question for which i already have an answer, however, i can't seem to figure out why this happens. 
        In order to enable ip_forwarding, i always enable it the same way, by issuing an: 
#echo "1" > /proc/sys/net/ipv4/ipv4_forwarding. 
I don't enable forwarding at boot time on purpose, i prefer to do it manually if the server crashes. 
         The thing is, i always write rules for iptables in order to enable it to NAT my packages through the router. However, last night, i forgot to load the proper iptables script, and instead, used a script i am currently tweeking. In this script, no rules are listed for both the FORWARD chain and nat table in the POSTROUTING chain. 
          Since forwarding was working (to my surprise, i might add) this could only mean, that the kernel default forwarding policies include masquerading. Is there a way to verify this?

Greetings.

---

### Post by CharlesA on 2010-09-13
Kinda. Masquerading = NAT. Forwarding is a part of that.

Not sure why it was working.

Could always cat /proc/sys/net/ipv4/ipv4_forwarding

and see if it's still set for 1.

---

### Post by horacv on 2010-09-13
Ok. I should explain myself better, specially since English is not my first tongue. 
basically: issuing an #echo "1" > /proc/sys/net/ipv4/ip_forwarding,
explicitly enables a NAT box inside the kernel. 
This could only be this way, since any message being forwarded through the router without any special nat/masquerading rules in iptables would receive an icmp Destination Unreachable, message.

Asked and answered. Sorry for the trouble. This baffled me the whole afternoon.

---

### Post by BkkBonanza on 2010-09-14
Actually if you look into the data flow thru iptables that isn't quite right.

NAT can be applied even when ip_forward is not enabled. It is applied in the PREROUTING and POSTROUTING chains of the nat table, which can affect traffic going to the INPUT/OUTPUT chains for the machine. 

"ip_forward" only affects if the FORWARD chain gets enabled, allowing traffic to go thru the box (skipping INPUT/OUTPUT chains). Now, usually we only apply NAT to the FORWARD traffic but it is possible otherwise, and is why SNAT is put in POSTROUTING and DNAT is put in PREPROUTING, since they need to affect also flow into the machine, or out of it.

This [diagram I sketched](http://img1.optimalseller.com/tx/iptables-flowchart.jpg) may make it clear (even though I think there may be a minor mistake)...

---

### Post by horacv on 2010-09-14
Indeed, one could NAT without any sort of forwarding. The point i was trying to make is that when ip_forwarding is enabled, the kernel is automatically mascarading the packages traveling through it.

---

### Post by BkkBonanza on 2010-09-14
Umm. No it's not. Packets will just go through as is. The purpose of the rules using SNAT, DNAT and MASQUERADE targets is to do the connection tracking and maintain the tables needed for these functions.

The kernel doesn't even drop or reject invalid or malformed packets, you'll need specific iptables rules to do that too.

---

### Post by horacv on 2010-09-14
I'm not sure. Lets say my computer uses 192.168.1.1 source ip address for the packages, and it is located behind a router. If the router doesn't somehow NAT the packages, they would find their way back. Again, there are no iptables rules in effect, except for default policies all set to ACCEPT.
As an example:
192.168.1.1 (my pc)
192.168.1.254 (router)
72.14.253.104 (google)
if i ping from my pc to google, and the router doesn't nat the packages, no replies would ever come through, since the source address for the reply is an address that shouldn't bee seen anywhere in the Internet. 
This would mean that my ping would result in timeouts. So, by echo "1" to ip_forward, the machine must be, somehow masquerading.

---

### Post by BkkBonanza on 2010-09-14
Yes, the router NATs the PACKETS. But not your computer.

But the router only does it because it's configured as a router with NAT rules already in place. I have done this to my Ubuntu based router and without the rules it won't just NAT by default. 

You have to add a SNAT rule to the POSTROUTING chain. And for port forwarding, a DNAT rule to the PREROUTING chain. The kernel won't do this by itself. These must be set each time the router boots, along with the ip_forward enabling. See **man iptables**.

---
Your computer sends packets with dest IP 72.14.253.104 to it's gateway, 192.168.1.254
Router uses SNAT rules in POSTROUTING chain to, 

[noparse]record origin IP 192.168.1.1:port and dest IP 72.14.253.104:port in NAT tables.[/noparse]

Then it replaces the packet src IP with it's own public IP (and often the port too). And sends the packet to it's gateway, the next hop, your ISP usually.

When a reply is received it looks in it's NAT tables and matches src IP 72.14.253.104 and dest port, and decides it needs to go back to 192.168.1.1 on correct port. It replaces the packet dest IP and port. And sends it out on it's LAN port.

Your system receives it thinking nothing is wrong. src IP is 72.14.253.104, and dest IP is 192.168.1.1, as normal. It gets passed via the PREROUTING and INPUT chains on it's way to your program, but your system need not change anything in the packet.
---
The NAT process occurs in the "nat" table in iptables using the PREROUTING/POSTROUTING chains and must be explicitly setup.

---

### Post by horacv on 2010-09-15
Iv'e tried the following:
#echo "0" > /proc/sys/net/ipv4/ip_forward
#iptables -X
#iptables -t nat --flush

The router doesn't forward anything, no access to the internet.
Now, 
#echo "1" > /proc/sys/net/ipv4/ip_forwarding

All pings get through. The kernel is *somehow* masquerading..

---

### Post by BkkBonanza on 2010-09-15
The only thing that comes to mind is that the nf_conntrack module is doing the NAT regardless of being told to - which doesn't make much sense. The actual tracking state is kept in /proc/net/nf_conntrack and /proc/net/ip_conntrack. 

Every reference I've ever read indicates that you need to add the POSTROUTING rule to do SNAT. So if it does it by default I have no idea why we add the rule.

I'm not sure if you made a typo in you post or are just doing it wrong but,

/proc/sys/net/ipv4/ip_forwarding

is not the correct value to set. It's

/proc/sys/net/ipv4/ip_forward

---

### Post by horacv on 2010-09-15
I'm going to try that. I'll disable the connection tracking in PREROUTING. I'll post the results this afternoon.

---

### Post by BkkBonanza on 2010-09-15
I had a look at the source code for nf_conntrack and the NAT code is definitely in there. It has comments indicating the decision to NAT is based on the _routes_ present.

So presumably using the **route** command affects what choices are made in NAT. I'm a bit surprised at that since I'd always believed the decision was up to the admin to control using the rules. I'm not sure if that is a recent change or not but I was looking at 2.6.20 source when I saw this.

The [netfilter]("http://en.wikipedia.org/wiki/Netfilter") and nf_conntrack modules can be selected during kernel compiling as to whether they are compiled in or dynamically loaded. I don't know what the normal choice is for Ubuntu but if it's compiled in by default, then it may be hard to remove the module. 

With a dynamic module you can remove any usage (dependency) of it, and unload the module. But when compiled in the kernel needs to be compiled again with it selected out for it to actually not be present. Though whether there's another setting to disable nf_conntrack I don't know. I didn't see anything obvious in the various control values in /proc/sys/net/ipv4/

---


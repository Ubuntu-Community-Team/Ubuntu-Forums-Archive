---
title: "Is Ubuntu Keeping All My Ports Stealthed?"
date: 2010-09-26
forum: Security
---

### Post by Ubuntiac on 2010-09-26
I know how to forward ports in my router.

Now I need to open a port to help with testing a project and no matter what I've tried, every port under 1055 shows up as stealthed (with 1-71 closed) according to Shields Up! I'm happy to run it at a port > 1024, but whatever I try also shows up stealthed. I even tried (briefly) turning on DMZ and still the same thing. My ISP swears that they only block port 80, 21 and 25, none of which I'm trying to use. UFW status reports inactive and I'm not using firestarter. I'm not running any other server (apache, light speed etc).

If it's not my router and it's not my ISP, and there's no other server apps running, then that kind of leaves Ubuntu as far as I can see,

Any ideas how to get this port open, anyone?

---

### Post by CharlesA on 2010-09-27
If there is nothing listening for connections, it will show that the port is closed or stealthed.

Shieldsup! tests your router, not the pc behind it.

What port do you need to be open?

---

### Post by Soul-Sing on 2010-09-27
not stealthed.
but there is a diff. between -drop and -deny.(rules)
stealthed isn't that important.

if your behind a router ports are mostly "stealthed".

---

### Post by Ubuntiac on 2010-09-27
Thanks Charles,

Preferably 3000 for testing Diaspora (yes, I know it has security issues at the moment), although I'm not averse to running a non standard port (if I can get it open).

Diaspora reports "Listening on 192.168.2.11:3000, CTRL+C to stop"

Ifconfig gives:
> eth1      Link encap:Ethernet  HWaddr 00:08:54:a5:88:b3  
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fea5:88b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1142550 errors:0 dropped:0 overruns:0 frame:0
          TX packets:900748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1132515464 (1.1 GB)  TX bytes:135585690 (135.5 MB)
          Interrupt:21 Base address:0xe800 

I also tried running Diaspora on 192.168.2.255. Shields up to test if my router was the problem, but it really does seem that the port forwarding is set up right...

So any better tests than shields up for whether a port replies?

---

### Post by The Cog on 2010-09-27
Don't use 192.168.2.255 - that's the broadcast address. 192.168.2.11 is fine.

First, check if you have any firewall rules. Ubuntu installs by default with the firewall in a permissive mode (permit everything), but installing a firewall configuration utility like gufw will change that. Use the command **sudo iptables -nvL** and make sure the output is like this, with all three chains saying policy ACCEPT and no other rules listed:
> Chain INPUT (policy ACCEPT 7717 packets, 974K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 35651 packets, 4558K bytes)
 pkts bytes target     prot opt in     out     source               destination     

Second, you can add a rule to count the number of connections coming in to your server:
**sudo iptables -I INPUT -p tcp --dport 3000 -m state --state NEW -j LOG**
These will show in the command **sudo iptables -nvL** and also in **tail /var/log/messages**

This will tell you for sure if the connection requests are reachong your server.

---

### Post by CharlesA on 2010-09-27
You can also check ***netstat -ln*** to see if it's listening on port 3000.

---

### Post by cprofitt on 2010-09-27
> **The Cog said:**
> Don't use 192.168.2.255 - that's the broadcast address. 192.168.2.11 is fine.

It could be a broadcast address... x.x.x.255 is not always a broadcast address.

10.120.0.0/23 for example

or

192.168.2.0/25 which would have 192.168.2.127 as its broadcast address.

---

### Post by The Cog on 2010-09-27
> **cprofitt said:**
> It could be a broadcast address... x.x.x.255 is not always a broadcast address.
Yes, but given the tone of his posts, I don't think he's been messing around configuring cidr on his router, somehow.

---

### Post by cprofitt on 2010-09-27
> **The Cog said:**
> Yes, but given the tone of his posts, I don't think he's been messing around configuring cidr on his router, somehow.

I agree, but we never know who will be reading this stuff in the future so I always err on the side of accuracy as much as possible.

---


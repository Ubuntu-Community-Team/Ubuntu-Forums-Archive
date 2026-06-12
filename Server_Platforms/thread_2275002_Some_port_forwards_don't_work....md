---
title: "Some port forwards don't work..."
date: 2015-04-23
forum: Server Platforms
---

### Post by fizgig on 2015-04-23
I'm on 14.04.2 server and I have two network cards with 8 total ports.  Only five are being used (4 on one card, 1 on the other).  Here are the interface specs:

p1p1 = 192.168.1.*
p1p2 = 192.168.2.*
p1p3 = 192.168.3.*
p1p4 = 192.168.5.*  (I skipped over 4.* for some reason I have forgotten)
p3p1 = 192.168.6.*

I have one network port that has 5 public IPs on it called em1.  So there's an em1, em1:0, em1:1 and so on.

Anyhow, each port is doing masquerading and there is some port forwading from p1p1 (which is the interface I am on usually) as you can see in the   /etc/ufw/before.rules:

```
*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]

# Port Forwardings
-A PREROUTING -i p1p1 -p tcp -d 192.168.3.4 -j DNAT --to-destination 192.168.3.4
-A PREROUTING -i p1p1 -p tcp -d 192.168.3.5 -j DNAT --to-destination 192.168.3.5
-A PREROUTING -i p1p1 -p tcp -d 192.168.5.4 -j DNAT --to-destination 192.168.5.4
-A PREROUTING -i p1p1 -p tcp -d 192.168.5.5 -j DNAT --to-destination 192.168.5.5
-A PREROUTING -i p1p1 -p tcp -d 192.168.6.4 -j DNAT --to-destination 192.168.6.4
-A PREROUTING -i p1p1 -p tcp -d 192.168.6.5 -j DNAT --to-destination 192.168.6.5

# Forward traffic from  through eth0.
-A POSTROUTING -s 192.168.1.0/24 -o em1 -j SNAT --to publicIP1
-A POSTROUTING -s 192.168.2.0/24 -o em1 -j SNAT --to publicIP2
-A POSTROUTING -s 192.168.3.0/24 -o em1 -j SNAT --to publicIP3
-A POSTROUTING -s 192.168.5.0/24 -o em1 -j SNAT --to publicIP4
-A POSTROUTING -s 192.168.6.0/24 -o em1 -j SNAT --to publicIP5

# don't delete the 'COMMIT' line or these nat table rules won't be processed
COMMIT

---Other stuff I haven't changed...


```


This all works pretty well.  Everyone can browse the internet and each subnet gets its own public IP address.  I have those port forwards in there in order for me to be able to login to wireless bridge equipment inside each subnet to troubleshoot issues.  I'm able to get to all the wireless equipment (*.4, *.5) in each subnet from my own 1.* subnet except for the 192.168.6/24 subnet.  The rules are exactly the same for this subnet and I'm not sure why the forward isn't working like the others are.

The only difference is that the 192.168.6/24 is by itself on its own network card.  That's why you see the first four local IP addresses belonging to p**1**p* and the fifth belongs to p**3**p1.

When I'm ssh'ing into this main server, I'm able to ping the 192.168.6.4 and 192.168.6.5 equipment so that works.  The port forwarding just doesn't.  Here's a snippet from **iptables -t nat -vnL**:

```
root@RGateway:/home/matt# iptables -t nat -vnL
Chain PREROUTING (policy ACCEPT 4844 packets, 343K bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DNAT       tcp  --  p1p1   *       0.0.0.0/0            192.168.3.4          to:192.168.3.4
    0     0 DNAT       tcp  --  p1p1   *       0.0.0.0/0            192.168.3.5          to:192.168.3.5
    0     0 DNAT       tcp  --  p1p1   *       0.0.0.0/0            192.168.5.4          to:192.168.5.4
    0     0 DNAT       tcp  --  p1p1   *       0.0.0.0/0            192.168.5.5          to:192.168.5.5
    0     0 DNAT       tcp  --  p1p1   *       0.0.0.0/0            192.168.6.4          to:192.168.6.4
    0     0 DNAT       tcp  --  p1p1   *       0.0.0.0/0            192.168.6.5          to:192.168.6.5


Chain INPUT (policy ACCEPT 95 packets, 6592 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 45 packets, 12708 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain POSTROUTING (policy ACCEPT 99 packets, 17828 bytes)
 pkts bytes target     prot opt in     out     source               destination
 2784  165K SNAT       all  --  *      em1     192.168.1.0/24       0.0.0.0/0            to:publicIP1
    0     0 SNAT       all  --  *      em1     192.168.2.0/24       0.0.0.0/0            to:publicIP2
    8   817 SNAT       all  --  *      em1     192.168.3.0/24       0.0.0.0/0            to:publicIP3
  129  9430 SNAT       all  --  *      em1     192.168.5.0/24       0.0.0.0/0            to:publicIP4
  562 44010 SNAT       all  --  *      em1     192.168.6.0/24       0.0.0.0/0            to:publicIP5

```

Here are the routes:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         My_Public_Gateway  0.0.0.0         UG    0      0        0 em1
My_public_network_number  *               255.255.255.248 U     0      0        0 em1
192.168.1.0     *               255.255.255.0   U     0      0        0 p1p1
192.168.2.0     *               255.255.255.0   U     0      0        0 p1p2
192.168.3.0     *               255.255.255.0   U     0      0        0 p1p3
192.168.5.0     *               255.255.255.0   U     0      0        0 p1p4
192.168.6.0     *               255.255.255.0   U     0      0        0 p3p1

```

Thanks!

---

### Post by matt_symes on 2015-04-23
Hi

> -A PREROUTING -i p1p1 -p tcp -d 192.168.6.4 -j DNAT --to-destination 192.168.6.4
-A PREROUTING -i p1p1 -p tcp -d 192.168.6.5 -j DNAT --to-destination 192.168.6.5

Maybe i'm not understanding correctly but shouldn't the interface be p3p1 above for this subnet ? 

Kind regards

---

### Post by fizgig on 2015-04-23
> **matt_symes said:**
> Hi



Maybe i'm not understanding correctly but shouldn't the interface be p3p1 above for this subnet ? 

Kind regards

I thought the -i was stating where the packet was coming from.  In my case, the packets will always be coming from me on the p1p1 (192.168.1/24) interface.  I just modified it anyway and, unfortunately, it didn't make a difference.

---

### Post by Doug S on 2015-04-23
> **fizgig said:**
> I thought the -i was stating where the packet was coming from.  In my case, the packets will always be coming from me on the p1p1 (192.168.1/24) interface.  I just modified it anyway and, unfortunately, it didn't make a difference.Actually, that whole DNAT block doesn't make any sense to me, because it seems to be a NOP, doing nothing. I must not be understanding something.

---

### Post by fizgig on 2015-04-23
Looks like you're right.  I just commented out those lines and I'm able to still ping into other subnets (although still not into the 6.* subnet).  Guess those rules weren't doing anything.

Guess I have a new question - how do I separate the subnets from each other?

---

### Post by matt_symes on 2015-04-23
Hi

> **fizgig said:**
> I thought the -i was stating where the packet was coming from.  In my case, the packets will always be coming from me on the p1p1 (192.168.1/24) interface.  I just modified it anyway and, unfortunately, it didn't make a difference.

That's me not understanding the question then :)

There are people better qualified to answer this question than me who frequent these fora so wait and see who replies.

One question i do have: Have you run tcpdump with a filter to see where the packets are going ?

Kind regards

---

### Post by fizgig on 2015-04-23
Haven't tried tcpdump yet.   Will look into how to use it - always want to learn a new tool.

Meanwhile, I've changed the before.rules to use MASQUERADING instead of SNAT.  I also show three port forwards that allow external traffic to reach my asterisk server.  Those port forwards work.

```
# nat Table rules
*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]

# Port Forwardings
-A PREROUTING -i em1 -p tcp --dport 4569 -j DNAT --to-destination 192.168.1.14
-A PREROUTING -i em1 -p udp --dport 4569 -j DNAT --to-destination 192.168.1.14
-A PREROUTING -i em1 -p tcp --dport 23299 -j DNAT --to-destination 192.168.1.14


# Forward traffic from  through eth0.
-A POSTROUTING -s 192.168.1.0/24 -o em1 -j MASQUERADE
-A POSTROUTING -s 192.168.2.0/24 -o em1:0 -j MASQUERADE
-A POSTROUTING -s 192.168.3.0/24 -o em1:1 -j MASQUERADE
-A POSTROUTING -s 192.168.5.0/24 -o em1:2 -j MASQUERADE
-A POSTROUTING -s 192.168.6.0/24 -o em1:3 -j MASQUERADE
```

I still can't ping the network equipment in the 6.* subnet but I can pick everything else.  In fact everyone can talk to everyone else (glad they're not actually using it yet).  I'm researching now how to keep them from talking to each other.

---

### Post by Doug S on 2015-04-23
> **fizgig said:**
> Haven't tried tcpdump yet.   Will look into how to use it - always want to learn a new tool.Matt's tcpdump idea is a good one. It will help figuring out what is going on.> **fizgig said:**
> Meanwhile, I've changed the before.rules to use MASQUERADING instead of SNAT.  And that is working? It shouldn't be. You need to use SNAT in this case, and you can not specify an aliased interface name with iptables. There was some other thread about this recently. If it is working, I'll have to go back and study why, as maybe something has changed with some newer version of iptables.

Perhaps show us your entire iptables, including the counters, both nat and the not nat  part.

---

### Post by Doug S on 2015-04-23
Could you post the output for the "route" command on your server.

---

### Post by fizgig on 2015-04-23
Sure!

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         Public_Gateway_IP  0.0.0.0         UG    0      0        0 em1
My_Public_subnet_number *               255.255.255.248 U     0      0        0 em1
192.168.1.0     *               255.255.255.0   U     0      0        0 p1p1
192.168.2.0     *               255.255.255.0   U     0      0        0 p1p2
192.168.3.0     *               255.255.255.0   U     0      0        0 p1p3
192.168.5.0     *               255.255.255.0   U     0      0        0 p1p4
192.168.6.0     *               255.255.255.0   U     0      0        0 p3p1
```

---

### Post by fizgig on 2015-04-23
I've discovered the problem with the 6.* communication.  They were misconfigured to use an incorrect gateway.  They are all set up now.  Only problem I have is trying to figure out how to isolate these subnets from each other and only let them see the internet.

---

### Post by fizgig on 2015-04-23
I'm experimenting in just trying to block my ip address (192.168.1.238) from another IP I don't want to be able to get to (192.168.6.4) by adding the following line to before.rules but I'm still able to ping it just fine.

```
-A OUTPUT -s 192.168.1.238 -d 192.168.6.4 -j DROP
```

I've changed OUTPUT to INPUT or FORWARD and re-ran ufw disable/enable but no change.

---

### Post by Doug S on 2015-04-23
> **fizgig said:**
> I've discovered the problem with the 6.* communication.  They were misconfigured to use an incorrect gateway.  They are all set up now.Aghh... O.K. that makes sense.  > **fizgig said:**
> Only problem I have is trying to figure out how to isolate these subnets from each other and only let them see the internet.I am not sure about this, but and for example, to prevent p1p2 from communicating with the others try this:```
-A PREROUTING -i p1p2 -d 192.168.1.0/24 -j DROP
-A PREROUTING -i p1p2 -d 192.168.3.0/24 -j DROP
-A PREROUTING -i p1p2 -d 192.168.5.0/24 -j DROP
-A PREROUTING -i p1p2 -d 192.168.6.0/24 -j DROP
```If that works, then expand the concept to the other interfaces. I have not thought of a way to do it with less rules.

---

### Post by fizgig on 2015-04-23
I tried adding:

```
-A PREROUTING -i p1p1 -d 192.168.6.0/24 -j DROP
```

but I got an error when trying to enable ufw.  I then changed it to:

```
-A PREROUTING -i p1p1 -d 192.168.6.4 -j DROP
```

and there was no more error.  I chose 192.168.6.4 as a test as I'm currently pinging it now.  Still am so it wasn't blocked.

---

### Post by fizgig on 2015-04-23
I tried another version:

```
-A PREROUTING -i p1p1 -o p3p1 -j DROP
```

but I can't re-enable ufw with that in there - it throws an error.  By the way, this is inside the *nat section.  Is that what you wanted?

---

### Post by Doug S on 2015-04-23
> **fizgig said:**
> I'm experimenting in just trying to block my ip address (192.168.1.238) from another IP I don't want to be able to get to (192.168.6.4) by adding the following line to before.rules but I'm still able to ping it just fine.

```
-A OUTPUT -s 192.168.1.238 -d 192.168.6.4 -j DROP
```

I've changed OUTPUT to INPUT or FORWARD and re-ran ufw disable/enable but no change.Try FORWARD with that rule and try something other than "ping" your rule set (which for other readers, I have via PM) has a UFW bypass for "ping".

And, yes PREROTUTING is always in the nat stuff.

---

### Post by Doug S on 2015-04-23
I forgot that one cannot do filtering in the PREROUTING area.
You need to nuke the UFW stuff and then do it in the FORWARD chain (and this time I have turned on my beater test computer and checked the syntax). So same example:```
-A FORWARD -i p1p2 -d 192.168.1.0/24 -j DROP
-A FORWARD -i p1p2 -d 192.168.3.0/24 -j DROP
-A FORWARD -i p1p2 -d 192.168.5.0/24 -j DROP
-A FORWARD -i p1p2 -d 192.168.6.0/24 -j DROP
```

---


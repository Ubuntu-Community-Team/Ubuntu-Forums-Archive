---
title: "VLAN Routing Issue"
date: 2013-06-06
forum: Security
---

### Post by MikeMunn on 2013-06-06
I have two vLAN's with different IP ranges that I am trying to get to talk to each other. Let me explain.

vlan15 is our corporate network, it has a range of 10.10.15.1/24
vlan202 is our guest wireless, it has a range of 10.10.202.1/23

I have a server on vlan15 that serves as our exchange server, lets say it is 10.10.15.251

When users are connected to the corporate network and ping the DNS name for that server they see the 10.10.15.251 address.
When users are connected to our wireless network and ping the DNS name for that server they see our public IP and the server is unreachable.
When users are connected to our wireless network and ping the 10.10.15.251 address it is unreachable.

I understand the concept that we may need to address our DNS servers differently, but is there a reason why I would not be able to even ping that server by IP from the vlan202? How would I resolve that?

---

### Post by The Cog on 2013-06-06
Firstly, you need something that is connected to both networks, and which will forward packets between them. Let's call this the "VLAN router". It could be a box that you install, or it could be something that the IT department installs on the corporate network. If you use a Linux box for this, you will need to enable IP forwarding. Edit /etc/sysctl.conf for that setting.

Secondly, I assume that both networks already have routers on them, for routing to other parts of the network, and for routing out to the internet. The routers on both networks will be what is called the "default gateway" for their releveant networks. The default gateway is the router that all the PCs send their packets to when they need to send packets to non-local networks. Both of these routers must be configured to know how to reach the other network. So for instance, the default gateway on the corporate network must be told that do reach the wireless network 10.10.202.1/23, it must forward packets to your VLAN router. The wireless network router must similarly know to forward packets destined for the corporate network to the VLAN router. Only when both routers know how to reach the other network will you be able to make a connection between the two. Configuring these routes will involve logging into the routers and probably configuring a "static route" pointing to the other network via the VLAN router. How you configure static routes is different in every make of router, and of course you need admin login for them.

It sounds as though your wireless router is passing your DNS requests out to the internet for resolution. You might have to set up your own DNS server that knows about the corporate addresses, and only forwards non-corporate-domain requests out to the internet. That could be a project in its own right.

---

### Post by MikeMunn on 2013-06-06
Let me be more specific. Our entire network is routed through a Ubuntu Linux server. Single device using 4 NICs.

eth0 - WAN connection 1
eth1 - 10.10.1.10/16 - Plugged into switching network
eth2 - Secondary WAN connection.
eth3 - 10.10.200.1/24 vlan raw device - all vlan's are routed through this device, also plugged into switching network

I didn't set this specific network up, but I have replicated the network and have the same problem elsewhere.

---

### Post by The Cog on 2013-06-06
Assuming that the Linux server is the default gateway for everything, then all you should have to do to get IP connectivity is to enable IP forwarding. Edit /etc/sysctl.conf and find this line, and remove the # from the front. 
```
#net.ipv4.ip_forward=1
```
that will make sure it forwards next time it boots, but without booting you need to also issue this sequence of comands to turn forwarding on now:
```
sudo su
echo 1 > /proc/sys/net/ipv4/ip_forward
exit
```
And maybe check you are not blocking with iptables. This command will list the current ruleset:
```
sudo iptables -nvL
```
By default there are 3  ACCEPT policies and no other rules.

---

### Post by uRock on 2013-06-06
Not sure what brand switch you are using, but you may need to configure the f/a ports to their particular vlan, if you haven't already done so.

---

### Post by MikeMunn on 2013-06-07
All of those items are already done. Here is a copy of what I have in my iptables. I don't see anything, do you?

```
Chain INPUT (policy ACCEPT 607K packets, 68M bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC 00:1C:26:64:12:61
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC 60:33:4B:1D:12:08
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC 00:16:CB:B8:10:D8
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC 70:1A:04:4E:55:B7
  850 74376 ACCEPT     tcp  --  *      *       10.10.50.102         0.0.0.0/0           tcp dpt:56565
    0     0 ACCEPT     tcp  --  *      *       10.10.50.102         0.0.0.0/0           tcp dpt:22
    0     0 ACCEPT     tcp  --  *      *       10.10.50.102         0.0.0.0/0           tcp dpt:80
    0     0 ACCEPT     tcp  --  *      *       10.10.50.101         0.0.0.0/0           tcp dpt:80
   31  1512 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:56565
 4327  173K DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80

Chain FORWARD (policy DROP 1557K packets, 135M bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC 00:1C:26:64:12:61
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC 34:15:9E:76:53:BD
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC 00:1E:C2:B4:AA:83
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC 00:1C:B3:B7:DF:D9
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC 00:23:14:17:5D:70
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC 00:13:02:B6:8D:06
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC 00:26:BB:05:1A:77
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC 00:25:D3:E6:79:33
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC 60:33:4B:1D:12:08
    0     0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC 60:33:4B:1D:12:08
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC 00:26:08:E9:E5:78
 158K   97M ACCEPT     47   --  *      *       0.0.0.0/0            0.0.0.0/0
  14M   12G ACCEPT     all  --  eth0   eth1    0.0.0.0/0            0.0.0.0/0
  12M 2831M ACCEPT     all  --  eth1   eth0    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  vlan26 eth1    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  eth1   vlan26  0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  vlan26 eth5    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  eth5   vlan26  0.0.0.0/0            0.0.0.0/0
 128K   22M ACCEPT     all  --  vlan172 eth0    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  vlan172 eth2    0.0.0.0/0            0.0.0.0/0
 172K  163M ACCEPT     all  --  eth0   vlan172  0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  eth2   vlan172  0.0.0.0/0            0.0.0.0/0
 589K   83M ACCEPT     all  --  vlan199 eth0    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  vlan199 eth2    0.0.0.0/0            0.0.0.0/0
 908K  972M ACCEPT     all  --  eth0   vlan199  0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  eth2   vlan199  0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  vlan26 eth0    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  vlan26 eth2    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  eth0   vlan26  0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  eth2   vlan26  0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  vlan5  eth0    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  vlan5  eth2    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  eth0   vlan5   0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  eth2   vlan5   0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  vlan5  eth1    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  eth1   vlan5   0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  vlan173 eth0    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  vlan173 eth2    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  eth0   vlan173  0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  eth2   vlan173  0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  vlan201 eth0    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  vlan201 eth2    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  eth0   vlan201  0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  eth2   vlan201  0.0.0.0/0            0.0.0.0/0
  23M 4775M ACCEPT     all  --  vlan202 eth0    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  vlan202 eth2    0.0.0.0/0            0.0.0.0/0
  31M   34G ACCEPT     all  --  eth0   vlan202  0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  eth2   vlan202  0.0.0.0/0            0.0.0.0/0
 212K   20M ACCEPT     all  --  vlan205 eth0    0.0.0.0/0            0.0.0.0/0
 282K  323M ACCEPT     all  --  eth0   vlan205  0.0.0.0/0            0.0.0.0/0
 280K  126M ACCEPT     all  --  vlan206 eth0    0.0.0.0/0            0.0.0.0/0
 283K  216M ACCEPT     all  --  eth0   vlan206  0.0.0.0/0            0.0.0.0/0
28610 3600K ACCEPT     all  --  eth3   eth1    10.10.200.0/24       10.10.15.20
    0     0 ACCEPT     all  --  eth1   eth3    10.10.15.20          10.10.200.0/24
 1285  748K ACCEPT     all  --  eth3   eth1    10.10.200.0/24       10.10.50.102
    0     0 ACCEPT     all  --  eth1   eth3    10.10.50.102         10.10.200.0/24
    0     0 ACCEPT     all  --  eth3   eth1    10.10.200.0/24       10.10.50.104
    0     0 ACCEPT     all  --  eth1   eth3    10.10.50.104         10.10.200.0/24
    0     0 ACCEPT     all  --  eth3   eth1    10.10.200.0/24       10.10.50.65
    0     0 ACCEPT     all  --  eth1   eth3    10.10.50.65          10.10.200.0/24
    0     0 ACCEPT     all  --  eth3   eth1    10.10.200.0/24       10.10.15.21
    0     0 ACCEPT     all  --  eth1   eth3    10.10.15.21          10.10.200.0/24
    0     0 ACCEPT     all  --  eth3   eth1    10.10.201.0/24       10.10.0.0/16
    0     0 ACCEPT     all  --  eth1   eth3    10.10.0.0/16         10.10.201.0/24
    0     0 ACCEPT     all  --  eth3   eth1    10.10.200.0/24       10.10.109.0/24
    0     0 ACCEPT     all  --  eth1   eth3    10.10.109.0/24       10.10.200.0/24
    0     0 ACCEPT     all  --  eth3   eth1    10.10.109.0/24       10.10.50.102
    0     0 ACCEPT     all  --  eth1   eth3    10.10.50.102         10.10.109.0/24
    0     0 ACCEPT     all  --  eth3   eth1    10.10.109.0/24       10.10.15.0/24
    0     0 ACCEPT     all  --  eth1   eth3    10.10.15.0/24        10.10.109.0/24
    0     0 ACCEPT     all  --  vlan50 eth0    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  eth0   vlan50  0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  vlan50 eth1    0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  eth1   vlan50  0.0.0.0/0            0.0.0.0/0


```

I am not new to this, I have been working with this type of network for 10 years. I have never run in to an issue like this before. 

So to clarify, we have a Ubuntu server, our switches are configured correctly, on the Ubuntu server we are utilizing vlans. vlan5 cannot talk to vlan202.

---

### Post by The Cog on 2013-06-07
That's a long manually edited access list. However, the forwarding default policy is to drop, and there is no entry at all for vlan15. And no entry allowing vlan202 to or from vlan5. My guess is that you need to add some more iptables rules.

---

### Post by paperplate9 on 2013-06-09
Another thing you may want to check since you have multiple network interfaces is rp_filter (a sysctl somewhere in the eth conf sections). Disable that (I think set it to the value 2 for all interfaces) as a quick test.

rp_filter is reverse path filtering - if the box received a packet on an interface that, according to its current routing table, would've came in on another interface, packet is blocked. I can see this happening if that server has IP addresses on Network A and Network B, and a host on Network B is trying to ping the server's Network A IP. Because essentially what you are asking is to have a ping come in on Network B NIC, and have the reply go out of the Network A NIC.

---

### Post by MikeMunn on 2013-06-12
> **paperplate9 said:**
> Another thing you may want to check since you have multiple network interfaces is rp_filter (a sysctl somewhere in the eth conf sections). Disable that (I think set it to the value 2 for all interfaces) as a quick test.

rp_filter is reverse path filtering - if the box received a packet on an interface that, according to its current routing table, would've came in on another interface, packet is blocked. I can see this happening if that server has IP addresses on Network A and Network B, and a host on Network B is trying to ping the server's Network A IP. Because essentially what you are asking is to have a ping come in on Network B NIC, and have the reply go out of the Network A NIC.

In this case it is commented out, is that the same as setting it to: net.ipv4.conf.default.rp_filter=0 ?

---

### Post by paperplate9 on 2013-06-27
I had a box (wasn't Ubuntu though) where rp_filter was set to 1 by default. You can double check with a: sysctl -a | grep \.rp_filter

---


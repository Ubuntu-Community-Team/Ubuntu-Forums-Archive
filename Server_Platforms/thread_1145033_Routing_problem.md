---
title: "Routing problem"
date: 2009-05-01
forum: Server Platforms
---

### Post by whitewash on 2009-05-01
Hello, everyone!

I have a problem with routing on Ubuntu server (it also may be something I forgot to set up, but I couldn't figure out, what could be causing the problem.)

I have set up a virtual network on VMWare (WinXP host machine), that consists of one Ubuntu server (with two NICs - eth0 and eth1) and one WinXP client (with only one NIC). 
Eth0 is connected to the VMWare's NAT interface, so that the linux server can connect to the Internet via WMWare on my physical host  - for more detailed scheme, I have attached file drawing.PNG)
The Ubuntu server should provide routing for the WinXP client connected to eth1 interface. However, when I start tracert from the WinXP client, the trace stops on the client's gw (the Ubuntu server). 
So the client can connect (ping works as well) to the Ubuntu server via eth1, server can both ping and traceroute (eth1) the client, and connect (eth0) to the WMWare gw and the Internet itself, but the client can't "go" anywhere past the server. 
Does anyone have an idea what can be wrong there? I guess something is missing in the server configuration, but this is the first time I am attempting to do something like that, so I am likely to have overlooked something.

Routes on the server are following:

```
#> route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.1.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.2     0.0.0.0         UG    100    0        0 eth0
```

IP forwarding is enabled (/proc/sys/net/ipv4/ip_forward set to 1)

Iptables chains are empty with Accept as the default policy

screenshot of the client: see Clipboard1.jpg

---

### Post by koenn on 2009-05-01
> **whitewash said:**
>  when I start tracert from the WinXP client, the trace stops on the client's gw (the Ubuntu server). 
It would have been more informative if you showed what address you're trying to tracert.
I'm assuming you want internet connectivity for your virtual network. Ping all addresses along your route to the internet :
```
ping 10.0.1.1
ping 192.168.0.10
ping 192.168.0.2
ping <VMware host physical NIC>
ping <ADSL router LAN address>
ping <ADSL router WAN address>
ping <any internet server>
```

You probably need an additional route on the VMware host to tell it that 10.0.1.0/24 can be reached through 192.168.0.10, to provide a route for the replies. 

If your ADSL router is also doing NAT, the 2 consecutive address translations might be getting in the way as well. You might want to investigate the other VMware networking solutions.

---

### Post by whitewash on 2009-05-01
Hello, 
thanks for the reply :)

Actually, the only ping and traceroute that succeeds, is 10.0.1.1 and 192.168.0.10. (LAN - eth1 and WAN - eth0 interfaces of the ubuntu server.) Everything beyond that (even 192.168.0.2) fails (ping and tracert)

Server itself can connect to the internet, so I don't think there is a problem with "dual NAT"

---

### Post by kalinath on 2009-05-01
sorry , i m new to this.

---

### Post by koenn on 2009-05-01
> **whitewash said:**
> Hello, 
thanks for the reply :)

Actually, the only ping and traceroute that succeeds, is 10.0.1.1 and 192.168.0.10. (LAN - eth1 and WAN - eth0 interfaces of the ubuntu server.) Everything beyond that (even 192.168.0.2) fails (ping and tracert)

Server itself can connect to the internet, so I don't think there is a problem with "dual NAT"

your server is multi-homed, it has an address in 192.168.0.0/24 so it's reacheable by 192.168.0.2. your clients are in a separate net. Entirely different situation. 

How about that additional route on your vmware host ?

re. the routes on the server, did you add them manually or were they created automatically

---

### Post by whitewash on 2009-05-01
Route on VMWare host added, tracert initiated directly from VMWare host succeeds (tracing 10.0.1.10 from 192.168.0.2), tracing & pinging 192.168.0.2 from 10.0.1.10 still fails :(

Routes on the Linux server were created automatically.

---

### Post by koenn on 2009-05-01
Exactly what does  VMWare NATed networking do ? What address translation is happening there ?

---

### Post by whitewash on 2009-05-01
The VMWare NAT interface is translating vmware virtual network (192.168.0.0/24) to the physical one(192.168.1.0/24), the same way as ADSL router is translating my physical network to the Internet. There is no port forwarding to the virtual network configured on that NAT interface.

---

### Post by whitewash on 2009-05-03
Actually, what I was trying to do is to simulate the network setup, before going for it in the real environment. So, if the server was connected directly to the Internet gateway (e.g. ADSL router) and not the virtual VMWare NAT, having the same situation as pictured on the drawing, would this configuration be OK ?

---

### Post by koenn on 2009-05-03
> **whitewash said:**
> Actually, what I was trying to do is to simulate the network setup, before going for it in the real environment. So, if the server was connected directly to the Internet gateway (e.g. ADSL router) and not the virtual VMWare NAT, having the same situation as pictured on the drawing, would this configuration be OK ?

sort of.
your DSL router may have a similar problem your VMware host had : if a packet arrives that has to go (back) to 10.0.1.0/24, it wouldn't know how to reach that network unless it knows a (static) route, ie via 192.168.0.10
similar to post #6
If your router doesn't let you add routes, you can masquerade 10.0.1.0 on 192.168.0.10, but that's a workaround you'd like to avoid, it makes your network less transparent and troubleshooting can become a pain.

Speaking of which, I still think your original problem is related to the VMware NAT device. It's unclear what it masqs  : 192.168.0.0 only ? all virtual networks ? ... and how it does that. The documentation I found isn't conclusive, but the fact that you can route from the vmware host into the host-only network, but not in the opposite direction (where the NATing occurs) supports the hypothesis that it's the NAT getting in the way.

You can prove me wrong by switching from VMware NAT networking to Bridged networking, i.e. bridge ubuntu server's eth0 to the NIC in the VMware host. My bet is you'll then be able to communicate from 10.0.1.0/24 to your router's LAN interface and back. This is similar to what you want to do for real. The point about the extra route on your DSL router still stands.

---

### Post by whitewash on 2009-05-03
Yup, NAT is masqing only the 192.168.0.0/24, that subnet is reserved and automatically assigned by VMWare for NATing.

The whole VMWare networking is somehow strange, now I'm getting Destination unreachable when trying to ping anything (yes, they are both on the correct subnet).

Anyway, what is important for me, is making this work in the real environment. I know the router that will be used as the Internet gw, and it has a function to setup own static routes, so that shouldn't be a problem. It also has options to define firewall rules, so that way I can exactly define who can access which resources.

---

### Post by koenn on 2009-05-03
I've done similar things on VMware server, like routing and vpn tunnels between host-only networks and things like that. 
For access to the real world, I usually do bridging, because the bridged virtual interface then behaves as if it is on the real LAN. Makes things really simple, and life-like.

Found similar info in de VMware documentation :
[http://www.vmware.com/support/ws55/doc/ws_net_configurations_custom.html](http://www.vmware.com/support/ws55/doc/ws_net_configurations_custom.html)

They also have a routing howto, maybe it's worth a read
[http://www.vmware.com/support/ws55/doc/ws_net_advanced_2hostonly_routing.html](http://www.vmware.com/support/ws55/doc/ws_net_advanced_2hostonly_routing.html)

Your setup looks sound, so it will probably work in real life, but you should also be able to get it to work with virtual networks. You probably want to do your troubleshooting without the risk of getting e real network in trouble.

---

### Post by spooots on 2009-05-23
Hi!

 I have got the same problem with my non virtual setup. 

The Server is based on Ubuntu 8.04. eth0 is configured by my FRITZ!Box DHCP to 192.168.2.94 and eth1 configured by hand to 192.168.10.1,255.255.255.0. Routing is enabled at the server, too. I`ve got a DHCP Server running at the Server for eth1 that gives a connected Windows host the address 192.168.10.50.
 Up to this point everything is working fine (except routing). 

 I'm also able to ping the FRITZ!Box (at 192.168.2.1) and the Client from my server, and pinging the server from the client is working, too.

 My problem is, that pinging the FRITZ!Box with the client fails. I think there is also only a missing configuration issue, but I ca figure it out by myself.

 I was watching the Network traffic via WIRESHARK. The ping arrives at the server, but it is never routed to eth0.

 The standard routes are ok.
192.168.2.0 -> eth0
192.168.10.0 -> eth1
0.0.0.0 gw 192.168.2.1 -> eth0

 I already checked the iptables setup via iptables -L, but there everything seems to be fine and the three chain policies are set to ACCEPT.

 Perhaps anyone may help me with this problem. 

 I'm not able to give you the exact settings at the moment, but I will add them as soon as possible.

 Thanks, spooots

---

### Post by koenn on 2009-05-23
> **spooots said:**
> Hi!

Routing is enabled at the server, too. 

My problem is, that pinging the FRITZ!Box with the client fails.

I was watching the Network traffic via WIRESHARK. The ping arrives at the server, but it is never routed to eth0.

The standard routes are ok.

I already checked the iptables setup via iptables -L, but there everything seems to be fine and the three chain policies are set to ACCEPT.

I'm not able to give you the exact settings at the moment, but I will add them as soon as possible.


It is possible that the routing stops at the server, but then at leat one of the things you say is incorrect (i.e. routing is not enabled, iptables is blocking something or translating / mangling packets so that they become unroutable, ...)

show us the output of ```
cat /proc/sys/net/ipv4/ip_forward 
```
you may also need to show your running iptables setup :
```
 iptables -L -n -v 
 iptables -L -n -v -t nat
```


A more likely explanation is that your ping actually reaches the fritzbox, but you never receive a reply. 
If your fritz receives an echo request (ping) from 192.168.10.50, it will want to reply, so it needs to know how to reach the 192.168.10.0/24 network. Unless it knows a route to 192.168.10.0/24, it will send everything that isn't destined for 192.168.2.0/24 (its own local net) out through its default route, presumably towards the internet. So that's where the ping reply goes, and your windows client never gets to see it.

---

### Post by spooots on 2009-05-23
Thank you koenn for your quick answer. 
Your suggestion hits the problem. I tried the following set up now:
Instead of pinging the fritz-box I was sending a ping to a second windows client within the 192.168.2.0/24 network. Watching the traffic via WIRESHARK I detected, that the ping was routed correctly to my windows pc, but no answer could be received.
 Now I added a new route to the windows client by

route ADD 192.168.10.0 MASK 255.255.255.0 192.168.2.94

 and tried again. 
Now the ping works as expected.
Thanks again!

---

### Post by koenn on 2009-05-23
no problem. been there, done that, etc. and once you've done a few of these setups you usually know where to look if things don't work -.

Your "route add" solution is correct. The only problem you may have is that  192.168.2.94 is a dynamic address (dhcp) so if it ever should change, your route isn't correct anymore. It's probably best to manually configure eth0 as well, or pin the address with a dhcp reservation (if your fritzbox can do that)

---

### Post by totallynewbie on 2009-08-09
i'm using 8.04 as a router, and never succeed to connect two subnets.

sysctl -p said:
root@marlin:~# sysctl -p
kernel.printk = 4 4 1 7
kernel.maps_protect = 1
fs.inotify.max_user_watches = 524288
vm.mmap_min_addr = 65536
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.ip_forward = 1

and
route -n said:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.88.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.100.0   0.0.0.0         255.255.252.0   U     0      0        0 eth2
0.0.0.0         172.16.88.88    0.0.0.0         UG    100    0        0 eth1

what else that i need to do?

---


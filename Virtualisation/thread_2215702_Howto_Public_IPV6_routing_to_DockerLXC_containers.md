---
title: "Howto Public IPV6 routing to Docker/LXC containers"
date: 2014-04-07
forum: Virtualisation
---

### Post by kevzettler on 2014-04-07
I am using Ubuntu 13.10. I have a public pool of ipv6 address's provided by my
hosting provider Linode. The pool is 2600:3c01:e000:0083::/64 routed to 2600:3c01::f03c:91ff:fe6e:2563
I want to assign address from this pool to Docker/Lxc containers.
I have seen an tried several different methods from various blog posts online with no success.
Currently I am attempting to use radvd and a bridge interface. 
This setup seems to assign valid addresses to the containers from the pool,
however I cannot ping them from the host or Internet.


My setup currently looks like this..


On the Host


/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp
   up /sbin/ip -6 addr add 2600:3c01::f03c:91ff:fe6e:2563/64 dev eth0




iface eth0mvlan inet static
  address 192.168.1.1
  netmask 255.255.0.0
  pre-up ip link add eth0mvlan link eth0 type macvlan mode bridge

```


radvd.conf
```

interface eth0 {
MinRtrAdvInterval 3;
MaxRtrAdvInterval 10;
AdvSendAdvert on;
AdvLinkMTU 1480;
    prefix 2600:3c01:e000:0083::/64 {
        AdvOnLink on;
        AdvAutonomous on;
        AdvRouterAddr on;
    };
};


interface eth0mvlan {
MinRtrAdvInterval 3;
MaxRtrAdvInterval 10;
AdvSendAdvert on;
AdvLinkMTU 1480;
    prefix 2600:3c01:e000:0083::/64 {
        AdvOnLink on;
        AdvAutonomous on;
        AdvRouterAddr on;
    };
};

```


sysctl.conf
```
net.ipv6.conf.all.forwarding=1
```


ip -6 r
```

2600:3c01::/64 dev eth0  proto kernel  metric 256
fe80::/64 dev eth0  proto kernel  metric 256
fe80::/64 dev eth0mvlan  proto kernel  metric 256
fe80::/64 dev veth49fa  proto kernel  metric 256

```


route -6 -n 


```

Kernel IPv6 routing table
Destination                    Next Hop                   Flag Met Ref Use If
2600:3c01::/64                 ::                         U    256 0     0 eth0
fe80::/64                      ::                         U    256 0     0 eth0
fe80::/64                      ::                         U    256 0     0 eth0mvlan
fe80::/64                      ::                         U    256 0     0 veth49fa
::/0                           ::                         !n   -1  1    60 lo
::1/128                        ::                         Un   0   1   834 lo
2600:3c01::/128                ::                         Un   0   1     0 lo
2600:3c01::f03c:91ff:fe6e:2563/128 ::                         Un   0   1    52 lo
fe80::/128                     ::                         Un   0   1     0 lo
fe80::/128                     ::                         Un   0   1     0 lo
fe80::/128                     ::                         Un   0   1     0 lo
fe80::485c:1eff:fe43:a186/128  ::                         Un   0   1     0 lo
fe80::5c40:b6ff:fe81:8189/128  ::                         Un   0   1     0 lo
fe80::f03c:91ff:fe6e:2563/128  ::                         Un   0   1   262 lo
ff00::/8                       ::                         U    256 1     0 eth0
ff00::/8                       ::                         U    256 1     0 eth0mvlan
ff00::/8                       ::                         U    256 0     0 veth49fa
::/0                           ::                         !n   -1  1    60 lo

```


And then on a container...


ip -6 r
```

2600:3c01:e000:83::/64 dev eth0  proto kernel  metric 256  expires 86396sec
fe80::/64 dev eth0  proto kernel  metric 256
default via fe80::485c:1eff:fe43:a186 dev eth0  proto ra  metric 1024  expires 26sec

```


route -6 -n


```

Kernel IPv6 routing table
Destination                    Next Hop                   Flag Met Ref Use If
2600:3c01:e000:83::/64         ::                         UAe  256 0     0 eth0
fe80::/64                      ::                         U    256 0     0 eth0
::/0                           fe80::485c:1eff:fe43:a186  UGDAe 1024 0     0 eth0
::/0                           ::                         !n   -1  1     1 lo
::1/128                        ::                         Un   0   1     4 lo
2600:3c01:e000:83:d82a:c7ff:fe78:68e3/128 ::                         Un   0   1     0 lo
fe80::d82a:c7ff:fe78:68e3/128  ::                         Un   0   1     0 lo
ff00::/8                       ::                         U    256 1     0 eth0
::/0                           ::                         !n   -1  1     1 lo

```


This is all out side my realm of expertise so any input is much appreciated.

---

### Post by jasonvp on 2014-04-17
> **kevzettler said:**
> I am using Ubuntu 13.10. I have a public pool of ipv6 address's provided by my
hosting provider Linode. The pool is 2600:3c01:e000:0083::/64 routed to 2600:3c01::f03c:91ff:fe6e:2563


Hm.  Where did you get this IPv6 address from: **2600:3c01::f03c:91ff:fe6e:2563** ?  Is that something your provider told you to put on your machine?  Or is that their side of the IPv6 connection?  If it's something they told you to put on your machine, they're expecting your machine to act like an IPv6 router.  Which means: it needs to know what the *other* side of that IPv6 connection is.  Did they give you another IPv6 address to set as the router's default route?

> Currently I am attempting to use radvd and a bridge interface. 
This setup seems to assign valid addresses to the containers from the pool,
however I cannot ping them from the host or Internet.

Unless I misunderstood what you wrote in your post: it seems like your Linux server doesn't have an IPv6 address on the /64 you were assigned.  It needs an interface on that LAN, facing the VMs, such as **2600:3c01:e000:0083::1/64** or the like, so that the VMs can use that as their IPv6 default.  Their default will still show up as the link-local address of that interface, but you need a "real" IPv6 address on the LAN.

Also, you don't really want radvd listening and/or announcing RAs on eth0, if that's the interface you have connected to your provider.  You only want it running on the internal interface(s).


**PROVIDER** --------- *eth0*_**LINUX SERVER**_*eth0mvlan*------VMs

eth0: 2600:3c01::f03c:91ff:fe6e:2563/64
eth0mvlan: 2600:3c01:e000:0083::1/64

Missing from the config: your IPv6 gateway.

---

### Post by kevzettler on 2014-04-17
> [COLOR=#000000]Hm. Where did you get this IPv6 address from: [/COLOR]**2600:3c01::f03c:91ff:fe6e:2563 ? Is that something your provider told you to put on your machine? Or is that their side of the IPv6 connection? If it's something they told you to put on your machine, they're expecting your machine to act like an IPv6 router. Which means: it needs to know what the *other side of that IPv6 connection is. Did they give you another IPv6 address to set as the router's default route?***

[COLOR=#333333][FONT=arial]2600:3c01::f03c:91ff:fe6e:2563/64 is attached to my eth0 interface by default from my provider.


[/FONT][/COLOR]> [COLOR=#000000]Also, you don't really want radvd listening and/or announcing RAs on eth0, if that's the interface you have connected to your provider. You only want it running on the internal interface(s).[/COLOR]

Do I need to setup radvd for the interface on the VM side? 

Does the interface on the VM side have to be bridged?

Another point of interest. It seems like when I enable net.ipv6.conf.all.forwarding=1 I cannot ping any of my global ip addresses does that effect the ipv6 routing or something?

---

### Post by jasonvp on 2014-04-18
> **kevzettler said:**
> [COLOR=#333333][FONT=arial]2600:3c01::f03c:91ff:fe6e:2563/64 is attached to my eth0 interface by default from my provider.

OK.  Your Linux box still needs an IPv6 default route, and I don't see one in the previous post.  What's
```

netstat -nr -A inet6 | grep ::/0
```

return?

> [/FONT][/COLOR]Do I need to setup radvd for the interface on the VM side?

You need radvd to be running on any interface that client machines will be running on.  So in this case, yes, you want it running on the interface *facing* the VMs.

> Does the interface on the VM side have to be bridged?

Forget IPv6 for a moment.  How is your eth0 configured for IPv4?  Is its address publicly routable?  Are your VMs set up to NAT through the Linux server?

If the VMs are NATing through the Linux server, it means they're *routing* through it as well.  That means you don't want the interface on the VM side to be bridged.  You want it to be NATed or routed.  The same will apply to IPv6.  In this case, you won't NAT for v6, but you will route for it.

Does that make sense?

> Another point of interest. It seems like when I enable net.ipv6.conf.all.forwarding=1 I cannot ping any of my global ip addresses does that effect the ipv6 routing or something?

When you say "any of my global IP address," which addresses?  On which machine or machines?

---

### Post by kevzettler on 2014-04-18
> [COLOR=#333333][FONT=arial]OK. Your Linux box still needs an IPv6 default route, and I don't see one in the previous post. What's[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]Code:
netstat -nr -A inet6 | grep ::/0[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]return?[/FONT][/COLOR]

this is the return:

```
root@li166-218:~# netstat -nr -A inet6 | grep ::/0
::/0                           fe80::1                    UGDAe 1024 1     0 eth0
::/0                           ::                         !n   -1  1    62 lo
::/0                           ::                         !n   -1  1    62 lo

```


> [COLOR=#000000]Forget IPv6 for a moment. How is your eth0 configured for IPv4? Is its address publicly routable? Are your VMs set up to NAT through the Linux server?[/COLOR]

[COLOR=#000000]If the VMs are NATing through the Linux server, it means they're [/COLOR][I]routing through it as well. That means you don't want the interface on the VM side to be bridged. You want it to be NATed or routed. The same will apply to IPv6. In this case, you won't NAT for v6, but you will route for it.

Does that make sense?[/I]

Makes sense a bit. 

eth0 on IPV4 is configured to this public address 173.230.156.218 and is pingable from the web. It also has 2600:3c01::f03c:91ff:fe6e:2563/64 assigned to it.

The VMs get auto-configured when they are created. The VMS are managed by a daemon (docker.io) that attaches itsself to an interface. You can assign this daemon an interface or it will create one its self. By default the daemon creates a bridge interface and I think expects a bridge interface. The daemon then creates interfaces within the VMS that are ( I think ) Nat'd to the daemon interface.

> [COLOR=#000000]When you say "any of my global IP address," which addresses? On which machine or machines?[/COLOR]

The IPV6 assigned to eth0 that I listed above 2600:3c01::f03c:91ff:fe6e:2563/64 suddenly becomes unreachable when I enable [COLOR=#000000][I]net.ipv6.conf.all.forwarding=1
[/I][/COLOR]The same goes for any addresses from the pool of [COLOR=#333333][FONT=arial]2600:3c01:e000:0083::/64 that I assign to other virtual interfaces[/FONT][/COLOR]

---

### Post by jasonvp on 2014-04-19
> **kevzettler said:**
> ```
root@li166-218:~# netstat -nr -A inet6 | grep ::/0
::/0                           fe80::1                    UGDAe 1024 1     0 eth0
::/0                           ::                         !n   -1  1    62 lo
::/0                           ::                         !n   -1  1    62 lo

```


What about:
```

ping6 www.google.com
```

Basically I'm just verifying that your external IPv6 is all in order.  It doesn't seem like it from what I can see, but if you can ping GOOG's IPv6 addresses, then I'm incorrect.

> 
You can assign this daemon an interface or it will create one its self. By default the daemon creates a bridge interface and I think expects a bridge interface. The daemon then creates interfaces within the VMS that are ( I think ) Nat'd to the daemon interface.

It's *this* interface that you need to assign another IPv6 address to.  Specifically on the /64 that you want your VMs to exist on.  So assign it an address of **[COLOR=#333333][FONT=arial]2600:3c01:e000:0083::1/64[/FONT][/COLOR]**[COLOR=#333333][FONT=arial], and then make sure radvd is *only* listening and attached to that interface.  Once you have that set up, kick your VMs and see if they autoconfig problem.  Don't worry about:
[/FONT][/COLOR]> when I enable [COLOR=#000000]*net.ipv6.conf.all.forwarding=1*[/COLOR]
Yet.  Let's just worry about getting the VMs autoconfiging properly, and make sure your physical server can ping outwards.

---

### Post by kevzettler on 2014-04-19
Thanks for all the help!

> [COLOR=#000000]Basically I'm just verifying that your external IPv6 is all in order. It doesn't seem like it from what I can see, but if you can ping GOOG's IPv6 addresses, then I'm incorrect.[/COLOR]


```
root@li166-218:~# ping6 www.google.com
PING www.google.com(pd-in-x6a.1e100.net) 56 data bytes
64 bytes from pd-in-x6a.1e100.net: icmp_seq=1 ttl=53 time=24.2 ms
64 bytes from pd-in-x6a.1e100.net: icmp_seq=2 ttl=53 time=24.2 ms
64 bytes from pd-in-x6a.1e100.net: icmp_seq=3 ttl=53 time=24.2 ms
64 bytes from pd-in-x6a.1e100.net: icmp_seq=4 ttl=53 time=24.2 ms

```

> [COLOR=#000000]It's [/COLOR]*this interface that you need to assign another IPv6 address to. Specifically on the /64 that you want your VMs to exist on. So assign it an address of **[COLOR=#333333][FONT=arial]2600:3c01:e000:0083::1/64[/FONT][/COLOR][COLOR=#333333][FONT=arial], and then make sure radvd is [I]only* listening and attached to that interface. Once you have that set up, kick your VMs and see if they autoconfig problem. Don't worry about:[/FONT][/COLOR]**[/I]

On the host:

```


$bash ip -6 addr add 2600:3c01:e000:0083::1/64 dev br0

br0       Link encap:Ethernet  HWaddr 56:84:7a:fe:97:99
          inet addr:172.17.42.1  Bcast:0.0.0.0  Mask:255.255.0.0
          inet6 addr: fe80::5484:7aff:fefe:9799/64 Scope:Link
          inet6 addr: 2600:3c01:e000:83::1/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:379 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:29656 (29.6 KB)  TX bytes:46490 (46.4 KB)


eth0      Link encap:Ethernet  HWaddr f2:3c:91:6e:25:63
          inet addr:173.230.156.218  Bcast:173.230.156.255  Mask:255.255.255.0
          inet6 addr: fe80::f03c:91ff:fe6e:2563/64 Scope:Link
          inet6 addr: 2600:3c01::f03c:91ff:fe6e:2563/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2913 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1924 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:252887 (252.8 KB)  TX bytes:263594 (263.5 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


On The VM. Looks like it has a proper Global address

```

eth0      Link encap:Ethernet  HWaddr 96:df:17:fe:5d:b2
          inet addr:172.17.0.2  Bcast:0.0.0.0  Mask:255.255.0.0
          inet6 addr: 2600:3c01:e000:83:94df:17ff:fefe:5db2/64 Scope:Global
          inet6 addr: fe80::94df:17ff:fefe:5db2/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:61 errors:0 dropped:2 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8503 (8.5 KB)  TX bytes:4987 (4.9 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```


Back on the host checking VM connectivity

```
root@localhost:~# ping6 fe80::94df:17ff:fefe:5db2%br0
PING fe80::94df:17ff:fefe:5db2%br0(fe80::94df:17ff:fefe:5db2) 56 data bytes
64 bytes from fe80::94df:17ff:fefe:5db2: icmp_seq=1 ttl=64 time=0.154 ms
64 bytes from fe80::94df:17ff:fefe:5db2: icmp_seq=2 ttl=64 time=0.083 ms
^C
--- fe80::94df:17ff:fefe:5db2%br0 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.083/0.118/0.154/0.037 ms
root@localhost:~# ping6 2600:3c01:e000:83:94df:17ff:fefe:5db2
PING 2600:3c01:e000:83:94df:17ff:fefe:5db2(2600:3c01:e000:83:94df:17ff:fefe:5db2) 56 data bytes
64 bytes from 2600:3c01:e000:83:94df:17ff:fefe:5db2: icmp_seq=1 ttl=64 time=0.134 ms
64 bytes from 2600:3c01:e000:83:94df:17ff:fefe:5db2: icmp_seq=2 ttl=64 time=0.089 ms
64 bytes from 2600:3c01:e000:83:94df:17ff:fefe:5db2: icmp_seq=3 ttl=64 time=0.108 ms
64 bytes from 2600:3c01:e000:83:94df:17ff:fefe:5db2: icmp_seq=4 ttl=64 time=0.101 ms

```

Pinging the VM from the web
```

[COLOR=#000000]core1.fmt2.he.net> ping ipv6 2600:3c01:e000:83:94df:17ff:fefe:5db2 numeric count 5[/COLOR]  Sending 5, 16-byte ICMPv6 Echo to 2600:3c01:e000:83:94df:17ff:fefe:5db2
timeout 5000 msec, Hop Limit 64
Request timed out.
Request timed out.
Request timed out.
Request timed out.
Request timed out.
No reply from remote host.
# Entry cached for another 34 seconds.
```

---

### Post by jasonvp on 2014-04-20
> **kevzettler said:**
> Pinging the VM from the web
```

[COLOR=#000000]core1.fmt2.he.net> ping ipv6 2600:3c01:e000:83:94df:17ff:fefe:5db2 numeric count 5[/COLOR]  Sending 5, 16-byte ICMPv6 Echo to 2600:3c01:e000:83:94df:17ff:fefe:5db2
timeout 5000 msec, Hop Limit 64
Request timed out.
Request timed out.
Request timed out.
Request timed out.
Request timed out.
No reply from remote host.
# Entry cached for another 34 seconds.
```

OK.  What if you traceroute6 to your VM from an external source?  Does it end at the Linux server's interface?  When I do it from my house it never gets that far.  When I traceroute6 to your Linux server's eth0, I do make it.

That seems to indicate to me that your provider isn't routing the /64 that your VMs are on to you properly.  Even if your machine wasn't configured to route properly, the traceroute6 should still make it as far as your Linux server and then die.

---

### Post by kevzettler on 2014-04-20
> [COLOR=#000000]OK. What if you traceroute6 to your VM from an external source? Does it end at the Linux server's interface? When I do it from my house it never gets that far. When I traceroute6 to your Linux server's eth0, I do make it.[/COLOR]

Here are two traceroutes. One is to the ip address on the br0 interface that I added manually [COLOR=#000000]2600:3c01:e000:83::1 
[/COLOR]The second traceroute is to the VM interface that has the auto configured address of [COLOR=#000000]2600:3c01:e000:83:94df:17ff:fefe:5db2 
[/COLOR]Both traceroutes touch the address of [COLOR=#000000]2001:470:1:3b8::2 which I believe is Linode's router. [/COLOR]

```
core1.fmt2.he.net> traceroute ipv6 2600:3c01:e000:83::1 numeric
  
Tracing the route to IPv6 node 2600:3c01:e000:83::1 from 1 to 30 hops

  1    21 ms    1 ms   <1 ms 2001:470:0:30::2
  2    <1 ms   <1 ms   <1 ms 2001:470:0:263::1
  3     1 ms    1 ms    1 ms 2001:470:1:3b8::2
  4     1 ms   <1 ms   <1 ms 2600:3c01:e000:83::1
# Entry cached for another 59 seconds.
```


```
core1.fmt2.he.net> traceroute ipv6 2600:3c01:e000:83:94df:17ff:fefe:5db2 numeric
  
Tracing the route to IPv6 node 2600:3c01:e000:83:94df:17ff:fefe:5db2 from 1 to 30 hops

  1    13 ms    1 ms   <1 ms 2001:470:0:30::2
  2    <1 ms   <1 ms   <1 ms 2001:470:0:263::1
  3     1 ms    1 ms    1 ms 2001:470:1:3b8::2
  4    *       *       *     ?
  5    *       *       *     ?
  6    *       *       *     ?
  7    *       *       *     ?
IP: Errno(8) Trace Route Failed, no response from target node.

# Entry cached for another 34 seconds.
```

A few things things of concern for me at this point.

I'm currently using the default bridge interface that the VM managment daemon creates on startup. I think this also creates some iptable rules that might affect routing. I'm not sure how to confirm or diagnosis this.

I'm not currently using the [I]net.ipv6.conf.all.forwarding=1 setting I don't know if that would change things.
[/I]
[FONT=arial]Is it possible that my providers firewall is blocking the ipv6 host discovery protocol? How would I confirm?[/FONT]

---

### Post by jasonvp on 2014-04-21
> **kevzettler said:**
> I'm currently using the default bridge interface that the VM managment daemon creates on startup. I think this also creates some iptable rules that might affect routing. I'm not sure how to confirm or diagnosis this.

Running the command```
ip6tables -L
```
will list any iptables set up for IPv6 specifically.  I wouldn't necessarily post the output of that command to the forums were I you, but that's just the security wonk in me speaking.

> I'm not currently using the net.ipv6.conf.all.forwarding=1 setting I don't know if that would change things.

It absolutely will matter and does need to be set to 1 in order to be an IPv6 router.  I just wanted to verify that the infrastructure was all configured properly before enabling it; baby steps as it were.

---


---
title: "OpenVPN problems"
date: 2006-12-11
forum: Server Platforms
---

### Post by tamiral on 2006-12-11
Hi,
New to this forum as an active participant but used it a lot as a knowledgebase to many problems I've had over the years...

Been trying to set up an OpenVPN server/client between my home network and my office network.

The link between the home and office networks are mainly for testing purposes.
Once this connection is up and running, I will distribute the client configuration files to our employees so they could connect from abroad or from their home networks to the office network.

Since some of our employees here are traveling abroad on business, I chose the "Road Warrior" configuration. I read somewhere that the suggested configuration for this kind of setup is the Bridged mode (instead of the routing one).

Passed the certificates stage, but this is where it ends.

The only thing I can think of is the subnet issue.
I've 192.168.1.0 at home and 192.168.0.0 at work.
Is there any way to pass this problem without changing subnet at home?

Thanks!

---

### Post by chrisfay on 2006-12-11
> I've 192.168.1.0 at home and 192.168.0.0 at work.
Is there any way to pass this problem without changing subnet at home?

Can you describe your problem a bit more? The two subnets differ and shouldn't be conflicting.

---

### Post by tamiral on 2006-12-26
Sorry it took me so long... 

Let me clarify this:

I have 192.168.1.0/24 at home (ranging from 192.168.1.0-192.168.1.255) - Client side
and 192.168.0.0/16 at work (ranging from 192.168.0.0-192.168.255.255) - Server side

This creates an IP conflict whenever the client wants to talk to, say, 192.168.1.15
This IP is up on both the Client and the Server networks.
As far as I know, there's no way to fix this conflict using a custom routing table.

Must I change one of the subnets in a way they won't conflict in order to get the 
OpenVPN connection to work?

---

### Post by druhboruch on 2006-12-26
I think that your configuration shuld work without reconfiguring subnets on eather side.

It is very easy to confirm this assumption:  just install Ipcop and Zerina OpenVpn plugin.

---

### Post by tamiral on 2006-12-27
I will.
Thanks.

Eventually decided to go with a routed OpenVPN solution. 
It suppose to be easier to config.

Let me ask you this:
I've passed all the authentication procedures, and I have "Initialization Sequence Completed" on both sides.

As I mentioned before, I have 192.168.0.0/24 at home. My Tun interface looks like this (Client side):
```

ifconfig tun0

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
             inet addr:10.8.0.6  P-t-P:10.8.0.5  Mask:255.255.255.255
             UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
             RX packets:10 errors:0 dropped:0 overruns:0 frame:0
             TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:100
             RX bytes:748 (748.0 b)  TX bytes:818 (818.0 b)

```
and my routing table looks like this:
```

tamiral@christopher:~$ ip route
10.8.0.5 dev tun0  proto kernel  scope link  src 10.8.0.6
10.8.0.1 via 10.8.0.5 dev tun0
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.200
192.168.0.0/16 via 10.8.0.5 dev tun0
default via 192.168.1.1 dev eth0

```

At work, I have 192.168.0.0/16, and my tun0 interface looks like this:

```

hotrtr:~# ifconfig tun0

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
             inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
             UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
             RX packets:15 errors:0 dropped:0 overruns:0 frame:0
             TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:100
             RX bytes:1070 (1.0 KiB)  TX bytes:1000 (1000.0 b)

```

My routing table (server side) looks like this (nevermind those unrelated):
```

hotrtr:~# ip route

10.8.0.2 dev tun0  proto kernel  scope link  src 10.8.0.1
10.150.150.128/30 dev eth1  proto kernel  scope link  src 10.150.150.130
80.74.119.64/28 dev eth1  proto kernel  scope link  src 80.74.119.64
10.8.0.0/24 via 10.8.0.2 dev tun0
192.168.0.0/16 dev eth0  proto kernel  scope link  src 192.168.1.6
default via 10.150.150.129 dev eth1  src 10.150.150.130

```

BTW: I've enabled push "route 192.168.0.0 255.255.0.0" on server side.

Is it alright that even though I have no 10.0.0.0 subnet what so ever, I still have those IPs on my tun interface? shouldn't it be 192.168.1.x P-t-P 192.168.1.y?
Is it OK that the P-t-P settings don't match (10.8.0.6 P-t-P 10.8.0.5 at home and 10.8.0.1 P-t-P 10.8.0.2 at work)? shouldn't they match?

I can ping 10.8.0.1 from home and I can ping 10.8.0.6 from work, but that's it.
Nothing else gets pinged...

What am I doing wrong here???

PS sorry for being so long...

---

### Post by tamiral on 2007-01-02
OK,
At last all is working well!

I've downloaded couple of example configuration files (server/client) and changed the them to fit to my configuration.

I still have a problem with my routing table though,
Since I have 192.168.0.0/24 at home and 192.168.0.0/16 at work, 
whenever I'm trying to ping 192.168.1.13, for example (doesn't exist at home, only at work),
the interface used is eth0 instead of tun0.
I'm verifying this using traceroute.

How can I fix that?

---

### Post by dom on 2007-03-01
You could move your home network to 172.16.0.0 or 10.0.0.0, or to IPV6, right ?

You could probably also move your home network from 192.168.0.0/24 to 192.168.x.0/24, where x is some number, 1 to 254, and hopefully isn't used at your work.

---


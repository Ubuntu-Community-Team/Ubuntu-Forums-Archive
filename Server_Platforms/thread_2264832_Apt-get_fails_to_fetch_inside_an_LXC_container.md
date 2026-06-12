---
title: "Apt-get fails to fetch inside an LXC container"
date: 2015-02-10
forum: Server Platforms
---

### Post by cmavr8 on 2015-02-10
Hi, I have problems with apt-get failing to fetch (getting lots of 404's) on a 14.04.1 linux container running on a 14.04.1 server.

I've described the issue a week ago in askubuntu.com, but no one has replied or commented, so I thought I'd try here too.

The system can ping the servers that it cannot get packages from. I tried changing sources.list, removing all the /var/lib/apt/lists and partial folders, as most people suggest, but nothing helped. No firewall is running on the host, and networking works fine in the container otherwise (it can both see and be seen by internet hosts).

The strange thing is apt-get works right after a host restart, but it is not possible to restart the whole server everytime one container needs to install/update something.

More info can be found [here]("http://askubuntu.com/questions/581102/apt-get-fails-to-fetch-inside-an-lxc-container").

Any recommendations are welcome!

Thanks,
Chris

PS: I posted this here and not in LXC forums/lists because it feels like an ubuntu issue, and not directly related to LXC. If, though, you think I should have done it differently, please let me know.

---

### Post by TheFu on 2015-02-10
NAT or bridged?
Did you manually create the bridge settings or are you using sometimes-never-works built-in bridge?
Also, have you validated all the network and routing makes sense?

---

### Post by cmavr8 on 2015-02-11
Thanks for your reply

Yes, I'm using the built-in bridge :( It was supposed to just work (on ubuntu) but seems like it's causing me the problems.

Yeap routing seems ok to me:

```
root@host# ip route show
default via 192.168.1.1 dev eth0 
10.0.3.0/24 dev lxcbr0  proto kernel  scope link  src 10.0.3.1 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.100 
```

```
root@container# ip route show
default via 10.0.3.1 dev eth0 
10.0.3.0/24 dev eth0  proto kernel  scope link  src 10.0.3.252
```

Shoudl I just man up and build the bridge myself? :P

EDIT: now that I think about it, it's neither bridged nor simply NAT. There's a bridge for all the containers, and that is NATed in relation to the host's network (192.168.1.0). Then another NAT to the outside world (internet connection).

---

### Post by TheFu on 2015-02-11
The automatic LXC networking is NAT, so if you want the outside to get to it, you'll have to foreword those ports manually. I just use bridged networks on the same subnet as the rest of my systems.
Manually created Linux bridges just work. They don't have performance issues (do have security issues) and I wouldn't use any containers on the internet, but for developers and internal-only servers, containers are great!

I'm not familiar with ip output. When they take away route, netstat, ifconfig, then I'll switch. ;) Of course, I've hear of it and played with it a few times. Don't see the point. It is like Unity, systemd, Gnome3 ... don't see the point.

The setting to control which bridge is used for a container is in the container config file. It is pretty easy to find and fix.

---

### Post by cmavr8 on 2015-02-11
> **TheFu said:**
> The automatic LXC networking is NAT, so if you want the outside to get to it, you'll have to foreword those ports manually. 
That's not a problem. I have that working already, and I like this layer of security.

> **TheFu said:**
> 
I just use bridged networks on the same subnet as the rest of my systems.
Manually created Linux bridges just work. They don't have performance issues (do have security issues) and I wouldn't use any containers on the internet, but for developers and internal-only servers, containers are great!
well, this container may have a couple of publicly available services, but not http servers or anything else widely accessible. Still, I don't like the approach of bridging. Too much fusing of the containers. I like NAT in theory. If it worked.

I started using these instructions, to transition from nat to bridge, but I stopped once I realized what I was about to do.
```
Disable default lxcbr0 in /etc/default/lxc
Make sure bridge-utils is installed
# apt-get install bridge-utils
Edit /etc/network/interfaces
You should have a line that says:
auto eth0 (not sure if this is necessary but I would think so in order to make sure eth0 comes up)

Edit /etc/network/interfaces and add:

auto br0
iface br0 inet static
bridge_ports eth0
bridge_fd 0
address 192.168.1.### (Host IP not ###)
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

This is the part that confuses people. The eth0 interface will NOT have an IP. It will simply be up. All traffic on the host will actually start routing through br0 with eth0 being the PORT (means of pkt transport). Unless you are using some sort of advanced config then eth0 should just be up but with no settings attached to it.
```
[source]("https://www.stgraber.org/2013/12/20/lxc-1-0-your-first-ubuntu-container/")

> **TheFu said:**
> 
I'm not familiar with ip output. When they take away route, netstat, ifconfig, then I'll switch. ;) Of course, I've hear of it and played with it a few times. Don't see the point. It is like Unity, systemd, Gnome3 ... don't see the point.

Haha I don't use it either! I'm just trying to switch to it, so when I post I refrain from using ifconfig etc :P :P :P

> **TheFu said:**
> The setting to control which bridge is used for a container is in the container config file. It is pretty easy to find and fix.
I know... easy yes. But still, can't I make NAT work?

So here we are:
```
root@host# ifconfig
eth0      Link encap:Ethernet  HWaddr <masked>  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: <masked> Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14855477 errors:7504 dropped:7677 overruns:7504 frame:0
          TX packets:8052722 errors:0 dropped:0 overruns:6 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20791849637 (20.7 GB)  TX bytes:762322169 (762.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89252 (89.2 KB)  TX bytes:89252 (89.2 KB)

lxcbr0    Link encap:Ethernet  HWaddr <masked> 
          inet addr:10.0.3.1  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: <masked> Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7712722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14507638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:606790366 (606.7 MB)  TX bytes:20577277664 (20.5 GB)

veth7HR5YG Link encap:Ethernet  HWaddr <masked>
          inet6 addr: <masked> Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1289 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:262732 (262.7 KB)  TX bytes:480386 (480.3 KB)

vethCSBEXI Link encap:Ethernet  HWaddr <masked>
          inet6 addr: <masked> Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7717787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14512609 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:718376462 (718.3 MB)  TX bytes:20577176074 (20.5 GB)

vethKQXBFS Link encap:Ethernet  HWaddr <masked> 
          inet6 addr: <masked> Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1134159 (1.1 MB)  TX bytes:2408611 (2.4 MB)

```

```
root@container# ifconfig
eth0      Link encap:Ethernet  HWaddr <masked>  
          inet addr:10.0.3.252  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: <masked>  Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:480386 (480.3 KB)  TX bytes:262732 (262.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---


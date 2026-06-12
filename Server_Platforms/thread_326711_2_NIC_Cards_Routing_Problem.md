---
title: "2 NIC Cards Routing Problem"
date: 2006-12-28
forum: Server Platforms
---

### Post by igb on 2006-12-28
I have two NIC in myserver eth0 and eth1. The objective is to use eth0 for local network traffic and have eth1 route via my ADSL router to the Internet. I am using Firehol to define my firewall/routing rules.

/etc/interfaces is set up as:

```
auto eth1
iface eth1 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        # dns-nameservers 192.168.0.15

auto eth0
iface eth0 inet static
        address 192.168.0.15
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        #gateway 192.168.1.2
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.15

```

My firehol.conf is:

```
# transparent_squid 3128 "proxy proxy" inface eth0

# Accept all client traffic on any interface
#interface any world
 #       client all accept

interface eth0 home
        server dns      accept
        server ftp      accept
        server samba    accept
        server squid    accept
        server http     accept
        server ssh      accept
        server icmp     accept
        server "imap imaps smtp"        accept

        client all      accept

interface eth1 internet
        protection      strong
        server smtp     accept
        server http     accept
     server ftp      accept

        client all      accept

router home2internet inface eth0 outface eth1
        masquerade
        client all accept
        route all accept


```

The output of route -n:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
```

I have edited sysctl.conf:

```
# Uncomment the next line to enable packet forwarding for IPv4
net/ipv4/ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
net/ipv6/ip_forward=1
```


The problem is that the system won't route. I can ping 192.168.1.2, but not 192.168.1.1 (my ADSL router). Looking at the output of the route -n command it seems that the default gateway for eth0 is 192.168.0.1 is this the cause of the routing problem?

Ian.

---

### Post by chrisfay on 2006-12-28
Why do you have your 'gateway' commented out for eth0? It's defaulting to the subnet of that interface until you specify otherwise.

---

### Post by igb on 2006-12-28
> **chrisfay said:**
> Why do you have your 'gateway' commented out for eth0? It's defaulting to the subnet of that interface until you specify otherwise.

Because I am an idiot:) However, setting the gateway to 192.168.0.15 doesn't improve things. I can ping 192.168.1.2 from the 192.168.0.x net, but I can't ping my router at 192.168.1.1.

Ian.

---

### Post by chrisfay on 2006-12-28
Wouldn't you want your gateway for eth0 to be 192.168.1.2? Then add a route for your 192.168.0.x subnet to eht1. This would direct any request for 192.168.0.x to your LAN subnet and the rest out to 192.168.1.1 (WAN) I could be wrong, its a bit late here.

This is a good guide for grasping routing tables and such...[http://lartc.org/howto/](http://lartc.org/howto/)  (It's not Ubuntu specific, but has good info)

---

### Post by igb on 2006-12-28
> **chrisfay said:**
> Wouldn't you want your gateway for eth0 to be 192.168.1.2? Then add a route for your 192.168.0.x subnet to eht1. This would direct any request for 192.168.0.x to your LAN subnet and the rest out to 192.168.1.1 (WAN) I could be wrong, its a bit late here.


That's what I thought, but I get a Network Unreachable" error when I restart the network.

Ian.

---

### Post by chrisfay on 2006-12-28
Did you manually add a route to eth1 that directs all 192.168.0.x traffic through eth0?

---

### Post by igb on 2006-12-28
> **chrisfay said:**
> Did you manually add a route to eth1 that directs all 192.168.0.x traffic through eth0?

No. However, I have made a little progress. If I set the default gateway for eth0 to 192.168.1.2 then reboot my routing table now looks like:

192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.2
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.15
default via 192.168.1.1 dev eth1

I can ping eth1 (192.168.1.2) OK from a workstation, but any attempt to ping the router (192.168.1.1) results in "Network unreachable".

Ian.

---

### Post by chrisfay on 2006-12-28
Here's a diagrammed explination of exactly what you're trying to accomplish...

[How to configure routing of two NICs on a PC]("http://www.fiberlogic.info/Frequently_Asked_Questions/FAQs/How_to_configure_routing_of_two_NICs_on_a_PC?/")

It may help visualize it...

---

### Post by igb on 2006-12-28
Finally found the problem. While in grasping at straws mode I ran lspci -v, thinking there might be a problem with on of the network cards. I noticed that my on board ethernet had somehow got enabled. For various reasons I had disabled it in the BIOS and stuck in 2 Netgear cards.

eth1 was in fact the on board ethernet, which had nothing plugged into it. Disabling it in the BIOS and rebooting magically fixed the problem:)

For the record here is my working network config:

auto eth1
```
iface eth1 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        # dns-nameservers 192.168.0.15

auto eth0
iface eth0 inet static
        address 192.168.0.15
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.1.2
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.15

```

Output of route -n:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

```

Thanks for all your help and the various links, which have given me lots of useful info.

Ian.

---

### Post by chrisfay on 2006-12-28
Excellent!

Glad you got it working....

---


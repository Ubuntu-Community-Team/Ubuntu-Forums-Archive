---
title: "What's a gateway? (LAN out to WAN)"
date: 2007-11-01
forum: Server Platforms
---

### Post by juantao on 2007-11-01
Cross posted. This has been sitting on Networking unanswered for 4 hours, maybe some one here could help me (?)

= = = = =

Sorry, I know this has been answered here (and elsewhere) many times, but I just don't get it.

I have a server which is working correctly. Several domains are hosted on it, I can ftp to and from it and I can connect to it via ssh. All of this works using eth0

I am trying to set up a LAN on eth1 and parts of it are working. I can pull an IP address from my DHCP server, but I don't understand how to get hosts on the LAN to connect to the Internet. Maybe the concepts of a gateway and routing have yet to be explained simply enough to me.

I know I'll have to set up NAT to actually surf from my LAN to the outside world, but I big step forward for me, would be if I could at least ping anything other than 192.168.7.2

(The narrow range (192.168.7.41 1 192.168.7.49) was created so I could be sure I was seeing my DHCP server, not confusing it with any others.)

Here's some info from my computer.
= = = = =
/etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary (WAN) network interface
auto eth0
iface eth0 inet static
address 69.9.146.99
netmask 255.255.255.0
network 69.9.146.0
broadcast 69.9.146.255
gateway 69.9.146.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 69.9.129.9 4.2.2.1 66.241.64.10
dns-search dsl.mind.net

# The secondary (LAN) network interface
auto eth1
iface eth1 inet static
address 192.168.7.2
netmask 255.255.255.0

= = = = =
me@myhost:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:60:08:11:F0:A9
inet addr:69.9.146.99 Bcast:69.9.146.255 Mask:255.255.255.0
inet6 addr: fe80::260:8ff:fe11:f0a9/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:38059 errors:0 dropped:0 overruns:0 frame:0
TX packets:21783 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:4991429 (4.7 MB) TX bytes:8304286 (7.9 MB)
Interrupt:16 Base address:0xd400

eth1 Link encap:Ethernet HWaddr 00:19:5B:6A:1D:E7
inet addr:192.168.7.2 Bcast:192.168.7.255 Mask:255.255.255.0
inet6 addr: fe80::219:5bff:fe6a:1de7/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:28 errors:0 dropped:0 overruns:0 frame:0
TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:4237 (4.1 KB) TX bytes:1314 (1.2 KB)
Interrupt:17

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2088 errors:0 dropped:0 overruns:0 frame:0
TX packets:2088 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:779117 (760.8 KB) TX bytes:779117 (760.8 KB)

= = = = =
me@myhost:~$ route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.7.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
69.9.146.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
0.0.0.0 69.9.146.1 0.0.0.0 UG 100 0 0 eth0
= = = = =
/etc/dhcp3/dhcpd.conf
#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers 69.9.129.9, 4.2.2.1;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the
# DHCP server to understand the network topology.

subnet 192.168.7.0 netmask 255.255.255.0 {
range 192.168.7.41 192.168.7.49;
}
= = = = =

---

### Post by PilotJLR on 2007-11-01
In addition to turning on NAT, you need to enable IP forwarding by uncommenting the following line in /etc/sysctl.conf
```

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.conf.default.forwarding=1

```

then either reboot or sudo sysctl -p to make the changes take effect.



But that is not enough! Then you need to setup NAT in iptables... have you already done anything with iptables? Could you post iptables -L -v

---

### Post by juantao on 2007-11-01
I have not done anything with iptables yet. Please advise.

---

### Post by PilotJLR on 2007-11-01
This should be what you need to do NAT:

```

iptables -t nat -A POSTROUTING -s 192.168.7.0/24 -o eth0 -j MASQUERADE

```

After this plus the ip forwarding switch, see if you can ping the IP ADDRESS of a website. THen try domain names to test DNS

---


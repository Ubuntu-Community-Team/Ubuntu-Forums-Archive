---
title: "Using ebtables to drop packets out of bridge and route via Tinc VPN"
date: 2013-05-21
forum: Server Platforms
---

### Post by TomUK on 2013-05-21
[COLOR=#000000][FONT=Arial]We posted this on Server Fault yesterday and so far haven't had any feedback so we thought we should try posting it here as well.

We have a bridge set up on Ubuntu (12.04.2 64 bit) to link our LAN to our gateway which is on the same subnet. We need this to be able to control the traffic and are not currently in a position to change subnets so we can't just route it instead.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The gateway is controlled via our ISP who provide MPLS to various other /24 subnets within 192.168.0.0/16.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The current set up is as follows:
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Arial]192.168.10.1 (gw) <-> eth0 <-> br0 (192.168.10.3) <-> eth1 <-> LAN (192.168.10.0/24)[/FONT][/COLOR]
```

```
br0  Link encap:Ethernet  HWaddr .. 
     inet addr:192.168.10.3  Bcast:192.168.10.255  Mask:255.255.255.0 
     UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
     ...
eth0  Link encap:Ethernet  HWaddr .. 
      UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth1  Link encap:Ethernet  HWaddr .. 
      UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
```
[COLOR=#000000][FONT=Arial]
This is working well and is not causing any issues.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]We also have a Tinc VPN to our datacenter infrastructure on the same server (192.168.10.3) which is not part of the bridge. i.e.:[/FONT][/COLOR]

```
tincvpn   Link encap:Ethernet  HWaddr .. 
          inet addr:192.168.10.3  Bcast:192.168.255.255  Mask:255.255.0.0 
          ...
```
[COLOR=#000000][FONT=Arial]
We would like to override the routing on packets going through the bridge from the LAN for certain destinations (e.g. 192.168.5.0/24) to make them go via tinc. i.e: 192.168.10.x on LAN to 192.168.5.x should go via tinc and not to the gateway.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]We would like this to work for all machines on the LAN without having to configure anything on them but have found a workaround for now which is to add the following static route to each PC/Server on the LAN:[/FONT][/COLOR]

```
route add -net 192.168.5.0/24 via 192.168.10.3 dev eth0
```
[COLOR=#000000][FONT=Arial]
For the static route to work we also had to enable proxy_arp for all interfaces on 192.168.10.3.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
We tried the following configuration but it didn't work:[/FONT][/COLOR]

```
ip rule add fwmark 20 lookup 20
ip route add 192.168.0.0/16 dev tincvpn table 20
ebtables -t broute -I BROUTING -i eth1 -p ipv4 --ip-dst 192.168.5.0/24 -j REDIRECT --redirect-target DROP
iptables -t mangle -I PREROUTING -i eth1 -d 192.168.5.0/24 -j MARK --set-mark 20
```
[COLOR=#000000][FONT=Arial]
With this setup the packets arrived at the mangle rule and were marked but they did not route onto the tincvpn interface.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Our understanding was that we needed to drop the packets out of the bridge using ebtables and then use policy based routing to make the packets go through tinc. Is this understanding correct?
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]If anybody has any ideas as to why this didn't work it would be appreciated.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thanks a lot,
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Tom[/FONT][/COLOR]

---


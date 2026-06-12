---
title: "Setting up networking bridge for OVPN with pppoe inet connection"
date: 2017-07-31
forum: Server Platforms
---

### Post by marcin5 on 2017-07-31
Hi,

I'm in the (very loooong) process of setting up my Ubuntu Server based router. Now I'm trying to setup a network bridge that I can use to bridge my LAN with an OVPN TAP interface. After a few hours of trying different configs I came to a point that I really don't know what else I can do to make it work.

This is my current (non-bridge) config:

/etc/network/interfaces
```
auto lo
iface lo inet loopback


auto enp2s0
iface enp2s0 inet static
        address 192.168.1.1
        netmask 255.255.255.0

auto enp1s0
iface enp1s0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
pre-up /bin/ip link set enp1s0 up # line maintained by pppoeconf
provider dsl-provider
```


iptables script:
```
LANIF="enp2s0"
WANIF="ppp0"


iptables -t filter -A INPUT -i lo -j ACCEPT #LOOPBACK - IN
iptables -t filter -A INPUT -i $LANIF -j ACCEPT #LAN -> ROUTER
iptables -t filter -A INPUT -p icmp -j ACCEPT
iptables -t filter -A INPUT -m state --state ESTABLISHED -j ACCEPT
iptables -t filter -A INPUT -i $WANIF -p tcp -m tcp --dport 21 -j ACCEPT #FTP WAN
iptables -t filter -A INPUT -i $WANIF -p tcp -m tcp --dport 25 -j ACCEPT #MAIL WAN
iptables -t filter -A INPUT -i $WANIF -p tcp -m tcp --dport 80 -j ACCEPT #HTTP WAN
iptables -t filter -A INPUT -p udp -m udp --sport 123 --dport 123 -j ACCEPT #NTP
iptables -t filter -A INPUT -i $WANIF -p tcp -m tcp --dport 443 -j ACCEPT #HTTPS WAN
iptables -t filter -A INPUT -i $WANIF -p tcp -m tcp --dport 64000 -j ACCEPT #SSH ROUTER WAN
iptables -t filter -A INPUT -j DROP #RESZTA DO SMIECI
 
iptables -t filter -A OUTPUT -o lo -j ACCEPT #LOOPBACK - OUT
iptables -t filter -A OUTPUT -p udp -m udp --sport 123 --dport 123 -j ACCEPT #NTP


iptables -t filter -A FORWARD -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT #CONNTRACK
iptables -t filter -A FORWARD -i $LANIF -o $WANIF -j ACCEPT #PRZEKIEROWANIE RUCHU LAN -> WAN
iptables -t filter -A FORWARD -i $LANIF -o $WANIF -p tcp -m tcp --dport 53 -j DROP #BLOKADA ZEWNETRZNYCH DNSOW TCP
iptables -t filter -A FORWARD -i $LANIF -o $WANIF -p udp -m udp --dport 53 -j DROP #BLOKADA ZEWNETRZNYCH DNSOW UDP
iptables -t filter -A FORWARD -d 192.168.1.10/32 -p tcp -m tcp --dport 32400 -j ACCEPT #PRZEKIEROWANIE PMS - PORT TCP - OUT
iptables -t filter -A FORWARD -d 192.168.1.10/32 -p udp -m udp --dport 32400 -j ACCEPT #PRZEKIEROWANIE PMS - PORT UDP - OUT
iptables -t filter -A FORWARD -j DROP #RESZTA DO SMIECI


iptables -t nat -A PREROUTING -i $WANIF -p tcp -m tcp --dport 32400 -j DNAT --to-destination 192.168.1.10 #PRZEKIEROWANIE PMS - PORT TCP - IN
iptables -t nat -A PREROUTING -i $WANIF -p udp -m udp --dport 32400 -j DNAT --to-destination 192.168.1.10 #PRZEKIEROWANIE PMS - PORT UDP - IN
iptables -t nat -A POSTROUTING -o $WANIF -j MASQUERADE #MASZKARADA
```


The above works fine, but as soon as I put in there some bridging stuff it all goes to hell. Either pppoe doesn't work and LAN works or pppoe works fine (on the router only) and I can't even ping anything on LAN.

Here's a latest sample of my bridge config:

/etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto enp2s0
iface enp2s0 inet manual
       up ip link set $IFACE promisc on
       down ip link set $IFACE promisc off


auto bridge0
iface bridge0 inet static
       bridge_ports enp2s0
       bridge_stp off
       bridge_fd 0
       bridge_maxwait 0
       address 192.168.1.1
       netmask 255.255.255.0
       gateway 192.168.1.1
       network 192.168.1.0
       broadcast 192.168.1.255


auto enp1s0
iface enp1s0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
pre-up /bin/ip link set enp1s0 up # line maintained by pppoeconf
provider dsl-provider
```


the iptables script is almost the same here - I just change LANIF to "bridge0".

Does any of the network gurus have an idea of what I'm doing wrong here ? Would appreciate a working solution.
I've had a bridge configured for KVM use on my old NAS - I've tried that config but it didn't work here (it was using dhcp instead of static in the bridge config).

After using the bridged config this is what I'm getting:
[ATTACH=CONFIG]276186[/ATTACH][ATTACH=CONFIG]276187[/ATTACH]

---

### Post by wildmanne39 on 2017-07-31
*Thread moved to **Server Platforms**.*

---

### Post by marcin5 on 2017-07-31
The topic is more networking than server (actually nothing here is server specific except that it is on Server)

---

### Post by darkod on 2017-07-31
One question. Why bridging?
I would usually use bridging if I want all machines from one to appear like they are on the other end. Like with kvm hosts when you want the VMs to show up all in one main LAN. In your case you don't want that because you don't want all machines to show up on the ppoe side of the ISP.
What you want is basic routing in ubuntu of traffic between both interfaces. And that's very easy to do.
1. Enable ipv4 forwarding in /etc/syscfg.conf. You need to uncomment the line for ipv4 forward. After that restart the networking or better the whole server.
2. Make necessary iptables rules. You need masquerade rule for traffic going out the ppoe. Whether you need other iptables rules depends on your general setup.

---

### Post by marcin5 on 2017-07-31
> **darkod said:**
> One question. Why bridging?

As I wrote I want to bridge my LAN with OVPNs TAP device.

> **darkod said:**
> I would usually use bridging if I want all machines from one to appear like they are on the other end. Like with kvm hosts when you want the VMs to show up all in one main LAN. In your case you don't want that because you don't want all machines to show up on the ppoe side of the ISP.

PPPoE is a connection in my config - I'm not bridging it.

> **darkod said:**
> What you want is basic routing in ubuntu of traffic between both interfaces. And that's very easy to do.
1. Enable ipv4 forwarding in /etc/syscfg.conf. You need to uncomment the line for ipv4 forward. After that restart the networking or better the whole server.

Done...

> **darkod said:**
> 2. Make necessary iptables rules. You need masquerade rule for traffic going out the ppoe. Whether you need other iptables rules depends on your general setup.

...and done (I think - depends on what you mean by necessary rules)... doesn't work.
Please reread my configs.

---

### Post by darkod on 2017-07-31
What is exactly bridging the lan with the ovpn device? If that means the lan computers to go out through a vpn tunnel, you can achieve that in another way. Honestly I have never setup ovpn tap, only tun.
But I have routed all lan traffic through ovpn tun tunnel, if that serves your purpose I could help with that.

---

### Post by marcin5 on 2017-08-01
> **darkod said:**
> What is exactly bridging the lan with the ovpn device? If that means the lan computers to go out through a vpn tunnel, you can achieve that in another way. Honestly I have never setup ovpn tap, only tun.
But I have routed **all lan** traffic through ovpn tun tunnel, if that serves your purpose I could help with that.


If you are able to do all LAN traffic through TUN then I'd like to see that (and I mean all - so that a device, doesn't matter what OS it has and what kind of device it is, connected through that tunnel behaves exactly like it was physically on that LAN, including bradcasting etc.)
I've used TAP for years now with my previous Tomato based routers. I really don't want reconfigure everything.




Now, we have gone away from the topic... Is there anyone that can tell me why my config doesn't work, and what to do to make it work ?

---

### Post by darkod on 2017-08-02
For all traffic through TUN I usually set up a machine on the lan that is connected to the ovpn server with tun connection. On server side in the ovpn config I set it to force the client to use the tun as default gateway once connected.
So that ovpn client on the lan will always go out through the tun. Any other machine on the lan set up to use that ovpn client pc as default gw, will have its traffic going only over the tun.

---


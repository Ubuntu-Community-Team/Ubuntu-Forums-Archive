---
title: "Dynamic IPv6 and PPPoE"
date: 2011-08-31
forum: Server Platforms
---

### Post by niallm90 on 2011-08-31
My ISP is now offering dynamic IPv6 I can get an address but ping6 ipv6.google.com fails.

I am not really sure how I should be doing this but I found I have to use dhcp6c to get an address. Just adding the ipv6 , to my ppp options doesn't work.

How should dhcp6 client or server or relay be set up if I just want access from the ppp client currently.

Then I can work on how I am going to hand out addresses as it is also a pppoe server.

Thanks,
Niall

P.S. Apologies I am very tired, hopefully it isn't to bad a description.

---

### Post by lemming465 on 2011-08-31
Could we see the output of *ip address show; ip -4 route show; ip -6 route show*?
Inability to ping could be due to lack of a default route, or any of 99 other causes.

---

### Post by niallm90 on 2011-08-31
Ok so I managed to find the ISPs IP that returns the IPv6 DHCP addresses and I can ping that using this:

```

ping6 fe80::90:1a00:d7a3:450e%ppp999

```Here is the output from 
```

ip -6 route show
fe80::/64 dev eth2  proto kernel  metric 256 
fe80::/64 dev br0  proto kernel  metric 256 
fe80::/64 dev br1  proto kernel  metric 256 
fe80::/64 dev eth1  proto kernel  metric 256 
fe80::/64 dev ppp999  proto kernel  metric 256 
fe80::/10 dev ppp999  metric 1 
fe80::/10 dev ppp999  proto kernel  metric 256

``````

ip -4 route show
111.69.17.20 dev ppp999  proto kernel  scope link  src 123.255.47.55 
10.1.2.3 dev ppp1  proto kernel  scope link  src 10.1.1.1 
10.1.1.89 dev ppp5  proto kernel  scope link  src 10.1.1.1 
10.1.2.2 dev ppp0  proto kernel  scope link  src 10.1.1.1 
10.1.1.90 dev ppp2  proto kernel  scope link  src 10.1.1.1 
10.1.1.116 dev ppp6  proto kernel  scope link  src 10.1.1.1 
10.1.1.5 dev ppp3  proto kernel  scope link  src 10.1.1.1 
10.1.1.113 dev ppp8  proto kernel  scope link  src 10.1.1.1 
10.1.1.114 dev ppp9  proto kernel  scope link  src 10.1.1.1 
10.1.1.115 dev ppp4  proto kernel  scope link  src 10.1.1.1 
192.168.1.0/24 dev br1  proto kernel  scope link  src 192.168.1.1 
192.168.0.0/24 dev br0  proto kernel  scope link  src 192.168.0.10 

```

---

### Post by hawkmage on 2011-08-31
The IPv6 range fe80::/10 and fe80::/64 are Link-Local addresses, they are not globally accessible.

---

### Post by niallm90 on 2011-08-31
Hi thanks, I do understand that and that is my problem. How do I configure it to get a dynamic global address.

---

### Post by lemming465 on 2011-09-03
I'm a little puzzled as to where your default IPv4 route is hiding.  There should be one for 0/0 or "default", e.g. I have "default via 172.17.14.1 dev eth0  proto static".  It's also typical on a Linux box to have a route for 169.254.0.0/16 "zeroconf" addresses.   And I'm completely unclear on whether this is on a client PC or some kind of wifi or broadband gateway box.  Could you describe your network topology in more detail?  E.g. I'm typing this from a PC running ubuntu 11.04, connect to a buffalo wifi router, connected to a motorola docsis 3 cable modem.

Current consumer-grade network gear and popular operating systems such as Microsoft windows XP or Apple's OS-X don't do DHCPv6 very well, or at all.  So most IPv6 deployments currently use DHCPv4 for the everything except the v6 address, and SLAAC ("stateless address autoconfiguration") for the v6 address and upstream v6 gateway.  This is dependent on receiving ICMPv6 multicast router advertisements from the upstream router, which contain options for the on-link IPv6 64-bit network prefix and the gateway address.

Try running wireshark for 2-3 minutes and see if any RA's show up.  If not, there could be a problem upstream at your ISP.

---

### Post by niallm90 on 2011-09-04
The IPv4 default route is the first one in the IPv4 forwarding table..?.. 

Sorry I shall explain my network topology better:
```

Draytek Vigor 120                 Ubuntu 11.04 Server                      Clients
192.168.0.1 --------------------- 192.168.0.10 (br0)
[In pppoe bridge mode] ---------- 123.255.47.55 (ppp999)
                                  192.168.1.1 (br1) [DHCP] --------------- 192.168.1*
                                  10.1.1.1 (ppp*) [PPPoE] ---------------- 10.1.1.*
                                  10.2.1.1 (ppp*) [PPTP] ----------------- 10.2.1.*

```How often are the router advertisements sent? I have been been capturing for 6min and haven't seen anything yet. I was using this command:
```
tshark -i ppp999 -f ip6 -w ipv6.log
```Though if I exec this command I found when I was initially trying to get IPv6 working I see 2 packets.

```
dhcp6c -dDf -c /etc/wide-dhcpv6/dhcp6c.conf ppp999
```The config files contains:
```

interface ppp999 {
    send rapid-commit;
    request domain-name-servers;
    send ia-pd 0;
};

id-assoc pd {
    prefix-interface br1 {
        sla-id 1;
    };
};

```Output from the command:
```

Sep/05/2011 14:45:34: get_duid: extracted an existing DUID from /var/lib/dhcpv6/dhcp6c_duid: 00:01:00:01:15:f0:6f:8e:00:50:8b:03:8c:fe
Sep/05/2011 14:45:34: cfdebug_print: <3>comment [# Default dhpc6c configuration: it assumes the address is autoconfigured using] (78)
Sep/05/2011 14:45:34: cfdebug_print: <3>comment [# router advertisements.] (24)
Sep/05/2011 14:45:34: cfdebug_print: <3>comment [#profile default] (16)
Sep/05/2011 14:45:34: cfdebug_print: <3>comment [#{] (2)
Sep/05/2011 14:45:34: cfdebug_print: <3>comment [#  #information-only;] (21)
Sep/05/2011 14:45:34: cfdebug_print: <3>comment [#] (1)
Sep/05/2011 14:45:34: cfdebug_print: <3>comment [#  request domain-name-servers;] (31)
Sep/05/2011 14:45:34: cfdebug_print: <3>comment [#  request domain-name;] (23)
Sep/05/2011 14:45:34: cfdebug_print: <3>comment [#] (1)
Sep/05/2011 14:45:34: cfdebug_print: <3>comment [#  script "/etc/wide-dhcpv6/dhcp6c-script";] (43)
Sep/05/2011 14:45:34: cfdebug_print: <3>comment [#};] (3)
Sep/05/2011 14:45:34: cfdebug_print: <3>[interface] (9)
Sep/05/2011 14:45:34: cfdebug_print: <5>[ppp999] (6)
Sep/05/2011 14:45:34: cfdebug_print: <3>begin of closure [{] (1)
Sep/05/2011 14:45:34: cfdebug_print: <3>[send] (4)
Sep/05/2011 14:45:34: cfdebug_print: <3>[rapid-commit] (12)
Sep/05/2011 14:45:34: cfdebug_print: <3>end of sentence [;] (1)
Sep/05/2011 14:45:34: cfdebug_print: <3>[request] (7)
Sep/05/2011 14:45:34: cfdebug_print: <3>[domain-name-servers] (19)
Sep/05/2011 14:45:34: cfdebug_print: <3>end of sentence [;] (1)
Sep/05/2011 14:45:34: cfdebug_print: <3>comment [#request prefix-delegation;] (27)
Sep/05/2011 14:45:34: cfdebug_print: <3>[send] (4)
Sep/05/2011 14:45:34: cfdebug_print: <3>[ia-pd] (5)
Sep/05/2011 14:45:34: cfdebug_print: <3>[0] (1)
Sep/05/2011 14:45:34: cfdebug_print: <3>end of sentence [;] (1)
Sep/05/2011 14:45:34: cfdebug_print: <3>end of closure [}] (1)
Sep/05/2011 14:45:34: cfdebug_print: <3>end of sentence [;] (1)
Sep/05/2011 14:45:34: cfdebug_print: <3>[id-assoc] (8)
Sep/05/2011 14:45:34: cfdebug_print: <15>[pd] (2)
Sep/05/2011 14:45:34: cfdebug_print: <15>begin of closure [{] (1)
Sep/05/2011 14:45:34: cfdebug_print: <3>[prefix-interface] (16)
Sep/05/2011 14:45:34: cfdebug_print: <5>[br1] (3)
Sep/05/2011 14:45:34: cfdebug_print: <3>begin of closure [{] (1)
Sep/05/2011 14:45:34: cfdebug_print: <3>[sla-id] (6)
Sep/05/2011 14:45:34: cfdebug_print: <3>[1] (1)
Sep/05/2011 14:45:34: cfdebug_print: <3>end of sentence [;] (1)
Sep/05/2011 14:45:34: cfdebug_print: <3>end of closure [}] (1)
Sep/05/2011 14:45:34: cfdebug_print: <3>end of sentence [;] (1)
Sep/05/2011 14:45:34: cfdebug_print: <3>end of closure [}] (1)
Sep/05/2011 14:45:34: cfdebug_print: <3>end of sentence [;] (1)
Sep/05/2011 14:45:34: configure_pool: called
Sep/05/2011 14:45:34: clear_poolconf: called
Sep/05/2011 14:45:34: dhcp6_reset_timer: reset a timer on ppp999, state=INIT, timeo=0, retrans=15
Sep/05/2011 14:45:34: client6_send: a new XID (32d384) is generated
Sep/05/2011 14:45:34: copy_option: set client ID (len 14)
Sep/05/2011 14:45:34: copy_option: set rapid commit (len 0)
Sep/05/2011 14:45:34: copy_option: set elapsed time (len 2)
Sep/05/2011 14:45:34: copy_option: set option request (len 2)
Sep/05/2011 14:45:34: copyout_option: set IA_PD
Sep/05/2011 14:45:34: client6_send: send solicit to ff02::1:2%ppp999
Sep/05/2011 14:45:34: dhcp6_reset_timer: reset a timer on ppp999, state=SOLICIT, timeo=0, retrans=1001
Sep/05/2011 14:45:34: client6_recv: receive reply from fe80::90:1a00:d7a3:450e%ppp999 on ppp999
Sep/05/2011 14:45:34: dhcp6_get_options: get DHCP option server ID, len 23
Sep/05/2011 14:45:34:   DUID: 00:02:00:00:0a:4c:45:31:32:30:2f:37:34:35:41:43:33:33:45:58:32:2f:d7
Sep/05/2011 14:45:34: dhcp6_get_options: get DHCP option client ID, len 14
Sep/05/2011 14:45:34:   DUID: 00:01:00:01:15:f0:6f:8e:00:50:8b:03:8c:fe
Sep/05/2011 14:45:34: dhcp6_get_options: get DHCP option rapid commit, len 0
Sep/05/2011 14:45:34: dhcp6_get_options: get DHCP option IA_PD, len 41
Sep/05/2011 14:45:34:   IA_PD: ID=0, T1=43200, T2=69120
Sep/05/2011 14:45:34: copyin_option: get DHCP option IA_PD prefix, len 25
Sep/05/2011 14:45:34: copyin_option:   IA_PD prefix: 2406:e000:6249::/48 pltime=86400 vltime=86400
Sep/05/2011 14:45:34: dhcp6_get_options: get DHCP option opt_20, len 0
Sep/05/2011 14:45:34: dhcp6_get_options: unknown or unexpected DHCP6 option opt_20, len 0
Sep/05/2011 14:45:34: dhcp6_get_options: get DHCP option status code, len 2
Sep/05/2011 14:45:34:   status code: success
Sep/05/2011 14:45:34: client6_recvreply: status code: success
Sep/05/2011 14:45:34: get_ia: make an IA: PD-0
Sep/05/2011 14:45:34: update_prefix: create a prefix 2406:e000:6249::/48 pltime=86400, vltime=86400
Sep/05/2011 14:45:34: ifaddrconf: failed to add an address on br1: File exists
Sep/05/2011 14:45:34: dhcp6_remove_event: removing an event on ppp999, state=SOLICIT
Sep/05/2011 14:45:34: client6_recvreply: got an expected reply, sleeping.

```

Thanks and I apologise for my sum what brief previous posts.

---

### Post by lemming465 on 2011-09-05
Could we see the output of *ip address show* on the Ubuntu server?  I'm particularly curious as to what IPv6 addresses, if any, have been configured on the ppp999 link.  My impression is that normally the PPP tunnel would have a /64 assigned, often with the upstream end using host part ::1 and your end using host part ::2.  Once your ubuntu box finished configuring, I'd expect to see at least 3 addresses in play:  (1) the fe80::/64 link-local automatic end point address,  (2) the ppp point to point address  (3) a global unicast address, perhaps configured under the 2406:e000:6249::/48 prefix you say from DHCP.  

Unfortunately, while I have a fair bit of experience with native IPv6 and some of the kinds of tunnels (6in4, 6to4, teredo), I'm a PPP neophyte.  So I'm unclear on whether or not the global unicast address would be on the ppp999 interface or not.  However, there should definitely be a default route for IPv6 associated with that interface in a working configuration.  That is missing in your *ip -6 route show* output, so clearly there are some missing configuration steps still.  Does [this Debian configuration advice]("http://silmor.de/66") offer any insight?

Is your ISP actually offering /48 IPv6 subnets to end users, as the DHCP trace seems to indicate?  This is not unheard of, but is fairly generous.

What happens if you try to add an IPv6 address and route to the ppp999 interface by hand, e.g.```
ip address add 2406:e000:6249::3/64 dev ppp999
ip route add ::/0 dev ppp999
host ipv6.google.com
ping6 -c4 2607:f8b0:4001:c01::93  # or whatever came back from the DNS query
```
It's probably worth while trying to troubleshoot with manual configuration steps to figure out what a working configuration looks like, before taking the second step of trying to make it happen automatically.

---

### Post by niallm90 on 2011-09-06
ip address show
```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 00:50:8b:03:8c:fe brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 94:0c:6d:82:cf:88 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::960c:6dff:fe82:cf88/64 scope link 
       valid_lft forever preferred_lft forever
4: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:0c:f1:8f:90:d3 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::20c:f1ff:fe8f:90d3/64 scope link 
       valid_lft forever preferred_lft forever
5: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN 
    link/ether 00:0c:f1:8f:90:d3 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.10/24 brd 192.168.0.255 scope global br0
    inet6 fe80::20c:f1ff:fe8f:90d3/64 scope link 
       valid_lft forever preferred_lft forever
6: br1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN 
    link/ether 00:50:8b:03:8c:fe brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.1/24 brd 192.168.1.255 scope global br1
    inet6 2406:e000:6249:1:250:8bff:fe03:8cfe/64 scope global 
       valid_lft forever preferred_lft forever
    inet6 2406:e000:6247:1:250:8bff:fe03:8cfe/64 scope global 
       valid_lft forever preferred_lft forever
    inet6 fe80::250:8bff:fe03:8cfe/64 scope link 
       valid_lft forever preferred_lft forever
11: ppp3: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1492 qdisc pfifo_fast state UNKNOWN qlen 3
    link/ppp 
    inet 10.1.1.1 peer 10.1.1.5/32 scope global ppp3
271: ppp8: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 3
    link/ppp 
    inet 10.1.1.1 peer 10.1.2.2/32 scope global ppp8
286: ppp6: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1492 qdisc pfifo_fast state UNKNOWN qlen 3
    link/ppp 
    inet 10.1.1.1 peer 10.1.1.190/32 scope global ppp6
299: ppp999: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1492 qdisc pfifo_fast state UNKNOWN qlen 3
    link/ppp 
    inet 123.255.47.55 peer 111.69.17.20/32 scope global ppp999
    inet6 fe80::8df0:7279:3bab:28fc/10 scope link 
       valid_lft forever preferred_lft forever
304: ppp0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1480 qdisc pfifo_fast state UNKNOWN qlen 3
    link/ppp 
    inet 10.1.1.1 peer 10.1.1.200/32 scope global ppp0
306: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 100
    link/none 
    inet 169.254.13.38 peer 169.254.13.37/32 scope global tun0
310: ppp1: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1480 qdisc pfifo_fast state UNKNOWN qlen 3
    link/ppp 
    inet 10.1.1.1 peer 10.1.1.204/32 scope global ppp1
313: ppp5: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1480 qdisc pfifo_fast state UNKNOWN qlen 3
    link/ppp 
    inet 10.1.1.1 peer 10.1.1.205/32 scope global ppp5
318: ppp2: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1480 qdisc pfifo_fast state UNKNOWN qlen 3
    link/ppp 
    inet 10.1.1.1 peer 10.1.1.209/32 scope global ppp2
319: ppp7: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1400 qdisc pfifo_fast state UNKNOWN qlen 3
    link/ppp 
    inet 10.1.1.1 peer 10.1.2.3/32 scope global ppp7
320: ppp9: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1480 qdisc pfifo_fast state UNKNOWN qlen 3
    link/ppp 
    inet 10.1.1.1 peer 10.1.1.210/32 scope global ppp9
176: ppp4: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1480 qdisc pfifo_fast state UNKNOWN qlen 3
    link/ppp 
    inet 10.1.1.1 peer 10.1.1.115/32 scope global ppp4

```

Yes the ISP has stated they are offering /48 subnets.

Yay. After preforming the steps you specified I could resolve the IPv6 Google address and ping the IP you gave. I did try to do it manualy but I am affraid I didn't know enough about IPv6 to do it.

Now I could right a script to run the commands. Is there a way I could just get the IPv6 subnet from the ISP.

---

### Post by lemming465 on 2011-09-06
The dhcp6c got the prefix, but I don't offhand see a way to get it to either add a route for it or send a dbus message about it.  However, it probably calls a setup script with arguments which include the prefix, and if you can find that, it would be the logical place to have the route added from automatically.  There should be a better way than running the output of *ip address show* into a perl script, which would be crude but effective.

---

### Post by niallm90 on 2011-09-07
Hi,
Thanks for everyone's help. I managed to hack something together with a bunch of dirty bash scripts. If anyone is interested I can post them but I am not sure how reliable they are.

Thanks,
Niall

---


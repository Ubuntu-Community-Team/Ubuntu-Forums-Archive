---
title: "Building a IPv6 gateway"
date: 2011-01-27
forum: Server Platforms
---

### Post by Rich43 on 2011-01-27
I have recently put together a small Intel Atom server as a gateway and installed Ubuntu Server onto its little 4GB SSD.

It has two NIC's, one on the motherboard (eth0) which is the Internet and A PCI NIC (eth1) which goes out to a gigabit switch and from there all the desktops, laptops etc.

I have set up ufw (Ubuntu's 'uncomplicated firewall') which handles the port filtering and masquerading. It works great for IPv4 (masquerading is working!) but I have problems using it with IPv6 as I will explain later.

I have also set it up with a Hurricane Electric IPv6 tunnel from [http://tunnelbroker.net/](http://tunnelbroker.net/). I have gotten radvd to send out the IPv6 addresses correctly and the IPv6 connection is working fine on the gateway itself.

The problems start when I try to access a website from an external device such as my laptop. It manages to resolve the IPv6 address of say ipv6.google.com just fine but gets stuck on connecting... and eventually fails.

ufw might be blocking it or I might of just set the whole thing up wrong, I've spent hours searching the web for solutions and tried all sorts of things :(

Here is my log output and config files etc: (warning large amount of text!)

tail /var/log/syslog while connecting to IPv6 website:
```

gateway@gateway:~$ tail /var/log/syslog
Jan 27 20:42:37 gateway kernel: [ 1949.847386] [UFW BLOCK] IN=he-ipv6 OUT= MAC=70:71:bc:bc:72:e7:00:23:cd:b0:5a:6e:08:00:45:00:00:ec:00:00:40:00:f7:29:8f:d4:d8:42:50:1a:c0:a8:0a:0f:60:00:00:00:00:b0:3a:40:fe:80:00:00:00:00:00:00:00:00:00:00:d8:42:50:1a:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:01:02:68:49:00:00:00:00:60:00:00:00:00:80:3a:ff:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:2a:00:14:50:80:06:00:00:00:00:00:00:00:00:00:93:89:00:63:64:00:00:00:00:20:01:04:70:1f:09:10:e7:d4:d1:f2:05:65:fc:84:94:20:01 TUNNEL=216.66.80.26->192.168.10.15 SRC=fe80:0000:0000:0000:0000:0000:d842:501a DST=fe80:0000:0000:0000:0000:0000:c0a8:14fd LEN=216 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=ICMPv6 TYPE=1 CODE=2 [SRC=fe80:0000:0000:0000:0000:0000:c0a8:14fd DST=2a00:1450:8006:0000:0000:0000:0000:0093 LEN=168 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=ICMPv6 TYPE=137 CODE=0 ] 
Jan 27 20:42:37 gateway kernel: [ 1949.882095] [UFW BLOCK] IN=he-ipv6 OUT= MAC=70:71:bc:bc:72:e7:00:23:cd:b0:5a:6e:08:00:45:00:00:ec:00:00:40:00:f7:29:8f:d4:d8:42:50:1a:c0:a8:0a:0f:60:00:00:00:00:b0:3a:40:fe:80:00:00:00:00:00:00:00:00:00:00:d8:42:50:1a:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:01:02:68:49:00:00:00:00:60:00:00:00:00:80:3a:ff:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:2a:00:14:50:80:06:00:00:00:00:00:00:00:00:00:93:89:00:63:66:00:00:00:00:20:01:04:70:1f:09:10:e7:d4:d1:f2:05:65:fc:84:94:20:01 TUNNEL=216.66.80.26->192.168.10.15 SRC=fe80:0000:0000:0000:0000:0000:d842:501a DST=fe80:0000:0000:0000:0000:0000:c0a8:14fd LEN=216 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=ICMPv6 TYPE=1 CODE=2 [SRC=fe80:0000:0000:0000:0000:0000:c0a8:14fd DST=2a00:1450:8006:0000:0000:0000:0000:0093 LEN=168 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=ICMPv6 TYPE=137 CODE=0 ] 
Jan 27 20:42:37 gateway kernel: [ 1949.917462] [UFW BLOCK] IN=he-ipv6 OUT= MAC=70:71:bc:bc:72:e7:00:23:cd:b0:5a:6e:08:00:45:00:00:ec:00:00:40:00:f7:29:8f:d4:d8:42:50:1a:c0:a8:0a:0f:60:00:00:00:00:b0:3a:40:fe:80:00:00:00:00:00:00:00:00:00:00:d8:42:50:1a:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:01:02:68:49:00:00:00:00:60:00:00:00:00:80:3a:ff:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:2a:00:14:50:80:06:00:00:00:00:00:00:00:00:00:93:89:00:63:68:00:00:00:00:20:01:04:70:1f:09:10:e7:d4:d1:f2:05:65:fc:84:94:20:01 TUNNEL=216.66.80.26->192.168.10.15 SRC=fe80:0000:0000:0000:0000:0000:d842:501a DST=fe80:0000:0000:0000:0000:0000:c0a8:14fd LEN=216 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=ICMPv6 TYPE=1 CODE=2 [SRC=fe80:0000:0000:0000:0000:0000:c0a8:14fd DST=2a00:1450:8006:0000:0000:0000:0000:0093 LEN=168 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=ICMPv6 TYPE=137 CODE=0 ] 
Jan 27 20:42:37 gateway kernel: [ 1949.951630] [UFW BLOCK] IN=he-ipv6 OUT= MAC=70:71:bc:bc:72:e7:00:23:cd:b0:5a:6e:08:00:45:00:00:ec:00:00:40:00:f7:29:8f:d4:d8:42:50:1a:c0:a8:0a:0f:60:00:00:00:00:b0:3a:40:fe:80:00:00:00:00:00:00:00:00:00:00:d8:42:50:1a:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:01:02:68:49:00:00:00:00:60:00:00:00:00:80:3a:ff:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:2a:00:14:50:80:06:00:00:00:00:00:00:00:00:00:93:89:00:63:6a:00:00:00:00:20:01:04:70:1f:09:10:e7:d4:d1:f2:05:65:fc:84:94:20:01 TUNNEL=216.66.80.26->192.168.10.15 SRC=fe80:0000:0000:0000:0000:0000:d842:501a DST=fe80:0000:0000:0000:0000:0000:c0a8:14fd LEN=216 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=ICMPv6 TYPE=1 CODE=2 [SRC=fe80:0000:0000:0000:0000:0000:c0a8:14fd DST=2a00:1450:8006:0000:0000:0000:0000:0093 LEN=168 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=ICMPv6 TYPE=137 CODE=0 ] 
Jan 27 20:42:37 gateway kernel: [ 1949.971056] [UFW BLOCK] IN=he-ipv6 OUT= MAC=70:71:bc:bc:72:e7:00:23:cd:b0:5a:6e:08:00:45:00:00:ec:00:00:40:00:f7:29:8f:d4:d8:42:50:1a:c0:a8:0a:0f:60:00:00:00:00:b0:3a:40:fe:80:00:00:00:00:00:00:00:00:00:00:d8:42:50:1a:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:01:02:68:49:00:00:00:00:60:00:00:00:00:80:3a:ff:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:2a:00:14:50:80:06:00:00:00:00:00:00:00:00:00:93:89:00:63:62:00:00:00:00:20:01:04:70:1f:09:10:e7:d4:d1:f2:05:65:fc:84:94:20:01 TUNNEL=216.66.80.26->192.168.10.15 SRC=fe80:0000:0000:0000:0000:0000:d842:501a DST=fe80:0000:0000:0000:0000:0000:c0a8:14fd LEN=216 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=ICMPv6 TYPE=1 CODE=2 [SRC=fe80:0000:0000:0000:0000:0000:c0a8:14fd DST=2a00:1450:8006:0000:0000:0000:0000:0093 LEN=168 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=ICMPv6 TYPE=137 CODE=0 ] 
Jan 27 20:42:47 gateway kernel: [ 1960.071997] [UFW BLOCK] IN=he-ipv6 OUT= MAC=70:71:bc:bc:72:e7:00:23:cd:b0:5a:6e:08:00:45:00:00:ec:00:00:40:00:f7:29:8f:d4:d8:42:50:1a:c0:a8:0a:0f:60:00:00:00:00:b0:3a:40:fe:80:00:00:00:00:00:00:00:00:00:00:d8:42:50:1a:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:01:02:68:49:00:00:00:00:60:00:00:00:00:80:3a:ff:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:2a:00:14:50:80:06:00:00:00:00:00:00:00:00:00:93:89:00:63:62:00:00:00:00:20:01:04:70:1f:09:10:e7:d4:d1:f2:05:65:fc:84:94:20:01 TUNNEL=216.66.80.26->192.168.10.15 SRC=fe80:0000:0000:0000:0000:0000:d842:501a DST=fe80:0000:0000:0000:0000:0000:c0a8:14fd LEN=216 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=ICMPv6 TYPE=1 CODE=2 [SRC=fe80:0000:0000:0000:0000:0000:c0a8:14fd DST=2a00:1450:8006:0000:0000:0000:0000:0093 LEN=168 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=ICMPv6 TYPE=137 CODE=0 ] 
Jan 27 20:42:47 gateway kernel: [ 1960.107258] [UFW BLOCK] IN=he-ipv6 OUT= MAC=70:71:bc:bc:72:e7:00:23:cd:b0:5a:6e:08:00:45:00:00:ec:00:00:40:00:f7:29:8f:d4:d8:42:50:1a:c0:a8:0a:0f:60:00:00:00:00:b0:3a:40:fe:80:00:00:00:00:00:00:00:00:00:00:d8:42:50:1a:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:01:02:68:49:00:00:00:00:60:00:00:00:00:80:3a:ff:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:2a:00:14:50:80:06:00:00:00:00:00:00:00:00:00:93:89:00:63:64:00:00:00:00:20:01:04:70:1f:09:10:e7:d4:d1:f2:05:65:fc:84:94:20:01 TUNNEL=216.66.80.26->192.168.10.15 SRC=fe80:0000:0000:0000:0000:0000:d842:501a DST=fe80:0000:0000:0000:0000:0000:c0a8:14fd LEN=216 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=ICMPv6 TYPE=1 CODE=2 [SRC=fe80:0000:0000:0000:0000:0000:c0a8:14fd DST=2a00:1450:8006:0000:0000:0000:0000:0093 LEN=168 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=ICMPv6 TYPE=137 CODE=0 ] 
Jan 27 20:42:47 gateway kernel: [ 1960.143516] [UFW BLOCK] IN=he-ipv6 OUT= MAC=70:71:bc:bc:72:e7:00:23:cd:b0:5a:6e:08:00:45:00:00:ec:00:00:40:00:f7:29:8f:d4:d8:42:50:1a:c0:a8:0a:0f:60:00:00:00:00:b0:3a:40:fe:80:00:00:00:00:00:00:00:00:00:00:d8:42:50:1a:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:01:02:68:49:00:00:00:00:60:00:00:00:00:80:3a:ff:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:2a:00:14:50:80:06:00:00:00:00:00:00:00:00:00:93:89:00:63:66:00:00:00:00:20:01:04:70:1f:09:10:e7:d4:d1:f2:05:65:fc:84:94:20:01 TUNNEL=216.66.80.26->192.168.10.15 SRC=fe80:0000:0000:0000:0000:0000:d842:501a DST=fe80:0000:0000:0000:0000:0000:c0a8:14fd LEN=216 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=ICMPv6 TYPE=1 CODE=2 [SRC=fe80:0000:0000:0000:0000:0000:c0a8:14fd DST=2a00:1450:8006:0000:0000:0000:0000:0093 LEN=168 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=ICMPv6 TYPE=137 CODE=0 ] 
Jan 27 20:42:47 gateway kernel: [ 1960.178958] [UFW BLOCK] IN=he-ipv6 OUT= MAC=70:71:bc:bc:72:e7:00:23:cd:b0:5a:6e:08:00:45:00:00:ec:00:00:40:00:f7:29:8f:d4:d8:42:50:1a:c0:a8:0a:0f:60:00:00:00:00:b0:3a:40:fe:80:00:00:00:00:00:00:00:00:00:00:d8:42:50:1a:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:01:02:68:49:00:00:00:00:60:00:00:00:00:80:3a:ff:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:2a:00:14:50:80:06:00:00:00:00:00:00:00:00:00:93:89:00:63:68:00:00:00:00:20:01:04:70:1f:09:10:e7:d4:d1:f2:05:65:fc:84:94:20:01 TUNNEL=216.66.80.26->192.168.10.15 SRC=fe80:0000:0000:0000:0000:0000:d842:501a DST=fe80:0000:0000:0000:0000:0000:c0a8:14fd LEN=216 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=ICMPv6 TYPE=1 CODE=2 [SRC=fe80:0000:0000:0000:0000:0000:c0a8:14fd DST=2a00:1450:8006:0000:0000:0000:0000:0093 LEN=168 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=ICMPv6 TYPE=137 CODE=0 ] 
Jan 27 20:42:48 gateway kernel: [ 1960.214946] [UFW BLOCK] IN=he-ipv6 OUT= MAC=70:71:bc:bc:72:e7:00:23:cd:b0:5a:6e:08:00:45:00:00:ec:00:00:40:00:f7:29:8f:d4:d8:42:50:1a:c0:a8:0a:0f:60:00:00:00:00:b0:3a:40:fe:80:00:00:00:00:00:00:00:00:00:00:d8:42:50:1a:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:01:02:68:49:00:00:00:00:60:00:00:00:00:80:3a:ff:fe:80:00:00:00:00:00:00:00:00:00:00:c0:a8:14:fd:2a:00:14:50:80:06:00:00:00:00:00:00:00:00:00:93:89:00:63:6a:00:00:00:00:20:01:04:70:1f:09:10:e7:d4:d1:f2:05:65:fc:84:94:20:01 TUNNEL=216.66.80.26->192.168.10.15 SRC=fe80:0000:0000:0000:0000:0000:d842:501a DST=fe80:0000:0000:0000:0000:0000:c0a8:14fd LEN=216 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=ICMPv6 TYPE=1 CODE=2 [SRC=fe80:0000:0000:0000:0000:0000:c0a8:14fd DST=2a00:1450:8006:0000:0000:0000:0000:0093 LEN=168 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=ICMPv6 TYPE=137 CODE=0 ] 
gateway@gateway:~$ 

```

sudo ufw status

```

gateway@gateway:~$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
546                        ALLOW       Anywhere
547                        ALLOW       Anywhere
41                         ALLOW       Anywhere
22                         ALLOW       Anywhere
67                         ALLOW       Anywhere
68                         ALLOW       Anywhere
53                         ALLOW       Anywhere
Anywhere                   ALLOW       95.172.230.195/ipv6
Anywhere                   ALLOW       216.66.80.26/ipv6
7                          ALLOW       Anywhere
546                        ALLOW       Anywhere (v6)
547                        ALLOW       Anywhere (v6)
41                         ALLOW       Anywhere (v6)
22                         ALLOW       Anywhere (v6)
67                         ALLOW       Anywhere (v6)
68                         ALLOW       Anywhere (v6)
53                         ALLOW       Anywhere (v6)
7                          ALLOW       Anywhere (v6)

gateway@gateway:~$ 

```

cat /etc/network/interfaces
```

gateway@gateway:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        address 192.168.20.253
        netmask 255.255.255.0
        network 192.168.20.0
        broadcast 192.168.20.255

auto he-ipv6
iface he-ipv6 inet6 v4tunnel
     endpoint 216.66.80.26
     address  2001:470:1f08:10e7::2
     netmask  64
     up ip -6 route add default dev he-ipv6
     down ip -6 route del default dev he-ipv6
gateway@gateway:~$ 

```

ifconfig
```

gateway@gateway:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 70:71:bc:bc:72:e7  
          inet addr:192.168.10.15  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::7271:bcff:febc:72e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6434248 (6.4 MB)  TX bytes:993571 (993.5 KB)
          Interrupt:44 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:1f:1f:e9:99:c6  
          inet addr:192.168.20.253  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:1fff:fee9:99c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:250412 (250.4 KB)  TX bytes:653333 (653.3 KB)
          Interrupt:20 Base address:0x6000 

he-ipv6   Link encap:IPv6-in-IPv4  
          inet6 addr: fe80::c0a8:14fd/64 Scope:Link
          inet6 addr: 2001:470:1f08:10e7::2/64 Scope:Global
          UP POINTOPOINT RUNNING NOARP  MTU:1480  Metric:1
          RX packets:777 errors:0 dropped:0 overruns:0 frame:0
          TX packets:772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:563617 (563.6 KB)  TX bytes:105701 (105.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13659 (13.6 KB)  TX bytes:13659 (13.6 KB)

gateway@gateway:~$ 

```

cat /etc/radvd.conf
```

gateway@gateway:~$ cat /etc/radvd.conf 
interface eth1
{
   AdvSendAdvert on;
   prefix 2001:470:1f09:10e7::/64
   {
        AdvOnLink on;
        AdvAutonomous on;
        AdvRouterAddr on;
   };
};
gateway@gateway:~$ 

```

ip -6 route show
```

gateway@gateway:~$  ip -6 route show
2001:470:1f08:10e7::/64 via :: dev he-ipv6  proto kernel  metric 256  mtu 1480 advmss 1420 hoplimit 0
fe80::/64 dev eth1  proto kernel  metric 256  mtu 1500 advmss 1440 hoplimit 0
fe80::/64 dev eth0  proto kernel  metric 256  mtu 1500 advmss 1440 hoplimit 0
fe80::/64 via :: dev he-ipv6  proto kernel  metric 256  mtu 1480 advmss 1420 hoplimit 0
default dev he-ipv6  metric 1024  mtu 1480 advmss 1420 hoplimit 0

```

If you need any more output let me know :)

---

### Post by Rich43 on 2011-01-27
Bump, Please someone help, I am really stuck. Any help however little appreciated. Networking is not my speciality.

---

### Post by Rich43 on 2011-01-28
BINGO! Took days of hard labour to figure this out!!!!

I added this to my /etc/network/interfaces:
auto eth1
iface eth1 inet static
.... ipv4 stuff here ...
up ip -6 addr add <routed 64 prefix from tunnel website>::<unique number here>/64 dev eth1
up ip -6 route add <ipv6 address of your tunnel (you can find it in ifconfig/he-ipv6)>/64  dev eth1
down ip -6 addr del <routed 64 prefix from tunnel website>::<unique number here>/64 dev eth1
down ip -6 route del <ipv6 address of your tunnel (you can find it in ifconfig/he-ipv6)>/64  dev eth1

I figured it out with some guess work and also from a reply on another forum that says:
> eth0 and eth1 don't have IPv6 addresses assigned to them...assign them an address from your routed /64 (or if they're on different subnets, from the /48)

He was only half right, eth0 didnt need an ipv6 address. only eth1 needed one, and I didnt need a /48, 64 seems to work fine.

I really hope this helps someone. Was the hardest networking problem ive had. If only there was more good info like this on the internet!

---

### Post by trmentry on 2011-02-04
> 
up ip -6 addr add <routed 64 prefix from tunnel website>::<unique number here>/64 dev eth1
up ip -6 route add <ipv6 address of your tunnel (you can find it in ifconfig/he-ipv6)>/64 dev eth1
down ip -6 addr del <routed 64 prefix from tunnel website>::<unique number here>/64 dev eth1
down ip -6 route del <ipv6 address of your tunnel (you can find it in ifconfig/he-ipv6)>/64 dev eth1


Can you expand on the <unique number here>/64

do I just take a another addr out of the /64?  Plus also assign an addy to my eth0 (only interface)

currently I've set up the tunnel from a linux host, not the firewall/gateway.  It hands out the ipv6 addys to the lan, but can't route.

so figure I'm missing the above, but a bit stuck.

thanks

---


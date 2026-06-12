---
title: "vpn connection gateway issue."
date: 2013-08-09
forum: Server Platforms
---

### Post by learnbash on 2013-08-09
Hello folks when i connect to vpn my internet browsing not working.

Below is the code before connecting.

```


# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

# ifconfig wlan0
wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.46  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 fe80::222:5fff:fe6c:4500  prefixlen 64  scopeid 0x20<link>
        ether 00:22:5f:6c:45:00  txqueuelen 1000  (Ethernet)
        RX packets 63747  bytes 45146944 (43.0 MiB)
        RX errors 0  dropped 0  overruns 0  frame 247211
        TX packets 61353  bytes 10983031 (10.4 MiB)
        TX errors 9  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 17  base 0xc000  



```

After vpn connection

```


# ifconfig tun0
tun0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 10.8.0.10  netmask 255.255.255.255  destination 10.8.0.9
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 100  (UNSPEC)
        RX packets 231  bytes 31034 (30.3 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 357  bytes 43482 (42.4 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.8.0.9        128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
10.8.0.1        10.8.0.9        255.255.255.255 UGH   0      0        0 tun0
10.8.0.9        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
80.1.1.xxx  192.168.2.1     255.255.255.255 UGH   0      0        0 wlan0
128.0.0.0       10.8.0.9        128.0.0.0       UG    0      0        0 tun0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0





```

Please help me what should i do, so my browsing will work.

---

### Post by sandyd on 2013-08-09
> **learnbash said:**
> Hello folks when i connect to vpn my internet browsing not working.

Below is the code before connecting.

```


# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

# ifconfig wlan0
wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.46  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 fe80::222:5fff:fe6c:4500  prefixlen 64  scopeid 0x20<link>
        ether 00:22:5f:6c:45:00  txqueuelen 1000  (Ethernet)
        RX packets 63747  bytes 45146944 (43.0 MiB)
        RX errors 0  dropped 0  overruns 0  frame 247211
        TX packets 61353  bytes 10983031 (10.4 MiB)
        TX errors 9  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 17  base 0xc000  



```

After vpn connection

```


# ifconfig tun0
tun0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 10.8.0.10  netmask 255.255.255.255  destination 10.8.0.9
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 100  (UNSPEC)
        RX packets 231  bytes 31034 (30.3 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 357  bytes 43482 (42.4 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.8.0.9        128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
10.8.0.1        10.8.0.9        255.255.255.255 UGH   0      0        0 tun0
10.8.0.9        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
80.1.1.xxx  192.168.2.1     255.255.255.255 UGH   0      0        0 wlan0
128.0.0.0       10.8.0.9        128.0.0.0       UG    0      0        0 tun0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0





```

Please help me what should i do, so my browsing will work.
few things to check

You have to have a masquerade/snat rule loaded in Iptables so that traffic from openvpn is routed to ip
something like
```

-A POSTROUTING -s 192.168.10.0/24 -j SNAT --to public-ip-here
```

You have to have enabled ipv4 forwarding in sysctl.conf
Check the value of


```

grep "net.ipv4.ip_forward" /etc/sysctl.conf
``` - it should return "net.ipv4.ip_forward=1" without a comment (#) in front

If your still having trouble, please post your openvpn config

---


---
title: "Newly installed VM unable to connect network/internet"
date: 2017-12-06
forum: Virtualisation
---

### Post by satimis on 2017-12-06
Hi all,

Networking problem
Newly installed VM unable to connect network/internet

Host - Ubuntu 16.04 desktop
VM1 - Ubuntu 16.04 desktop (running VM)
VM2 - Ubuntu 16.04 desktop (newly installed on ubuntu-16.04.3-desktop-amd64.iso)


VM1
===
&#10219; cat /etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto enp0s3
iface enp0s3 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.8.26
        dns-nameservers xxx.xxx.xxx.xxx
        network         192.168.8.0
        netmask         255.255.255.0
        broadcast       192.168.8.255
        gateway         192.168.8.1
        bridge_ports    enp0s3
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```

&#10219; ifconfig```

br0       Link encap:Ethernet  HWaddr 08:00:27:77:75:55  
          inet addr:192.168.8.26  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe77:7555/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:998 errors:0 dropped:0 overruns:0 frame:0
          TX packets:313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91820 (91.8 KB)  TX bytes:18022 (18.0 KB)

enp0s3    Link encap:Ethernet  HWaddr 08:00:27:77:75:55  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:999 errors:0 dropped:0 overruns:0 frame:0
          TX packets:323 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:105878 (105.8 KB)  TX bytes:23511 (23.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:338 (338.0 B)  TX bytes:338 (338.0 B)

```


VM2
===
&#10219; cat /etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto enp0s3
iface enp0s3 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.8.30
        dns-nameservers xxx.xxx.xxx.xxx
        network         192.168.8.0
        netmask         255.255.255.0
        broadcast       192.168.8.255
        gateway         192.168.8.1
        bridge_ports    enp0s3
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```

&#10219; ifconfig```

enp0s3    Link encap:Ethernet  HWaddr 08:00:27:f6:ad:56  
          inet6 addr: fe80::a00:27ff:fef6:ad56/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19779 (19.7 KB)  TX bytes:2763 (2.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

VM2 unable to connect network/internet


If /etc/network/interfaces changed to;

&#10219; cat /etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.8.30
        dns-nameservers xxx.xxx.xxx.xxx
        network         192.168.8.0
        netmask         255.255.255.0
        broadcast       192.168.8.255
        gateway         192.168.8.1
        bridge_ports    eth0
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```


&#10219; ifconfig```

enp0s3    Link encap:Ethernet  HWaddr 08:00:27:f6:ad:56  
          inet addr:192.168.8.2  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::23c7:e5c0:65de:5c29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4584 (4.5 KB)  TX bytes:8425 (8.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1210 (1.2 KB)  TX bytes:1210 (1.2 KB)

```

VM2 can connect network/internet but I couldn't set static IP

Please help.  Thanks

Regards
satimis

---

### Post by satimis on 2017-12-06
Hi all,

Problem solved.

I forgot to install bridge-utils

Thanks

Regards
satimis

---

### Post by linuxsecrets on 2017-12-06
I believe you're missing some utilities, the bridge-utils

---


---
title: "How to allow ping between ubuntu 14.04 qemu host and windows guests"
date: 2014-06-29
forum: Virtualisation
---

### Post by kurnosem on 2014-06-29
I have a Ubuntu 14.04 host with this config:

```
    $ brctl show
    bridge name     bridge id               STP enabled     interfaces
    virbr0          8000.000000000000       yes

```


ifconfig:

   ```
 $ifconfig
    em1       Link encap:Ethernet  HWaddr f8:bc:12:41:54:2c
              inet addr:10.105.3.174  Bcast:10.105.3.255  Mask:255.255.252.0
              inet6 addr: fe80::fabc:12ff:fe41:542c/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:12929453 errors:0 dropped:35056 overruns:0 frame:0
              TX packets:5711442 errors:65 dropped:0 overruns:0 carrier:0
              collisions:348042 txqueuelen:1000
              RX bytes:4199352937 (4.1 GB)  TX bytes:3621341059 (3.6 GB)
              Interrupt:16
    
    lo        Link encap:Local Loopback
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:65536  Metric:1
              RX packets:247410 errors:0 dropped:0 overruns:0 frame:0
              TX packets:247410 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0
              RX bytes:471219741 (471.2 MB)  TX bytes:471219741 (471.2 MB)
    
    macvtap0  Link encap:Ethernet  HWaddr 52:54:00:25:ce:8b
              inet6 addr: fe80::5054:ff:fe25:ce8b/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:3524694 errors:16 dropped:16 overruns:0 frame:0
              TX packets:508283 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:500
              RX bytes:334642552 (334.6 MB)  TX bytes:33851959 (33.8 MB)
    
    tap0      Link encap:Ethernet  HWaddr 0e:f6:5f:b1:36:d0
              inet addr:192.168.100.151  Bcast:192.168.100.255  Mask:255.255.255.0
              inet6 addr: fe80::cf6:5fff:feb1:36d0/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:1419732 errors:0 dropped:0 overruns:0 frame:0
              TX packets:314900 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:100
              RX bytes:287785383 (287.7 MB)  TX bytes:156840878 (156.8 MB)
    
    virbr0    Link encap:Ethernet  HWaddr 00:00:00:00:00:00
              inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:91794797 errors:0 dropped:0 overruns:0 frame:0
              TX packets:48168192 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0
              RX bytes:135117531316 (135.1 GB)  TX bytes:5636029278 (5.6 GB)
```


Guest network config:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=254350&d=1404077650[/IMG]
[ATTACH=CONFIG]254350[/ATTACH]


I'm able to access/ping to the guest machine from any other machine of the network. But I can't do it host <=> guest:

host => guest

```
    $ ping 10.105.2.65
    PING 10.105.2.65 (10.105.2.65) 56(84) bytes of data.
    From 10.105.3.174 icmp_seq=1 Destination Host Unreachable
```

guest => host (sorry for the spanish)

```
    C:\Users\admin>ping 10.105.3.174
    Haciendo ping a 10.105.3.174 con 32 bytes de datos:
    Respuesta desde 10.105.2.65: Host de destino inaccesible.
```


The host => guest arping works ok!!

    ```
$ nmap -Pn -n 10.105.2.65
    
    Starting Nmap 6.40 ( http://nmap.org ) at 2014-06-29 20:57 CEST
    Nmap scan report for 10.105.2.65
    Host is up (0.090s latency).
    All 1000 scanned ports on 10.105.2.65 are filtered
    
    Nmap done: 1 IP address (1 host up) scanned in 14.06 seconds

```

But I cannot ping directly or use any other service. Any solution? I want that the guest machine looks in the network like any other real machine.

---

### Post by Tadaen_Sylvermane on 2014-06-29
[https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

The virbr0 is the internal network between virtual machines. To get them on the same lan as the host you need to follow the above and create a bridge.

My hosts /etc/network/interfaces for reference. With this I have a couple guests running as if plugged directly into my router. Separate static ips on each.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# eth0
auto eth0
iface eth0 inet manual


# kvm br0
auto br0
iface br0 inet static
    address 10.0.1.175
    network 10.0.1.0
    netmask 255.255.255.0
    broadcast 10.0.1.255
    gateway 10.0.1.1
    bridge_ports eth0
    bridge_stp off
    dns-nameservers 10.0.1.1 8.8.8.8 8.8.4.4
```

---


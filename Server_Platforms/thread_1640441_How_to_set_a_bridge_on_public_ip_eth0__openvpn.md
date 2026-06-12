---
title: "How to set a bridge on public ip eth0 / openvpn"
date: 2010-12-07
forum: Server Platforms
---

### Post by 007c on 2010-12-07
Hi there i'm trying to setup a network bridge to get openvpn going in bridge mode however i'm having a rough time.

I have a dedicated server and 5 usable public ips.
Right now my  ifconfig is
```

eth0      Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx
          inet addr:xxx.94.247.202  Bcast:xxx.94.247.207  Mask:255.255.255.248
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34567 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4710259 (4.4 MiB)  TX bytes:12782064 (12.1 MiB)
          Interrupt:16

eth0:1    Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx
          inet addr:xxx.94.247.203  Bcast:xxx.94.247.207  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16

eth0:2    Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx
          inet addr:xxx.94.247.204  Bcast:xxx.94.247.207  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16

eth0:3    Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx
          inet addr:xxx.94.247.205  Bcast:xxx.94.247.207  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16

eth0:4    Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx
          inet addr:xxx.94.247.206  Bcast:xxx.94.247.207  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16

eth0:5    Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13998614 (13.3 MiB)  TX bytes:13998614 (13.3 MiB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.0.0.1  P-t-P:10.0.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

Now from what i read openvpn needs to connect to eth0 through tap so i removed eth0

and added:
```

auto br0
iface br0 inet static
address xxx.94.247.202
network xxx.94.247.200
netmask 255.255.255.248
broadcast xxx.94.247.207
bridge_ports eth0 tap0
pre-up openvpn --mktun --dev tap0

```

However when i try to bring it up it i can't reconnect to my server.

Do i need to rename eth0:2 to br0:2 etc? 

Is there anything else i'm overlooking? Also should i use xxx.94.247.200 or network xxx.94.247.201 for network, 200 doesn't seem reachable...

Also how do i set it up so i can connect trough the vpn from my local client via the tap0? From their manuals (openvpn) it says to bridge a private ip range on the server however my interface is on a public ip so how do i get this going so my client get's an ip? Do i have to assign one of my 5 public ip's to tap0 or client, if i do how do i do that? 

Any help would be great, i've been pulling my hairs for a while trying to get the networking up and i'm failing big time.

---


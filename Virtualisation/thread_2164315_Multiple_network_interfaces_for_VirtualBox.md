---
title: "Multiple network interfaces for VirtualBox"
date: 2013-07-31
forum: Virtualisation
---

### Post by milad on 2013-07-31
Is it possible to have both bridged mode and NAT enabled on a virtualbox linux guest? I want bridged adapter as the default one to access my guest's home directory from other computers on the network (using samba), and at the same time I need guest to access the host locally. Does this even make sense?

I tried enabling both adapters in VirtualBox and I can see both of them in my guest now. I can ping the first one (192.168.39.107) from my windows host but not the second one (10.0.3.15).

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:10:ad:0d  
          inet addr:192.168.39.107  Bcast:192.168.39.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe10:ad0d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:302443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64619 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113996112 (113.9 MB)  TX bytes:34120651 (34.1 MB)

eth1      Link encap:Ethernet  HWaddr 08:00:27:99:1c:13  
          inet addr:10.0.3.15  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe99:1c13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1477 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1785 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:930120 (930.1 KB)  TX bytes:215640 (215.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:8864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19021832 (19.0 MB)  TX bytes:19021832 (19.0 MB)

```

My /etc/interfaces does not seem to have much in it:

```
$ more /etc/network/interfaces 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

And some other diagnostics (which don't make sense to me):

```
$ netstat -i
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0    303846      0      0 0         64931      0      0      0 BMRU
eth1       1500 0      1478      0      0 0          1795      0      0      0 BMRU
lo        65536 0      8911      0      0 0          8911      0      0      0 LRU


$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         192.168.39.254  0.0.0.0         UG        0 0          0 eth0
10.0.3.0        *               255.255.255.0   U         0 0          0 eth1
link-local      *               255.255.0.0     U         0 0          0 eth1
192.168.39.0    *               255.255.255.0   U         0 0          0 eth0
```

---

### Post by wildmanne39 on 2013-07-31
*Thread moved to **Virtualisation**.*

---

### Post by euxneks on 2013-07-31
Check out the options to forward ports. If you figure out the services you want to access from the virtualbox machine (they listen on specific ports), you can forward a port on the Host machine to the guest machine and not have to have multiple networks set up for your VM.  I have it set up on my machine to forward a port not in use on the host to a guest port for webserving as well as another service.

Settings>network>advanced>port forwarding

Keep in mind the HOST IP is the IP address you want to listen on, so whatever the other machines see as your host machine's IP address, and the GUEST IP is the ip address as the guest OS sees it.

Hope this puts you on the road to solving it :)

---


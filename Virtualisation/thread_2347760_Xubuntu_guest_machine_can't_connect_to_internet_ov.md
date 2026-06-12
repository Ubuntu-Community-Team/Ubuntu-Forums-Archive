---
title: "Xubuntu guest machine can't connect to internet over bridged adapter connection"
date: 2016-12-28
forum: Virtualisation
---

### Post by peter1897 on 2016-12-28
I have Windows 7 host and Xubuntu guest virtualbox machines. The guest machine can't connect to internet over bridged connection. From the guest machine i can ping the host and other devices connected to the LAN network, but i can't ping the router - I get 'Destination Host Unreachable' when i try to ping the router. Also, i can ping the guest machine from the host machine. 

Any idea why the guest machine can't connect to internet and why it can't ping the router when it can ping the host? Also, if i switch to NAT the guest can access internet but with bridged connection it can't.

This is the output of the ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 08:00:27:5e:ca:2e  
          inet addr:192.168.31.104  Bcast:192.168.31.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe5e:ca2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43930 (43.9 KB)  TX bytes:27323 (27.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12485 (12.4 KB)  TX bytes:12485 (12.4 KB)
```



This is the content of the interfaces file:
```
osboxes@osboxes:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

---

### Post by DuckHook on 2016-12-28
[LIST=1]
[*]You might have your router more IP constrained than your internal LAN. In default configuration, most routers will only permit/hand out &#8776;254 IPs in the 192.168.**1**.xxx range, so yours looks customized.
[*]What is your host's IP? In NAT configuration, your guest connection is piggybacked onto your host IP, so it's no surprise that it would work.
[*]Do you have a separate DHCP/DNS server other than your router?
[/LIST]
You may wish to check your router settings for outgoing IP restrictions.

---


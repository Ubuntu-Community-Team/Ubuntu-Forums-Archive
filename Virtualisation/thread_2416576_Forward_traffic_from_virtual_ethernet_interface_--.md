---
title: "Forward traffic from virtual ethernet interface --&gt; Virtual machine"
date: 2019-04-11
forum: Virtualisation
---

### Post by buksa on 2019-04-11
Hi all. 

I have a Ubuntu 16.04 server with VMware and a Ubuntu 16.04 guest OS. 
The VM host has 1 ethernet interface with a static IP, and also I have added eth0:0 in the [FONT=arial]/etc/network/interfaces file. 
I have a second global IPv4 address that I have assigned to eth0:0 
When I ssh into the second IP, it works. I can also traceroute back to it and it looks like it works as it should. 

I want all traffic that goes to eth0:0 to be redirected to my virtual machine's network interface so that I can run those two as if they were two physical and independent machines. 
I've tried to find some good example online, in forums, etc. But the only similar cases I've run into is where one want to forward traffic from certain ports only. What I want is to just send every little package that comes in to my second IP/eth0:0, straight through --> VM-interface. 

I understand that I somehow need to bridge eth0:0 with one of the vmware virtual adapters. So that they would be on the same network so that traffic can be sent between the gateway interface and the guest vm. I also have figured out that I need to do this by using iptables somehow. I have come so far that I have enabled my kernel to allow ipv4 forwarding so that is a go. 

ifconfig gives: 

[/FONT]```
eth0      Link encap:Ethernet  HWaddr 54:04:a6:b4:94:2d          inet addr:148.251.237.28  Bcast:148.251.237.31  Mask:255.255.255.224
          inet6 addr: fe80::5604:a6ff:feb4:942d/64 Scope:Link
          inet6 addr: 2a01:4f8:202:8027::2/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:22229 (22.2 KB)  TX bytes:23425 (23.4 KB)


eth0:0    Link encap:Ethernet  HWaddr 54:04:a6:b4:94:2d
          inet addr:148.251.237.40  Bcast:148.251.237.63  Mask:255.255.255.224
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:354 (354.0 B)  TX bytes:354 (354.0 B)


vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01
          inet addr:172.16.147.1  Bcast:172.16.147.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08
          inet addr:192.168.192.1  Bcast:192.168.192.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```[FONT=arial]

Also I'm not quite sure why VMware creates both vmnet1 and 8. Also, I'm not sure if the vmnet1 and 8 even are virtual interfaces at all, since they do not appear in the ubuntu interfaces file - and if it's possible to redirect anything at all to these? Some things aren't 100% clear for me here. 

Any advice is appreciated. Just ask if you need more input. 

This is my interfaces file: 

[/FONT]```
source /etc/network/interfaces.d/*


auto lo
iface lo inet loopback
iface lo inet6 loopback


auto eth0
iface eth0 inet static
  address 148.251.237.28
  netmask 255.255.255.224
  gateway 148.251.237.1
  # route 148.251.237.0/27 via 148.251.237.1
  up route add -net 148.251.237.0 netmask 255.255.255.224 gw 148.251.237.1 dev eth0


auto eth0:0
iface eth0:0 inet static
  address 148.251.237.40
  netmask 255.255.255.224
  gateway 148.251.237.1
  # route 148.251.237.0/27 via 148.251.237.1
  up route add -net 148.251.237.0 netmask 255.255.255.224 gw 148.251.237.1 dev eth0:0

iface eth0 inet6 static
  address 2a01:4f8:202:8027::2
  netmask 64
  gateway fe80::1
```

---

### Post by buksa on 2019-04-12
> [COLOR=#000000]The VM host has 1 ethernet interface with a static IP, and also I have added eth0:0 in the [/COLOR][COLOR=#000000][FONT=arial]/etc/network/interfaces file. [/FONT][/COLOR]
What I ment here was 1 PHYSICAL ethernet interface.

---


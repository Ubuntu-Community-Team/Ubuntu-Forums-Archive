---
title: "IPsec to virbr0 subnet KVM/QEMU (host acts as router)"
date: 2022-12-16
forum: Server Platforms
---

### Post by volkswagner on 2022-12-16
Greetings,

I'm struggling with setting up Strongswan IPsec VPN between home and cloud
hosted hardware server acting as KVM host.

The host is running 20.04 server with KVM and Strongswan.
Home network has MikroTik router/firewall with IPsec.

I have the tunnel up and running but it only works in one direction
(from home to host/VMs). The goal is to be able to reach NATed VMs
from home and also allow the VMs to reach my home subnet.

I can reach the VMs without issue, I can ping hosts in both directions, but
services like SSH & HTTP don't work from the hosted server to my home LAN.

It acts like a firewall issue, but I'm out of things to try. It seems like the virbr0
has some inherent limitations combined with the policy based routing of IPsec.

I also tried connecting two KVM hosts using Strongswan, with a similar symptom.
Ping works but services do not. This is in both directions (virbr0 on both sides).

Does anyone know if the virbr0 has limitations in this regard?

[Here's]("https://pastebin.ubuntu.com/p/kpjCHGGY8F/") IPtables on the host running KVM.

[This]("https://pastebin.ubuntu.com/p/65wR7qr3Fv/") is my IPsec config.

Crude diagram:
[VM1]=192.168.222.155 >> [kvmhost]=51.52.53.54 >>> [Internet]  <<< 123.10.10.22=[MikroTik] << [Home_LAN]=192.168.7.0/24

With the above I can ssh from any computer on Home_LAN to VM1 via ssh, I can't 
ssh from VM1 to any Home_LAN device, but I can ping from VM1 to Home_LAN.
I don't think this is an issue with my Mikrotik firewall because I get the same symptom
when trying to tunnel between two strongswan IPsec KVMhosts via the virbr0 network.

Any thoughts on what to try? Should this be a supported scenario or should I create
a VPN server virtual machine on the "LAN/virbr0" and route that way?

Typically I don't NAT IPsec traffic. I exclude it from the masquerade rule. Oddly [this tutorial]("https://sysadmins.co.za/setup-a-site-to-site-ipsec-vpn-with-strongswan-on-ubuntu/")
seems to do the opposite.

I don't normally need to add any routes with IPsec. The policy just recognizes the "interesting traffic
and sends it via the tunnel. I noticed if I ran traceroute from VM1, the first hop was the public
interface IP of the host, not virbr0 IP. I added a route and now it show 192.168.222.1 as the first
hop, but it still doesn't route via the tunnel.

Could this be a layer2 vs layer3 issue? Is ICMP (working ping command) using layer2?

I'm truly stumped as to why ping works but no other services, they just hang/time out.

---

### Post by volkswagner on 2023-04-03
I finally get some help from ##strongswan.

I had to change the order of my NAT rules.
Traffic was not recognized by the ipsec policy
because it was hitting NAT rules too early.

Here's the modified NAT from iptables:

```

*nat
:PREROUTING ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
:LIBVIRT_PRT - [0:0]
-A PREROUTING -s 123.10.10.22/32 -i enp1s0f0 -p tcp -m tcp --dport 52022 -j DNAT --to-destination 192.168.222.155:22
[COLOR="#FF0000"]-A POSTROUTING -m policy --pol ipsec --dir out -j ACCEPT[/COLOR]
-A LIBVIRT_PRT -s 192.168.222.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE -m comment --comment "this is for ipsec to srv"
-A LIBVIRT_PRT -s 192.168.222.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE -m comment --comment "this is for ipsec to srv"
-A LIBVIRT_PRT -s 192.168.222.0/24 ! -d 192.168.7.0/24 -p tcp -j MASQUERADE -m comment --comment "this is for ipsec to house"
-A LIBVIRT_PRT -s 192.168.222.0/24 ! -d 192.168.7.0/24 -p udp -j MASQUERADE -m comment --comment "this is for ipsec to house"
-A POSTROUTING -j LIBVIRT_PRT
-A LIBVIRT_PRT -s 192.168.222.0/24 -d 224.0.0.0/24 -j RETURN
-A LIBVIRT_PRT -s 192.168.222.0/24 -d 255.255.255.255/32 -j RETURN
-A LIBVIRT_PRT -s 192.168.222.0/24 ! -d 192.168.0.0/16 -p tcp -j MASQUERADE --to-ports 1024-65535
-A LIBVIRT_PRT -s 192.168.222.0/24 ! -d 192.168.0.0/16 -p udp -j MASQUERADE --to-ports 1024-65535
-A LIBVIRT_PRT -s 192.168.222.0/24 ! -d 192.168.0.0/16 -j MASQUERADE

```

---


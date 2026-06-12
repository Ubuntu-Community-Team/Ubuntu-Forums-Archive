---
title: "[SOLVED] Can't get a Cisco VPN running on a Virtualbox XP guest on a Hardy host"
date: 2008-09-10
forum: Virtualisation
---

### Post by tigercorp on 2008-09-10
Hi,

I've got Virtualbox 1.6.4 running on Hardy (downloaded and installed last week).
An XP guest has the Cisco VPN client 5.0... installed and will connect out of the box using UDP.  

*** I need it to work on TCP port 10000 ***

The XP guest can access the internet fine.

The Hardy host can telnet to the vpn server on port 10000. 
There's no firewall set up on the host (or at least I haven't installed/configured any - I'm new to linux)

I've set up port forwarding for TCP 10000.

Running
```
VBoxManage getextradata XP-Work enumerate
```
returns

Key: VBoxInternal/Devices/pcnet/0/LUN#0/Config/vpn_10k/HostPort, Value: 10000
Key: VBoxInternal/Devices/pcnet/0/LUN#0/Config/vpn_10k/GuestPort, Value: 10000
Key: VBoxInternal/Devices/pcnet/0/LUN#0/Config/vpn_10k/Protocol, Value: TCP


When I try to connect, it just doesn't reach the server and times out.  It does work with UDP though.

Any ideas?

---

### Post by tigercorp on 2008-09-21
After trying some stuff out as suggested on the Virtualbox forums, I still haven't been able to get this to work with NAT and port 10k on TCP.

It does work however using Host Interface Networking and bridging, so i'm going with that...

---


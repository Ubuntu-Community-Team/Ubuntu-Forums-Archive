---
title: "CONNECTIVITY Problem Server 12.04 Machines running in VMware 8 Please HELP"
date: 2013-03-12
forum: Virtualisation
---

### Post by CyberVikingo on 2013-03-12
Hi to all,
I'm a new enthusiast of Ubuntu but I'm experiencing a connectivity issue in the next basic scenario:

Virtual Machine 1 (DMZ):
Network Adapter: LAN segment 10.0.4.0 (I also used VMnet4)
#Ubuntu's Server 12.04 configuration is:
auto eth0
iface eth0 inet static
address: 10.0.4.16
netmask: 255.255.255.224
network: 10.0.4.0
broadcast: 10.0.4.31
gateway: 10.0.4.1

route add -net 10.0.4.32 netmask 255.255.255.224 gw 10.0.4.1 dev eth0
#When route:
default       10.0.4.1   0.0.0.0               UG   100   0   0   eth0
10.0.4.0     *            255.255.255.224   U     0      0   0   eth0
10.0.4.32   10.0.4.1   255.255.255.224   UG   0      0   0   eth0
#Connectivity tests from 10.0.4.16:
ping 10.0.4.16   OK
ping 10.0.4.1    OK
ping 10.0.4.33   OK
ping 10.0.4.44   HERE IS THE PROBLEM!!! I'm not even get UNREACHABLE NETWORK response.

Virtual Machine 2 (FIREWALL):
Network Adapter: NAT
Network Adapter 2: LAN segment 10.0.4.0 (I also used VMnet4)
Network Adapter 3: LAN segment 10.0.4.32 (I also used VMnet2)
#Ubuntu's Server 12.04 configuration is:
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet static
address: 10.0.4.1
netmask: 255.255.255.224
network: 10.0.4.0
broadcast: 10.0.4.31
auto eth2
iface eth2 inet static
address: 10.0.4.33
netmask: 255.255.255.224
network: 10.0.4.32
broadcast: 10.0.4.63

route add -net 10.0.4.0 netmask 255.255.255.224 gw 10.0.4.1 dev eth1
route add -net 10.0.4.32 netmask 255.255.255.224 gw 10.0.4.33 dev eth2
#When route:
default       10.0.0.2    0.0.0.0                UG   100   0   0   eth0
10.0.0.0     *             255.255.255.0       U     0      0   0   eth0
10.0.4.0     10.0.4.1    255.255.255.224   UG   0      0   0   eth1
10.0.4.32   10.0.4.33   255.255.255.224   UG   0      0   0   eth2
#UFW is disabled:
service ufw status
ufw stop/waiting
#Connectivity tests:
ping 10.0.4.1     OK
ping 10.0.4.33   OK
ping 10.0.4.16   OK
ping 10.0.4.44   OK

Virtual Machine 3 (LAN):
Network Adapter: LAN segment 10.0.4.32 (I also used VMnet2)
#Ubuntu's Server 12.04 configuration is:
auto eth0
iface eth0 inet static
address: 10.0.4.44
netmask: 255.255.255.224
network: 10.0.4.32
broadcast: 10.0.4.63
gateway: 10.0.4.33

route add -net 10.0.4.0 netmask 255.255.255.224 gw 10.0.4.33 dev eth0
#When route:
default       10.0.4.33   0.0.0.0               UG   100   0   0   eth0
10.0.4.0     10.0.4.33   255.255.255.224   UG   0      0   0   eth0
10.0.4.32   *              255.255.255.224   U     0      0   0   eth0
#Connectivity tests from 10.0.4.44:
ping 10.0.4.44   OK
ping 10.0.4.1     OK
ping 10.0.4.33   OK
ping 10.0.4.16   HERE IS THE PROBLEM!!! I'm not even get UNREACHABLE NETWORK response.

I do not understand why the LAN machine can't ping to the DMZ machine  and vice versa if the static routes are already configured and the  firewall (ufw) is disabled.
I'd really appreciate any help or guidance.
Thank you in advance for your time and cooperation.

---


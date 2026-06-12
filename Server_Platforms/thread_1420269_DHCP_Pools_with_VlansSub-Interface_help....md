---
title: "DHCP Pools with Vlans/Sub-Interface help..."
date: 2010-03-02
forum: Server Platforms
---

### Post by dvlabguy on 2010-03-02
Hi, I'm new to the Ubuntu forum and installed server 9.10 for the first time and going to use an Ubuntu Server for my lab DHCP/DNS server, replacing an older Cisco router that use DHCP Pools, NAT, ACL, etc.
 
(See configs below)
 
I have vlans and sub-interfaces (500-999) that use 12 IP's per Vlan/sub-interface.
(See Cisco example below)
 
ip dhcp pool vlan500
network 10.115.50.0 255.255.255.240
dns-server 10.15.12.9 10.10.1.10
default-router 10.115.50.1
domain-name dvlab.acterna.com
lease 10
!
ip dhcp pool vlan501
network 10.115.50.16 255.255.255.240
dns-server 10.15.12.9 10.10.1.10
default-router 10.115.50.17
domain-name dvlab.acterna.com
lease 10
!
ip dhcp pool vlan502
network 10.115.50.32 255.255.255.240
dns-server 10.15.12.9 10.10.1.10
default-router 10.115.50.33
domain-name dvlab.acterna.com
lease 10
!
!
interface GigabitEthernet5/0.500
encapsulation dot1Q 500
ip address 10.115.50.1 255.255.255.240
ip access-group 100 in
ip nat inside
no cdp enable
!
interface GigabitEthernet5/0.501
encapsulation dot1Q 501
ip address 10.115.50.17 255.255.255.240
ip access-group 100 in
ip nat inside
no cdp enable
!
interface GigabitEthernet5/0.502
encapsulation dot1Q 502
ip address 10.115.50.33 255.255.255.240
ip access-group 100 in
ip nat inside
no cdp enable
!
ip default-gateway 10.15.8.1
ip nat pool dvlab 10.15.12.225 10.15.12.254 netmask 255.255.255.0
ip nat inside source list 1 pool dvlab
ip nat inside source static 10.115.28.20 10.15.12.41 extendable
ip nat inside source static 10.115.28.1 10.15.12.239 extendable
ip nat inside source static 10.115.28.3 10.15.12.237 extendable
ip classless
ip route 0.0.0.0 0.0.0.0 10.15.12.1
no ip http server
ip ospf name-lookup
!
access-list 100 permit ip any any log
access-list 105 permit ip 10.115.0.0 0.0.255.255 10.15.12.0 0.0.0.255
no cdp run
!
!
route-map nattest permit 10
match ip address 105
set ip next-hop 10.15.12.1
 
(IP/Vlan address range)
Available Addresses NetMask 
VLAN Gateway Start End Address Bits
500 10.115.50.1 10.115.50.2 10.115.50.14 255.255.255.240 28
501 10.115.50.17 10.115.50.18 10.115.50.30 255.255.255.240 28
502 10.115.50.33 10.115.50.34 10.115.50.46 255.255.255.240 28
 
My main questions...
 
1) Do I need to configure sub-interfaces just as the cisco environment in the dhcp3-server?
 
2) Any examples how to configure this to work as it does in the Cisco router?
 
Many thanks!

---


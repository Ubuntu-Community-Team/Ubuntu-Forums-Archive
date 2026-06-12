---
title: "Problem with vlan"
date: 2014-07-20
forum: Server Platforms
---

### Post by kenaj83 on 2014-07-20
[COLOR=#000000][FONT=Arial]hi i have a problem with vlan's on my network. i have server dell poweredge r210 II and then install vmware vSphere hypervisor 5.5. Next i create virtual machine with ubuntu server 14.04. Network plan is that: connection from ISP to ubuntu server (first NIC) then to cisco sg200 -26P as trunk port toG25. First seven ports (on switch) are configured as vlan port G1-vlan 10, G2-vlan 20... G7-vlan 70, as untagged with access mode.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Ubuntu server configuration : -apt-get install vlan -/etc/network/interfaces like that (the rest vlan's looks the same)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]auto eth1
 iface eth1 inet static
 address 192.168.1.2
 netmask 255.255.255.0
 gateway 192.168.1.1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iface vlan10 inet static
 address 192.168.10.1
 netmask 255.255.255.0
 network 192.168.1.0
 broadcast 192.168.10.55
 vlan_raw_device eth1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]-enable ip forwarding, edit /etc/sysctl.conf file:i change net.ipv4.ip_forward from 0 to 1 -modprobe 8021q -enabled /proc/sys/net/ipv4/ip_forward[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]-/proc/net/vlan[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]when i connect my laptop with static ip 192.168.10.10 netmask 255.255.255.0 gateway 192.168.10.1 to G1 port (vlan10) i cant ping my gateway. i have dhcp configuraton file[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]example vlan10

vlan10[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]subnet 192.168.10.0 netmask 255.255.255.0 { 
range 192.168.10.2 192.168.10.100; 
option routers 192.168.10.1; 
option domain-name "eth1_vlan10";[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]even that my laptop can't get ip address from dhcp.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I installed the same Configuration in the second computer and still the same. Can anyone help me[/FONT][/COLOR]

---


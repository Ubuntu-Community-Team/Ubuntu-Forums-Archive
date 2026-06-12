---
title: "DHCP server on trunk interface"
date: 2011-04-30
forum: Server Platforms
---

### Post by terminator14 on 2011-04-30
I'm a network tech and I have setup a Linux Server (11.04 Final) at work to act as a gateway for several networks, which will replace our old hardware that performs a similar role. The setup is basically this:

ISP --> Linux Server --> Cisco Switch (VLAN 2, 4, 6)

So the Ubuntu server is going to have the ISP connected to one interface (eth1), and the other interface will be a trunk port from the server to the switch using 802.1q (eth0). The switch has 3 VLANs for 3 different networks. The server needs to allow each network access to the internet, as well as assign IPs to hosts on each network with DHCP.

This is what I did to set it up:

[LIST]
[*]sudo apt-get install vlan
[*]added 8021q to /etc/modules
[*]created sub-interfaces eth0.2, eth0.4, eth0.6 using /etc/network/interfaces and assigned each sub-interface an IP on their VLAN which will be the default gateway on that subnet
[*]enabled ipv4 forwarding
[*]enabled NAT on eth1 with "sudo iptables --table nat -A POSTROUTING -o eth1 -j MASQUERADE"
[*]installed dhcp3-server
[*]activated dhcpd in /etc/default/isc-dhcp-server on interfaces eth0.2, eth0.4, and eth0.6
[*]configured dhcp3-server as such (here's an excert of dhcpd.conf):
[/LIST]

> #ISP subnet declaration
subnet 200.0.0.0 netmask 255.255.255.248 {
}

#Subnet 1
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.10 192.168.1.254;
  option domain-name-servers 8.8.8.8;
  option domain-name "ourcompany.local";
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
  default-lease-time 600;
  max-lease-time 7200;
}

#Subnet 2
subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.10 192.168.2.254;
  option domain-name-servers 8.8.8.8;
  option domain-name "ourcompany.local";
  option routers 192.168.2.1;
  option broadcast-address 192.168.2.255;
  default-lease-time 600;
  max-lease-time 7200;
}

#Subnet 3
subnet 192.168.3.0 netmask 255.255.255.0 {
  range 192.168.3.10 192.168.3.254;
  option domain-name-servers 8.8.8.8;
  option domain-name "ourcompany.local";
  option routers 192.168.3.1;
  option broadcast-address 192.168.3.255;
  default-lease-time 600;
  max-lease-time 7200;
}

This server has been configured, but not put in place because the old hardware is still running the network and downtime for the network is scheduled to happen in a couple of hours. Testing the server in a virtual environment (with an unused cisco switch with a similar vlan configuration) could take several more days, which we do not have - the server is basically going up in 2 hours and it needs to work.

Should the dhcpd.conf's subnets be encapsulated by a single "shared-network" statement because all 3 networks are going through the same interface on the server (the trunk)?

Am I forgetting anything? Any advice to make it better/faster/stronger?

---

### Post by elico on 2011-04-30
i thing you should have another rule on the iptables in order to make it work.

you should have some 802q module for iptables and to make sure the dhcp server will get the right dhcp request add
to the iptables rules that will allow udp ports 67+68 on each virutal interface only for specific marked VLAN.
cause you have the switch that will mark each client packets with VLAN markes but will forward all of the client to the same physical interface and you have "forward" enabled on the linux kernel.(should\must)
and if im not wrong there is an options of vlan on dhcp so it will make it less painful.

and you should bound every subnet to the virtual interface and not globally.

Regards Elico

edit:
found a bug on DHCP vlan
[https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/295520](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/295520)
so you better look at it before doing anything with dhcp and vlan.

---

### Post by terminator14 on 2011-05-05
> **elico said:**
> i thing you should have another rule on the iptables in order to make it work.

you should have some 802q module for iptables and to make sure the dhcp server will get the right dhcp request add
to the iptables rules that will allow udp ports 67+68 on each virutal interface only for specific marked VLAN.
cause you have the switch that will mark each client packets with VLAN markes but will forward all of the client to the same physical interface and you have "forward" enabled on the linux kernel.(should\must)
and if im not wrong there is an options of vlan on dhcp so it will make it less painful.

and you should bound every subnet to the virtual interface and not globally.

Regards Elico

edit:
found a bug on DHCP vlan
[https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/295520](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/295520)
so you better look at it before doing anything with dhcp and vlan.

When I plugged in the server, it worked perfectly. The only problem I ran into was with the cisco business switch which required some weird trickery to create a new VLAN - this had nothing to do with the server though. In my case, I did not need an 8021q module for iptables since I did not need to secure it to such an extent that DHCP requests from a different vlan on a single virtual interface would be denied. Could that even happen?

I ended up not using any specific vlan options for dhcp, and only configuring the subinterfaces accordingly. Basically, the subinterfaces get assigned to vlans automatically depending on their name ending:

eth0.2 to VLAN 2
eth0.4 to VLAN 4
eth0.6 to VLAN 6

Then I gave each interface an IP and told the DHCP server to give out IPs on those subnets (as seen in the dhcpd.conf below). Basically, that caused dhcpd to look at each subinterface and go "this interface is in this subnet, and I'm supposed to assign addresses in this range on this subnet", so that's how it knows which ip range belongs on which interface.

How would I bind a subnet to a virtual interface? Is there an option in dhcpd.conf to do that? Would this really improve security all that much?

And thanks for the link to the bug - I'll take a closer look at it if I run into problems with VLANs and DHCP, but for now, everything seems to work great.

The entire setup is basically a temporary solution until our new Cisco router arrives (which could take weeks). Our old hardware's CPU usage was always at 100% and was slowing us down, so this was our temporary solution. It works pretty good, and overall I'm pretty happy with it.

Thanks for the info.

---


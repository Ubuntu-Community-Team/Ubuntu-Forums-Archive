---
title: "Bridge installation (Debian/Ubuntu)"
date: 2006-03-17
forum: Server Platforms
---

### Post by tepegoz on 2006-03-17
Hi all,
I am trying to install a bridge using ubuntu (or debian). Is there a good tutorial? Or any other documentation?

Thanks

---

### Post by tomski on 2006-04-27
im trying to do the exact same thing with:

ubuntu (server install)
2 NIC's (eth0 =WAN, eth1 =LAN
shorewall (for firewall)
webmin (with shorewall-webmin for configuration)

when i say WAN in the above its not really, as its another network (192.168.0.0) with all ip's on this network being provided via DHCP from the router/Gateway (DG834G) that is connected to a 2mb adsl line, so yes im ' double NAT'ing ' but it should work.

i have managed to setup a normal router/firewall with the above but when i follow the instructions on the shorewall site in documentation (using my current shorewall configs with some zone changes) i cant get a connection to pass over the bridge.

 this is what i have done so far:
shorewall stop
ifconfig eth0 0.0.0.0
ifconfig eth1 0.0.0.0
brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1
ifconfig br0 192.168.0.15 netmask 255.255.255.0 up
then change the ip of the pc behind the bridge/firewall to one in the same network (192.168.0.65)

on the out set i decided that after doing the above and i could ping [www.bbc.co.uk](www.bbc.co.uk) from behind the bridge/firewall then i would add the following to /etc/network/interfaces :

auto br0
iface br0 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        pre-up /sbin/ip link set eth0 up
        pre-up /sbin/ip link set eth1 up
        pre-up /usr/sbin/brctl addbr br0
        pre-up /usr/sbin/brctl addif br0 eth0
        pre-up /usr/sbin/brctl addif br0 eth1


i would like to figure this bridge/firewall out because i work for an ISP and its in our intrest to keep servers protected so if i can learn about bridging & layer2 routing(MAC address) then we can have transparent firewalls in front of our servers (our sys admin are quite busy)

---


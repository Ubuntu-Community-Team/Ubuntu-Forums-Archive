---
title: "Shorewall"
date: 2009-09-23
forum: Server Platforms
---

### Post by black_shadow on 2009-09-23
Hello All 

I am having problems setting up shorewall, I have the following configuration
eth0 > net
eth1 > internal

I have DHCP and DNS running on the server when I plug a PC into the LAN cable I dont get a IP address. This only happens when connected to my ISP's cable modem when I have it set to my internal LAN on ETH0 I get an IP from ETH1 with PC plugged in.

If you need more information then plz ask.

Mike

---

### Post by black_shadow on 2009-09-24
Please find the config files for shore wall.

Zones :-

fw    firewall
net    ipv4
loc    ipv4

Interfaces :-

net     eth0            detect          dhcp,tcpflags,routefilter,nosmurfs,logmartians
loc     br0             detect          dhcp,tcpflags,detectnets,nosmurfs,routeback

Default Policy :-

loc        net        ACCEPT
net        all        DROP     info
$FW        net        ACCEPT        info
$FW        loc        ACCEPT        info
$FW        all        ACCEPT        info
net        $FW        DROP        info
net        loc        DROP        info
all        all        REJECT        info

Rules :- 

ACCEPT        loc        $FW        tcp    10000
ACCEPT        net        $FW        tcp    10000
ACCEPT         net           $FW        tcp    80
ACCEPT         loc           $FW           tcp    80
DNS/ACCEPT    $FW        net
DNS/ACCEPT    loc        $FW
SSH/ACCEPT    loc        $FW
Ping/ACCEPT    loc        $FW
Ping/ACCEPT    net    $FW
ACCEPT        $FW        loc        icmp
ACCEPT        $FW        net        icmp
ACCEPT          loc             $FW             icmp
ACCEPT          net             $FW             icmp

MASQ :-

eth0                    br0

When Stopped :-

br0    

My /etc/network/interfaces files :-
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# Set up the local loopback interface
auto lo
iface lo inet loopback

# Set up the external interface
#
# Don't forget to change eth0 to the proper name of the external
# interface if applicable.
#
auto eth0
iface eth0 inet dhcp

# Set up the internal wireless network
#
# Don't forget to change wlan0 to the proper name of the internal
# wireless network interface if applicable.
#
# If you would like to use WEP, uncomment the line 'wireless-key'
# and replace '<key goes here>' with a WEP key.
# 
# You may also change the network essid and channel.
#
auto wlan0
iface wlan0 inet manual 
#    wireless-mode Managed
    #wireless-mode Master
    wireless-mode Ad-hoc
    wireless-essid GateKeeper
    wireless-channel 1
    wireless-key 0d8430cde3e6f695e7989d8813

# Set up the internal wired network
#
# It's not necessary to bring this interface up as the bridge
# we are about to create does this. Leave these lines commented.
#
#auto eth1
#iface eth1 inet manual


# Set up the internal wired/wireless network bridge
#
# Don't forget to change wlan0 and eth1 to the proper name of
# the internal wired and wireless interfaces if applicable.
#
auto br0

iface br0 inet static
    address 192.168.168.101
    network 192.168.168.0
    netmask 255.255.255.0
    broadcast 192.168.0.255
    bridge-ports eth1 wlan0

Regards Mike

---


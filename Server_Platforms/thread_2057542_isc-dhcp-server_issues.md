---
title: "isc-dhcp-server issues"
date: 2012-09-13
forum: Server Platforms
---

### Post by ellisgl on 2012-09-13
I'm setting up a router/AP/firewall device with with Ubuntu server, and have an issue with isc-dhcp-server when I boot. I've noticed that my eth0 device is receiving an IP from it, instead of from my real gateway, and I haven't figured out how to get isc-dhcp-server to stop it.

Configs:
/etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# Lan network interface
#auto eht1
#iface eht1 inet manual

# wireless wlan0
#allow-hotplug wlan0
#iface wlan0 inet manual

# Wired / Wireless bridge
auto eth1 wlan0 br0
allow-hotplug wlan0
iface br0 inet static
    address      192.168.1.1
    netmask      255.255.255.0
    network      192.168.1.0
    broadcast    192.168.1.255
    bridge_ports wlan0 eth1

/etc/default/isc-dhcp-server
INTERFACES="br0"

/etc/dhcp/dhcpd.conf
ddns-update-style none;
default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

subnet 192.168.1.0 netmask 255.255.255.0 {
        range 192.168.1.100 192.168.1.200;
        option domain-name-servers 192.168.1.1;
        option routers 192.168.1.1;
}


Here's some interesting bits of the syslog:

Sep 13 12:37:55 conxtions-ap kernel: [    2.271460] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
Sep 13 12:37:55 conxtions-ap kernel: [    2.271464] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
Sep 13 12:37:55 conxtions-ap kernel: [    2.271496] e1000e 0000:0d:00.0: Disabling ASPM L0s L1
Sep 13 12:37:55 conxtions-ap kernel: [    2.271512] e1000e 0000:0d:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 13 12:37:55 conxtions-ap kernel: [    2.271538] e1000e 0000:0d:00.0: setting latency timer to 64
Sep 13 12:37:55 conxtions-ap kernel: [    2.271727] e1000e 0000:0d:00.0: irq 43 for MSI/MSI-X


Sep 13 12:37:55 conxtions-ap kernel: [    2.383536] e1000e 0000:0d:00.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:30:48:d4:88:54
Sep 13 12:37:55 conxtions-ap kernel: [    2.383540] e1000e 0000:0d:00.0: eth0: Intel(R) PRO/1000 Network Connection
Sep 13 12:37:55 conxtions-ap kernel: [    2.383724] e1000e 0000:0d:00.0: eth0: MAC: 2, PHY: 2, PBA No: 0100FF-0FF
Sep 13 12:37:55 conxtions-ap kernel: [    2.383735] e1000e 0000:0f:00.0: Disabling ASPM L0s L1
Sep 13 12:37:55 conxtions-ap kernel: [    2.383748] e1000e 0000:0f:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Sep 13 12:37:55 conxtions-ap kernel: [    2.383768] e1000e 0000:0f:00.0: setting latency timer to 64
Sep 13 12:37:55 conxtions-ap kernel: [    2.383923] e1000e 0000:0f:00.0: irq 44 for MSI/MSI-X
Sep 13 12:37:55 conxtions-ap kernel: [    2.496573] e1000e 0000:0f:00.0: eth1: (PCI Express:2.5GT/s:Width x1) 00:30:48:d4:88:55
Sep 13 12:37:55 conxtions-ap kernel: [    2.496576] e1000e 0000:0f:00.0: eth1: Intel(R) PRO/1000 Network Connection
Sep 13 12:37:55 conxtions-ap kernel: [    2.496646] e1000e 0000:0f:00.0: eth1: MAC: 2, PHY: 2, PBA No: FFFFFF-0FF


Sep 13 12:37:55 conxtions-ap kernel: [    7.178286] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 13 12:37:55 conxtions-ap kernel: [    7.178293] ADDRCONF(NETDEV_UP): eth1: link is not ready
 

Sep 13 12:37:55 conxtions-ap kernel: [    7.364635] Bridge firewalling registered


Sep 13 12:37:55 conxtions-ap kernel: [    7.425050] type=1400 audit(1347557874.090:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=634 comm="apparmor_parser"
Sep 13 12:37:55 conxtions-ap kernel: [    7.425065] type=1400 audit(1347557874.090:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=607 comm="apparmor_parser"
Sep 13 12:37:55 conxtions-ap kernel: [    7.425074] type=1400 audit(1347557874.090:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=546 comm="apparmor_parser"
Sep 13 12:37:55 conxtions-ap kernel: [    7.425434] type=1400 audit(1347557874.090:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=634 comm="apparmor_parser"
Sep 13 12:37:55 conxtions-ap kernel: [    7.425463] type=1400 audit(1347557874.090:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=607 comm="apparmor_parser"
Sep 13 12:37:55 conxtions-ap kernel: [    7.425472] type=1400 audit(1347557874.090:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=546 comm="apparmor_parser"
Sep 13 12:37:55 conxtions-ap kernel: [    7.425660] type=1400 audit(1347557874.090:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=634 comm="apparmor_parser"
Sep 13 12:37:55 conxtions-ap kernel: [    7.425696] type=1400 audit(1347557874.090:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=607 comm="apparmor_parser"
Sep 13 12:37:55 conxtions-ap kernel: [    7.425704] type=1400 audit(1347557874.090:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=546 comm="apparmor_parser"
Sep 13 12:37:55 conxtions-ap kernel: [    7.456261] e1000e 0000:0f:00.0: irq 44 for MSI/MSI-X
Sep 13 12:37:55 conxtions-ap kernel: [    7.516120] e1000e 0000:0f:00.0: irq 44 for MSI/MSI-X
Sep 13 12:37:55 conxtions-ap kernel: [    7.516642] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep 13 12:37:55 conxtions-ap kernel: [    7.518438] ADDRCONF(NETDEV_UP): br0: link is not ready



Sep 13 12:37:55 conxtions-ap kernel: [    7.608251] e1000e 0000:0d:00.0: irq 43 for MSI/MSI-X
Sep 13 12:37:55 conxtions-ap kernel: [    7.664098] e1000e 0000:0d:00.0: irq 43 for MSI/MSI-X
Sep 13 12:37:55 conxtions-ap kernel: [    7.664729] ADDRCONF(NETDEV_UP): eth0: link is not ready


Sep 13 12:37:57 conxtions-ap kernel: [   10.700956] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Sep 13 12:37:57 conxtions-ap kernel: [   10.701155] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Sep 13 12:37:57 conxtions-ap dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Sep 13 12:37:57 conxtions-ap dhclient: DHCPREQUEST of 192.168.1.136 on eth0 to 255.255.255.255 port 67
Sep 13 12:37:57 conxtions-ap dhclient: DHCPOFFER of 192.168.1.136 from 192.168.1.1
Sep 13 12:37:57 conxtions-ap dhclient: DHCPACK of 192.168.1.136 from 192.168.1.1
Sep 13 12:37:57 conxtions-ap dhclient: bound to 192.168.1.136 -- renewal in 42389 seconds.

Any clues on how to get this to work? Maybe delay the start of the dhcpd?

---

### Post by ellisgl on 2012-09-13
Edited /etc/init/isc-dhcp-server.conf
changed: 
start on runlevel [2345]

to:
start on (runlevel [2345] and net-device-up IFACE=br0)

Didn't help...

---

### Post by ellisgl on 2012-09-13
I'll try the following when I get to my desk tomorrow and report my findings (since that last one didn't work - I can't access it remotely.. =( )

/etc/init/isc-dhcp-server
start on (filesystem and stopped networking)
start on (filesystem and static-network-up)
start on (filesystem and net-device-up IFACE=br0)

---

### Post by ellisgl on 2012-09-14
/etc/init/isc-dhcp-server.conf
start on (filesystem and static-network-up)

This only work 1/2 the time (ever other reboot)..

Then added "sleep 30" right before ". /etc/default/isc-dhcp-server" (both of them)

/etc/init.d/isc-dhcp-server
added "sleep 30" after set -e.

This only work 1/2 the time also, so I cranked up the sleep times to 60.

Same thing...

Any ideas?

---

### Post by ellisgl on 2012-09-14
Here's another non working config - try to ignore requests from the mac address.

/etc/dhcp/dhcpd.conf
dns-update-style none;
default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

class "self" {
    match if (substring(hardware, 0 , 14) = "00:30:48:d4:88");
    ignore bootp;
    ignore booting;
}

subnet 192.168.1.0 netmask 255.255.255.0 {
    pool {
        range 168.168.1.100 192.168.1.200;
        option domain-name-servers 192.168.1.1;
        option routers 192.168.1.1;
        deny members of "self";
    }    
}

---

### Post by ellisgl on 2012-09-14
Figured it out:
/etc/dhcp/dhclient.conf
added "reject 192.168.1.1;"

---


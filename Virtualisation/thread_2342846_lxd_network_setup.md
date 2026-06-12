---
title: "lxd network setup"
date: 2016-11-10
forum: Virtualisation
---

### Post by alex19742 on 2016-11-10
Hi community,

I managed getting LXD working but have troubles with the network.
My server setup:
*eth *for internet (isp)
*lan* homenet
*wlan* homenet
*lan* and *wlan* are bridged to [I]br0 (nat to eth).

[/I]How can I access the lxd containers through br0 in the homenet and eth from outside?

```
alex@server:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth
iface eth inet dhcp


# Network bridge
auto br0
iface br0 inet static
    address 192.168.3.1
    network 192.168.3.0
    netmask 255.255.255.0
    broadcast 192.168.3.255
    bridge-ports lan wlan

echo "1" > /proc/sys/net/ipv4/ip_forward
echo "1" > /proc/sys/net/ipv4/ip_dynaddr

# load nftable 
up nft -f /etc/nftables.rules

# hostapd und dnsmasq neu starten
up /etc/init.d/hostapd restart
up /etc/init.d/dnsmasq restart
```

```
alex@server:~$ lxc list
+-----------+---------+---------------------+------+------------+----------------+
|   NAME    | STATUS  |        IPV4         | IPV6 |    TYP     | SCHNAPPSCHÜSSE |
+-----------+---------+---------------------+------+------------+----------------+
| mediawiki | RUNNING | 192.168.3.64 (eth0) |      | PERSISTENT | 0              |
+-----------+---------+---------------------+------+------------+----------------+
| owncloud  | STOPPED |                     |      | PERSISTENT | 0              |
+-----------+---------+---------------------+------+------------+----------------+
| torrent   | RUNNING | 192.168.3.70 (eth0) |      | PERSISTENT | 0              |
+-----------+---------+---------------------+------+------------+----------------+
| webserver | STOPPED |                     |      | PERSISTENT | 0              |
+-----------+---------+---------------------+------+------------+----------------+

```

---


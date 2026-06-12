---
title: "Fixing my DHCP server - clients can't access internet"
date: 2008-02-11
forum: Server Platforms
---

### Post by Uaine on 2008-02-11
I'm trying to configure my server as a home router/gateway, and I've been having some trouble getting DHCP properly configured.  Right now, DHCP client machines can successfully get an IP address from my machine.  However, the clients cannot access the internet, and cannot even ping the server

For example, a connecting winxp client can do an ipconfig /all, and it will have an ipaddress assigned by my server, and list the gateway as 192.168.0.1.  The client cannot ping google, nor can it ping 192.168.0.1.

I thought this might be a firewall issue, but after flushing my iptables rules, the client was still unable to ping 192.168.0.1.

I would appreciate any recommendations on what to look at to fix this.  Here is some relevant info:

/etc/network/interfaces:
auto lo
iface lo inet loopback
#WAN
auto eth0
iface eth0 inet dhcp
#LAN
auto eth1
iface eth1 inet static
address 192.168.0.1
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255

/etc/resolv.conf:
search launchmodem.com
nameserver 192.168.1.254
nameserver 192.168.1.254

/etc/dhcp3/dhcpd.conf:
# option definitions common to all supported networks...
option domain-name "launchmodem.com";
option domain-name-servers 192.168.1.254;
option routers 192.168.0.1;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
ddns-update-style none;

authoritative;

default-lease-time 600;
max-lease-time 7200;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.100 192.168.0.128;
# If you want to provided WINS Server
#  option netbios-name-servers 192.168.10.13;
#  option netbios-node-type 8;
}

---

### Post by faulkes on 2008-02-11
Even though you have used a class B (192.168.0.0) address block, you have told it that it is on a class C network (255.255.255.0).  However, you have told dhcp that DNS servers live at 192.168.1.254 - a different network.

This may be a simple timeout issue because of the DNS pointers (although it usually goes through anyways).

You must also make sure that you are using NAT to reach the external world as you are using private IP space.

On the linux server after an XP client has received an address, try to ping the client machine.  As well as turn off any firewall that may be running on the XP side.

I would also look at the routing table (netstat -nr) to see what the default route looks like and any other routes which may exist.

That would be a starting point.

Faulkes

---

### Post by Iowan on 2008-02-11
> auto eth1
iface eth1 inet static
address 192.168.0.1
ne[COLOR="Red"]_t_[/COLOR]work 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255
Couldn't be this simple...

---

### Post by Uaine on 2008-02-11
> **faulkes said:**
> Even though you have used a class B (192.168.0.0) address block, you have told it that it is on a class C network (255.255.255.0).  However, you have told dhcp that DNS servers live at 192.168.1.254 - a different network.

[...]You must also make sure that you are using NAT to reach the external world as you are using private IP space.

[...]I would also look at the routing table (netstat -nr) to see what the default route looks like and any other routes which may exist.
Faulkes
Thanks, I'll look into these things after work - I don't have SSH access to the machine at the moment.

> **Iowan said:**
> Couldn't be this simple...

Actually, no - it isn't that simple.  I typed that by hand instead of a copy-paste, and mistyped.  I'll edit the first post accordingly. Thanks for the catch.

---

### Post by Uaine on 2008-02-14
Alright, I got it working.  Thank you for the suggestions, faulkes - once I configured my NAT (followed directions here: [http://www.section6.net/wiki/index.php/Setting_up_a_Firewall_NAT_using_IPTables](http://www.section6.net/wiki/index.php/Setting_up_a_Firewall_NAT_using_IPTables) ) the internet connection sharing worked fine.

---


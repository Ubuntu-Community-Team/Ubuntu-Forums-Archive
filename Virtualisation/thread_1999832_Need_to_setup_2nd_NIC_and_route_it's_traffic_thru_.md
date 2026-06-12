---
title: "Need to setup 2nd NIC and route it's traffic thru Virtualbox guest OS"
date: 2012-06-08
forum: Virtualisation
---

### Post by dishbert on 2012-06-08
I followed a tutorial and have a setup that routes all Virtualbox traffic through TOR. I use Ubuntu 10.04 as both guest and host.

Now I'd like to connect an additional physical device with a second network card and route it's traffic through the guest OS so that it is anonymous as well.

I've done some searching and can't find anything (that I can understand as a novice) that would guide me through this. I've looked at many articles that talk about setting up Linux as a router, but none seem to fit my particular needs. 

My bridge interface in /etc/network/interfaces looks like this:

# VirtualBox NAT bridge
auto vnet0
iface vnet0 inet static
 address 172.16.0.1
 netmask 255.255.255.0
 bridge_ports none
 bridge_maxwait 0
 bridge_fd 1
        
 up iptables -t nat -I POSTROUTING -s 172.16.0.0/24 -j MASQUERADE
 down iptables -t nat -D POSTROUTING -s 172.16.0.0/24 -j MASQUERADE

/etc/dnsmasq.conf includes this:

interface=vnet0
dhcp-range=172.16.0.2,172.16.0.254,1h

/etc/tor/torrc includes this:

VirtualAddrNetwork 10.192.0.0/10
AutomapHostsOnResolve 1
TransPort 9040
TransListenAddress 172.16.0.1
DNSPort 53
DNSListenAddress 172.16.0.1

Lastly, there is a new file middlebox.sh that looks like this:

#!/bin/sh

# destinations you don't want routed through Tor
NON_TOR="192.168.1.0/24"

# Tor's TransPort
TRANS_PORT="9040"

# your internal interface
INT_IF="vnet0"

iptables -F
iptables -t nat -F

for NET in $NON_TOR; do
 iptables -t nat -A PREROUTING -i $INT_IF -d $NET -j RETURN
done
iptables -t nat -A PREROUTING -i $INT_IF -p udp --dport 53 -j REDIRECT --to-ports 53
iptables -t nat -A PREROUTING -i $INT_IF -p tcp --syn -j REDIRECT --to-ports $TRANS_PORT

Once TOR is restarted and middlebox.sh is run, it works perfectly. 

Again this is NOT my work and I'm totally unqualified to modify it to route a second NIC through the VM without screwing it up royally.  

Right now the HM shows it's connected to eth1 and the VM shows eth0.
I haven't yet physically installed the 2nd NIC, but presumably it will be eth2.

---


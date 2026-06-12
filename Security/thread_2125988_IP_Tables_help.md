---
title: "IP Tables help?"
date: 2013-03-15
forum: Security
---

### Post by TheHammer101 on 2013-03-15
Hey, I understand I'm new, and I apologize if this is posted in the wrong section, but I've currently got Ubuntu Server running. My question is about iptables. Obviously, there are a lot of people trying to teach me through google searches about what it is, and how to go about doing what I need. While I'm spending time learning all the nitty gritty details I would like some help. I am CCNA parts 1&2 completed, so I am not exactly a noob when it comes to all this.

I have a Ubuntu server with 3 ethernet connections that is going to be used as a router, and I am having problems getting it to work correctly. I followed a guide for setting up a NAT router that had me install a DHCP server, after I had set up a bridge between eth1 and eth2, and that's working how I was hoping, I think. It gives out IPs with the correct information, but I have no internet access on the client machines. So, I tried another iptables configuration that is supposedly more secure in /etc/rc.local, but it doesn't give me internet access while cutting out all SSH accessibility. I'll post my file contents, and hope someone can/will help me.

/etc/rc.local

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Delete all previously existing rules
#/sbin/iptables -F
#/sbin/iptables -t nat -F
#/sbin/iptables -t mangle -F
#/sbin/iptables -X

# Always accept loopback traffic
#/sbin/iptables -A INPUT -i lo -j ACCEPT

# Allow established connections
#/sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
#/sbin/iptables -A FORWARD -i eth0 -o br0 -m state --state ESTABLISHED,RELATED $

# ALLOW INCOMING OPEN PORTS TO THE SERVER FROM OUTSIDE HERE


# Allow outgoing connections from the LAN side
#/sbin/iptables -A FORWARD -i br0 -o eth0 -j ACCEPT

# Masquerade
#/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

# Reject any non-established connections from the WAN
#/sbin/iptables -A INPUT -m state --state NEW -i eth0 -j REJECT
#/sbin/iptables -A FORWARD -i eth0 -o br0 -j REJECT

#OLD FORWARDING BITS
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE
exit 0
```

/etc/network/interfaces

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

iface eth1 inet manual

iface eth2 inet manual

auto br0
iface br0 inet static
address 192.168.0.1
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
bridge_ports eth1 eth2
```

/etc/dhcp/dhcpd.conf

```
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "google.com";
option domain-name-servers 8.8.8.8, 8.8.4.4;

default-lease-time 3600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.100 192.168.0.150;
  option subnet-mask 255.255.255.0;
  option broadcast-address 192.168.0.255;
  option routers 192.168.0.1;
}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.
```

---

### Post by Toz on 2013-03-15
Duplicate threads merged.

Please do not create duplicate threads - it dilutes community effort.

---

### Post by TheHammer101 on 2013-03-15
Sorry, I wasn't sure where to place it. Can you remove the duplicate then?

---

### Post by Doug S on 2013-03-15
Most of your iptables rules are actually commented out. iptables rule sets are difficult to read at the best of times, so I'm not sure, but I think if you just uncomment the rules things might work as expected.

---

### Post by TheHammer101 on 2013-03-15
> **Doug S said:**
> Most of your iptables rules are actually commented out. iptables rule sets are difficult to read at the best of times, so I'm not sure, but I think if you just uncomment the rules things might work as expected.

I've tried commenting the currently uncommented ones, and uncommenting those other ones. I gain no internet access from the DHCP clients, and can't SSH into the server with the ones that are currently commented. I'm at a loss.

---

### Post by CharlesA on 2013-03-15
Why not use iptables-restore instead of writing up a bash script to apply the rules?

---

### Post by TheHammer101 on 2013-03-15
I was told to put those in the rc.local file by the guide I was initially following. I'm not sure of another way to save the iptable configurations, what else is there?

---

### Post by CharlesA on 2013-03-15
iptables-save and iptables-restore

If I am testing firewall rules, I will use iptables-apply so I don't locked myself out of the machine.

Check this out:
[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by TheHammer101 on 2013-03-15
With as many iptable commands as I had written it seems such a pain if I wind up losing that all in the process. Is there a way to save them into a file, and to not add them into a non-visible running portion that can be run on command? I also couldn't figure out if it was checking the file each time for what to do, and the commands had to be in order (I assumed the file's rules were loaded into RAM on boot).

Oh, wow, that is the most well written piece on all this I've found. Thank you so much. I'll be looking into that for the next hour or so. LOL Is there any light on my specific situation you'd be willing to pull your hair out for, and share with me?

---

### Post by CharlesA on 2013-03-15
I don't know why you are bridging eth1 and eth2.

If you are going to be using your box as a "router" this might help:
[http://itsecureadmin.com/wiki/index.php/Setup_a_Home_Router_using_IPTables](http://itsecureadmin.com/wiki/index.php/Setup_a_Home_Router_using_IPTables)

---

### Post by TheHammer101 on 2013-03-15
I'm bridging them because I will be adding more Ethernet cards later on and I would like to have a transparent "LAN" network that merely routes layer 2 unless it hits the bridge address. I'll look into what you just showed me more in a minute.

---

### Post by TheHammer101 on 2013-03-15
I plan on adding more Ethernet cards later, and I want a bridge to provide more transparent layer 2 connections like a switch between all the computers hooked up to it.

---


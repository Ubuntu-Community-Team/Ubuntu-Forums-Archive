---
title: "DHCP-settings"
date: 2008-08-27
forum: Server Platforms
---

### Post by Low_E on 2008-08-27
I just installed ubuntu-server on a machine that has to deliver several server-functions.

One of them is the DHCP-function

This machine had two network-devices, eth0, which connects to the local network, and 
eth1 which has a connection to the internet.

As for DHCP, 
I made some changes in the dhcp.conf-file:
> 
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
[B]# CHANGES
option domain-name "secundair";
option domain-name-servers 195.238.2.21,195.238.2.22;[/B]

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
[B]# CHANGES
authoritative;[/B]

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.
[B]# CHANGES
subnet 192.168.250.0 netmask 255.255.255.0 {
}[/B]

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
[B]# CHANGES
subnet 192.168.250.0 netmask 255.255.255.0 {
  range 192.168.250.20 192.168.250.250;
  option domain-name-servers 195.238.2.21,195.238.2.22;
  option domain-name "secundair";
  option routers 192.168.250.254;
  option broadcast-address 192.168.250.255;
  default-lease-time 600;
  max-lease-time 7200;
#}
[/B]
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

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}

also I editted dhcp3-server:

> 
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"

Did I make mistakes? I must have because the pc's on my local network are not receiving an ip-address.

Are there other things to do to make this function on my basic server?

**ALSO**, how do I restart this DHCP-server, s that it functions with the corrected settings?


thx in adavance

Ludo

---

### Post by Iowan on 2008-08-27
Comment out the 3rd change:```
# No service will be given on this subnet, but declaring it helps the
# DHCP server to understand the network topology.
# CHANGES
subnet 192.168.250.0 netmask 255.255.255.0 {
}
``` > As for DHCP,
I made some changes in the dhcp.conf-file:Hope this is a typo and file is dhcpd.conf

Restart with **/etc/init.d/dhcp3-server restart**

---

### Post by Low_E on 2008-08-28
> **Iowan said:**
>  Hope this is a typo and file is dhcpd.conf

indeed it was :)

thx dude!

---


---
title: "[SOLVED] wpad not working?"
date: 2007-09-21
forum: Server Platforms
---

### Post by xyrer on 2007-09-21
Hi, I'm trying to make my dhcp server to serve wpad, I got the proxy.pac file all setuo good, but can't figure out how to enable WPAD, this is my dhcpd.conf:

allow unknown-clients;
#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
ddns-update-style none;


default-lease-time 86400;
max-lease-time 604800;

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
# Satena
subnet 192.168.15.0 netmask 255.255.255.0 {
	authoritative;
	default-lease-time 86400;
	ddns-updates on;
	range dynamic-bootp 192.168.15.21 192.168.15.252;
	}
#option option-252 "http://proxy2/proxy/proxy.pac ";
option wpad-url code 252 = text;
option wpad-url    "http://192.168.15.36/proxy/proxy.pac\n";


I want to avoid re-configuration on browsers, not even putting the pac file address, we are about to change the proxy and that would mean configuring 300 pcs, please someone tell me what do i have wrong?

---

### Post by g14 on 2007-09-22
Why not set up apache to listen as a name based virtual host on wpad.your.domain.com?

That is the default that IE uses I believe. One of my buddies is also working on wpad support for gnome.
[http://code.google.com/p/gnome-proxy/](http://code.google.com/p/gnome-proxy/)
[http://code.google.com/p/wpad/](http://code.google.com/p/wpad/)

---

### Post by xyrer on 2007-09-23
Sounds good to me, but could you be a little more especific? I'm not what you could call an expert, but I have the will to learn.

Thanks.

---

### Post by xyrer on 2007-09-27
I noticed that computers configured with the pac file were much slower than others, so I'm giving up on it. thanks anyway.

---


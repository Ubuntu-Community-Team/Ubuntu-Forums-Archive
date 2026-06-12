---
title: "Secure DHCP with MAC allow list"
date: 2011-08-29
forum: Server Platforms
---

### Post by Phaser on 2011-08-29
I am trying to setup a secure DHCP server with Ubuntu 10.10. I have the server setup and running DHCP but I cannot correctly setup a secure list of clients.

Here is my current configuration for DHCP

use-host-decl-names on;
ddns-update-style interim;
ignore client-updates;
next-server 10.1.10.11;

subnet 10.1.10.0 netmask 255.255.255.0 {
	option domain-name-servers 75.75.75.75;
	option subnet-mask 255.255.255.0;
	default-lease-time 21600;
	max-lease-time 43200;
	option routers 10.1.10.1;
	filename "pxelinux.0";
	range dynamic-bootp 10.1.10.100 10.1.10.149;
	}

I have tried adding the deny unknown-clients; to the subnet options which works by itself but when I try to add allow known clients or known-clients DHCP will not start up.

It was suggested I create a class and pool so I did that with adding this configuration after the subnet options.

class "my-clients" {
          match if substring (hardware,1,8) = "xx:xx:xx:xx:xx:xx" ;
}
pool {
          range 10.1.10.100 10.1.10.149;
          allow members of  "my-clients" ;
}

When I add that DHCP will not start saying error around the lines I added.

Any help with this would be much appreciated.

---

### Post by Phaser on 2011-08-30
The error I am getting is - 

Failed to restart dhcpd :

dhcpd self-test failed. Please fix the config file.
The error was: 
Internet Systems Consortium DHCP Server V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
/etc/dhcp3/dhcpd.conf line 20: pool declared outside of network
pool 
^
Configuration file errors encountered -- exiting

Lines around 20 in /etc/dhcp3/dhcpd.conf :

	range dynamic-bootp 10.1.10.100 10.1.10.149;
	}
class "my-clients" {
        match if substring (hardware,1,8) = "00:24:e8:31:d8:26"; }
pool {
        range 10.1.10.100 10.1.10.149;
        allow members of "my-clients"; }

---

### Post by Phaser on 2011-09-01
I was able to resolve the problem with the DHCP configuration so it would restart but what I have now doesn't allow the MAC to receive a IP address. What am I doing wrong? 

Here is what I have now - 

use-host-decl-names on;
ddns-update-style interim;
ignore client-updates;
next-server 10.1.10.11;

subnet 10.1.10.0 netmask 255.255.255.0 {
	option domain-name-servers 75.75.75.75;
	option subnet-mask 255.255.255.0;
	default-lease-time 21600;
	max-lease-time 43200;
	option routers 10.1.10.1;
	filename "pxelinux.0";
class "my-clients" {
        match if substring (hardware,1,8) = "xx:xx:xx";
}
pool {
        range 10.1.10.100 10.1.10.149;
        allow members of "my-clients";
}
}

---

### Post by Doug S on 2011-09-02
I use client MAC addresses to assign IP addresses on my network, although via quite a different method than you are using. I have struggled to understand your method. In particular, I don't understand the prelinux part, even though I can find information about it on internet.
Shouldn't this line:```
match if substring (hardware,1,8) = "xx:xx:xx";
```
be this:```
match if substring (hardware,1,3) = "xx:xx:xx";
```
In your code, I am not following where the full comparision is done for the client full MAC. It looks as though only the prefix is being checked. I.E. Wouldn't any computer with the same prefix be accepted?. Maybe that is something I don't understand with the prelinux file.
I include my dhcpd.conf file below as an example of another method. I do have an address pool for unknown MAC's (I.E. for visitors), but that could be deleted.
```
 
#
# 2010.12.26 add MAC addresses.
#
# 2010.12.21 add MAC addresses.
#
# 2010.12.17 Smythies.com edits.
#      There are some discrepencies between the original
#      of this example file and the "how to install and
#      configure DHCP server in Ubuntu Server - Ubuntu Geek"
#      reference that I am also using.
#      This is my best intreptation as to how it should be
#      for my application.
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
default-lease-time 86400;
max-lease-time 93000;
option domain-name "smythies.com";
option domain-name-servers 192.168.111.1, 75.154.133.68, 75.154.133.100;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.111.255;
option routers 192.168.111.1;
# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;
# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;
# The Basic DHCP allocated addresses
subnet 192.168.111.0 netmask 255.255.255.0 {
  range 192.168.111.3 192.168.111.50;
}
# Some specifically declared static IP addresses
host Wireless-R {
  hardware ethernet 00:22:ZZ:ZZ:ZZ:ZZ;
  fixed-address 192.168.111.57;
}
host Doug-XPS {
  hardware ethernet 00:23:ZZ:ZZ:ZZ:ZZ;
  fixed-address 192.168.111.100;
}
host Doug-XPS2 {
  hardware ethernet 00:21:ZZ:ZZ:ZZ:ZZ;
  fixed-address 192.168.111.101;
host S10 {
  hardware ethernet 00:0c:ZZ:ZZ:ZZ:ZZ;
  fixed-address 192.168.111.102;
}
host cyd-hp {
  hardware ethernet 70:1a:ZZ:ZZ:ZZ:ZZ;
  fixed-address 192.168.111.103;
}
host cyd-hp2 {
  hardware ethernet 00:26:ZZ:ZZ:ZZ:ZZ;
  fixed-address 192.168.111.104;
}
host tv01 {
  hardware ethernet 00:15:ZZ:ZZ:ZZ:ZZ;
  fixed-address 192.168.111.105;
}
host carrie {
  hardware ethernet 00:23:ZZ:ZZ:ZZ:ZZ;
  fixed-address 192.168.111.106;
}
host carrie2 {
  hardware ethernet 00:23:ZZ:ZZ:ZZ:ZZ;
  fixed-address 192.168.111.107;
}
host graham-it {
  hardware ethernet 00:23:ZZ:ZZ:ZZ:ZZ;
}
host graham-ps3 {
  hardware ethernet A8:E3:ZZ:ZZ:ZZ:ZZ;
  fixed-address 192.168.111.109;
}
host dsmythies {
  hardware ethernet 00:09:ZZ:ZZ:ZZ:ZZ;
  fixed-address 192.168.111.130;
}
host test-smy {
  hardware ethernet 00:50:ZZ:ZZ:ZZ:ZZ;
  fixed-address 192.168.111.140;
}
# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.
#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}
 

```

---

### Post by Phaser on 2011-09-02
Thank you for the reply Doug S. I tried your method of manually entering in the hosts and set it to have a fixed IP then added the deny unknown-clients option and it worked.

I was trying to get the known clients or hosts to pull an IP from the address pool/range but this way will work if I cannot figure out how to do the other way.

You are correct in that if I just wanted to allow clients matching the first three octets that I would need to put match if substring (hardware,1,3) = "xx:xx:xx"; which would allow more than I would like. I was wanting it to allow only clients matching the full MAC address and was entering the full MAC. I tried both ways hardware,1,3 and hardware,1,8 and neither worked. I should have been more clear in my response

The prelinux option that you mentioned is actually pxelinux. I am also using this DHCP server as a PXE server for imaging.

I will keep messing around with the configuration to see if I can get it to the exact way I would like and post if on here if I am successful.

---


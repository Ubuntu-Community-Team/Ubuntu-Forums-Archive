---
title: "Dnsmasq fails to offer IP to static hosts"
date: 2011-12-04
forum: Server Platforms
---

### Post by trogdor1138 on 2011-12-04
I'm running 64-bit Ubuntu 11.10 Server using Dnsmasq (installed from the repository) for both DHCP and DNS. It works great for any clients which are set up to use defined ranges, but any static IP defined by 'dhcp-host' does not work. Running Dnsmasq in debug mode shows that it receives the DHCPREQUEST from these hosts but never responds with a DHCPOFFER. The really weird thing is that when I change the hosts in question to assign them to a range, they receive an IP address just fine. In other words, the problem definitely lies with the 'dhcp-host' option. Additionally, it doesn't show any message to indicate that a host is ignored, as it does with MAC addresses which are not in the config file.

Even more frustrating, this same setup worked on a previous 11.10 install and a 10.04 install. I even have my old configuration files to compare against. My current configuration file follows:



# Configuration file for dnsmasq
# See man dnsmasq(8) man page for details
# Version: 20111203

# Actually bind only to specified interfaces/addresses
#bind-interfaces
# Don't forward queries in the private IP (ie 192.168.x.x) ranges
bogus-priv
# Set the cachesize
#cache-size=150
# Specify that dnsmasq is the only DHCP server
dhcp-authoritative
# Where should dnsmasq store its leases
#dhcp-leasefile=/var/lib/misc/dnsmasq.leases
# Specify the local domain to give to clients
domain=bkmoller.net
# Never forward plain names (without a dot or domain part)
domain-needed
# Specify the group to run as (default: dip)
#group=
# Specify the interface to listen on
interface=br0
# Specify the local domain so queries in it are not forwarded
local=/bkmoller.net/
# Disable negative caching
#no-negcache
# Don't read /etc/resolv.conf for nameservers
no-resolv
# Set the user to run as (default: 'nobody')
#user=

# Upstream DNS servers (add '@eth0' to specify interface to use)
server=208.67.220.220
server=208.67.222.222
server=208.67.220.222
server=208.67.222.220

# Set CNAME records against the records in hosts file
cname=subsonic.bkmoller.net,Pogi-Server.bkmoller.net

# Static DHCP clients
# HP LaserJet 4100TN
dhcp-host=00:11:0A:C4:23:DA,192.168.1.5
# Sony PS3
dhcp-host=00:19:C5:4A:5C:34,192.168.1.7

# Known wired clients
# Beast
dhcp-host=00:1F:BC:02:34:36,00:1F:BC:02:34:37,set:wired
# Sony VAIO VPCCW27FX
dhcp-host=54:42:49:03:B0:59,set:wired
# Brandon's MacBook Pro
dhcp-host=10:9A:DD:66:2D:9C,set:wired

# Known wirless clients
# Brandon's MacBook Pro
dhcp-host=C8:BC:C8:EC:D5:BE,set:wireless
# Kerri's MacBook
dhcp-host=60:33:4B:0C:A2:EA,set:wireless
# Motorola Photon
dhcp-host=98:4B:4A:6A:A5:B8,set:wireless
# Sony VAIO VPCCW27FX
dhcp-host=78:DD:08:C5:B7:82,set:wireless
# HTC Evo 4G
dhcp-host=D8:B3:77:71:4E:BE,set:wireless
# Apple iPad 2
dhcp-host=A4:67:06:07:41:55,set:wireless

# Ignore any clients not defined above
dhcp-ignore=tag:!known

# Address range for wired clients
dhcp-range=tag:wired,192.168.1.10,192.168.1.19,255.255.255.0,1h

# Address range for wireless clients
dhcp-range=tag:wireless,192.168.1.20,192.168.1.29,255.255.255.0,1h

# DHCP options given to known clients

# Subnet mask
dhcp-option=1,255.255.255.0
# Default gateway
dhcp-option=3,192.168.1.1
# DNS server
dhcp-option=6,192.168.1.3
# Broadcast address
dhcp-option=28,192.168.1.255

---

### Post by 2oznet on 2012-11-04
Hi!
i have nearly the same problem. My clients receive ip addresses from the dynamic range, and not the static ip addresses that i have confgured.

dhcp-range=192.168.178.101,192.168.178.130,12h
dhcp-host=00:03:23:1f:1c:62,squeezeboom,192.168.178.74,12h
dhcp-host=78:83:33:c2:d3:55,sonytv,192.168.178.75,12h

Have you found a solution for this problem in the meantime ?

Regards,
Joerg

---

### Post by trogdor1138 on 2012-12-05
Sorry for the delayed reply; I'm not on here too often.

Anyway, I did figure it out finally. I don't remember this being a requirement in previous versions of dnsmasq, but apparently this version requires that static leases be a part of a defined range. For me, adding the following got things working again:

# Address range for static network appliances
dhcp-range=192.168.1.4,192.168.1.9,static,255.255.255.0,infinite

Hope that helps.

---


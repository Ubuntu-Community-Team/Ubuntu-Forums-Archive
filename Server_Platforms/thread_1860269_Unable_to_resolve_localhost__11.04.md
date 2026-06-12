---
title: "Unable to resolve localhost ? 11.04"
date: 2011-10-14
forum: Server Platforms
---

### Post by drifting on 2011-10-14
Hopefully someone can shed some light, as I am confused as anything. I was forced out from 10.4 LTS because of a DVB-S card that was a pain to get working. After the upgrade to 11.04 DHCP got upgraded and failed miserably. I fought with it for a few days, as all the documentation I found referred to the earlier working DHCP.
I gave up and installed dnsmasq, have a few problems with resolve and un-installed the resolver and used a standard resolv.conf. It has been working fine for quite a while. 

Problem now is that I noticed I have ebox installed, so as I never used it I removed it. Now whether this has bearing on the none resolution of localhost, I have no idea. It could have happened a while ago from an update? 

Anyway, here are my hosts, dnsmasq, nsswitch conf files, anyone see anything untoward?

HOSTS

127.0.0.1	localhost.localdomain	localhost
::1	vs	localhost6.localdomain6	localhost6
127.0.1.1	vs

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

DNSMASQ
domain=spud				
dhcp-range=10.0.0.30,10.0.0.50,255.255.255.0,12h
#
#
dhcp-authoritative
# Server DNS settings... this is required as the server itself will
# Server DNS settings... this is required as the server itself will
# not be obtaining it's IP address via DHCP and therefore would 
# not be automatically added to the DNS records for forward/reverse
# DNS queries as required by Kerberos
ptr-record=2.0.0.10.in-addr.arpa.,"vs.spud" address=/vs.spud/10.0.0.1 
 
# Kerberos and LDAP automatic stuff...
# This maps kerberos.spud and
# ldap.spud to the server and also makes all
# dhcp clients aware of the kerberos realm... magic :D
address=/kerberos.spud/10.0.0.1 
address=/ldap. spud/10.0.0.1 
 
txt-record=_kerberos.spud,"SPUD"
srv-host=_kerberos._udp.spud,"kerberos.spud",88
srv-host=_kerberos._tcp.spud,"kerberos.spud",88
srv-host=_kerberos-master._udp.spud,kerberos."spud",88
srv-host=_kerberos-adm._tcp.spud,"kerberos.spud",749
srv-host=_kpasswd._udp.spud,"kerberos.spud",464
srv-host=_ldap._tcp.spud,ldap.spud,389
#
#
#
#dhcp-vendorclass=new
interface=eth0
except-interface=eth1
listen-address=127.0.0.1
#no-resolv
resolv-file= /etc/resolv.conf
#strict-order
#no-poll
#

NSSWITCH

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:	files dns mdns4 wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis


I have gone round in circles with this, any help really appreciated.

Regards Paul

---


---
title: "can't get DHCP working with dnsmasq"
date: 2006-07-15
forum: Server Platforms
---

### Post by Kurt` on 2006-07-15
Hi,

My network setup looks like this:

cable modem -> (eth0)Ubuntu Machine(eth1) -> workstation/device

eth0 gets an IP from my ISP via DHCP, works fine.

dnsmasq is set to listen on eth1 and assign addresses. No device/machine I attach to it can get an address from the Ubuntu machine though. :(

eth1 is configured in /etc/network/interfaces as follows:

```
iface eth1 inet static
address 192.168.0.1
network 192.168.0.0
netmask 255.255.255.0
```

Here are the only 2 changes I added to dnsmasq.conf:

```
interface=eth1
dhcp-range=192.168.0.50,192.168.0.99
```

dnsmasq is running correctly, and syslog shows it starting fine.

I have /proc/sys/net/ipv4/ip_forward set to 1 (via /etc/sysctl.conf).

I directly connected another Ubuntu machine (ethernet to ethernet) to this one via a crossover cable. It sent out many DHCPDISCOVERs, but received no replies. There are no logs from the connection attempt in syslog! (even when I enabled logging)

I can't determine if this is a configuration issue, or a physical issue or what. Is eth1 setup correctly? I'm pretty sure it's something stupid. Any help would be greatly appreciated!

---

### Post by fatbastard spice on 2006-07-17
I've got basically the same setup, gateway machine, using dnsmasq as DHCP/DNS server and it's been a dream for a few years now. Which means it's been ages since i've touched my config so i can't quite remember if the things i'm typing will be of any use, but...

In my eth1 config in the interfaces i've also got:
```
broadcast 192.168.0.255
```

In the dnsmasq.conf:
```
dhcp-range=192.168.0.100,192.168.0.200,255.255.255.0,12h
```

If that doesn't help maybe post the whole config file and i can check for other inconsistencies.

---

### Post by az on 2006-07-17
I think you need to enable something in /etc/defaults so that it actually starts up.  Did you read the documentation in /usr/share/doc/dnsmasq?

I'm in the same boat as Fatbastard Spice.  It's been ages, so I'm a little foggy....

---

### Post by Kurt` on 2006-07-24
Ok, still can't get it working. :(

/etc/dnsmasq.conf
```
# Configuration file for dnsmasq.
#
# Format is one option per line, legal options are the same
# as the long options legal on the command line. See
# "/usr/sbin/dnsmasq --help" or "man 8 dnsmasq" for details.

# The following two options make you a better netizen, since they
# tell dnsmasq to filter out queries which the public DNS cannot
# answer, and which load the servers (especially the root servers)
# uneccessarily. If you have a dial-on-demand link they also stop
# these requests from bringing up the link uneccessarily.

# Never forward plain names (without a dot or domain part)
domain-needed
# Never forward addresses in the non-routed address spaces.
bogus-priv


# Uncomment this to filter useless windows-originated DNS requests
# which can trigger dial-on-demand links needlessly.
# Note that (amongst other things) this blocks all SRV requests,
# so don't use it if you use eg Kerberos.
# This option only affects forwarding, SRV records originating for
# dnsmasq (via srv-host= lines) are not suppressed by it.
#filterwin2k

# Change this line if you want dns to get its upstream servers from
# somewhere other that /etc/resolv.conf
#resolv-file=

# By  default,  dnsmasq  will  send queries to any of the upstream
# servers it knows about and tries to favour servers to are  known
# to  be  up.  Uncommenting this forces dnsmasq to try each query
# with  each  server  strictly  in  the  order  they   appear   in
# /etc/resolv.conf
#strict-order

# If you don't want dnsmasq to read /etc/resolv.conf or any other
# file, getting its servers from this file instead (see below), then
# uncomment this
#no-resolv

# If you don't want dnsmasq to poll /etc/resolv.conf or other resolv
# files for changes and re-read them then uncomment this.
#no-poll

# Add other name servers here, with domain specs if they are for
# non-public domains.
#server=/localnet/192.168.0.1

# Add local-only domains here, queries in these domains are answered
# from /etc/hosts or DHCP only.
#local=/localnet/

# Add domains which you want to force to an IP address here.
# The example below send any host in doubleclick.net to a local
# webserver.
#address=/doubleclick.net/127.0.0.1

# If you want dnsmasq to change uid and gid to something other
# than the default, edit the following lines.
#user=
#group=

# If you want dnsmasq to listen for DHCP and DNS requests only on
# specified interfaces (and the loopback) give the name of the
# interface (eg eth0) here.
# Repeat the line for more than one interface.
#interface=
# Or you can specify which interface _not_ to listen on
#except-interface=
# Or which to listen on by address (remember to include 127.0.0.1 if
# you use this.)
#listen-address=
# If you want dnsmasq to provide only DNS service on an interface,
# configure it as shown above, and then use the following line to
# disable DHCP on it.
#no-dhcp-interface=

# On systems which support it, dnsmasq binds the wildcard address,
# even when it is listening on only some interfaces. It then discards
# requests that it shouldn't reply to. This has the advantage of
# working even when interfaces come and go and change address. If you
# want dnsmasq to really bind only the interfaces it is listening on,
# uncomment this option. About the only time you may need this is when
# running another nameserver on the same machine.
#bind-interfaces

# If you don't want dnsmasq to read /etc/hosts, uncomment the
# following line.
#no-hosts
# or if you want it to read another file, as well as /etc/hosts, use
# this.
#addn-hosts=/etc/banner_add_hosts

# Set this (and domain: see below) if you want to have a domain
# automatically added to simple names in a hosts-file.
#expand-hosts

# Set the domain for dnsmasq. this is optional, but if it is set, it
# does the following things.
# 1) Allows DHCP hosts to have fully qualified domain names, as long
#     as the domain part matches this setting.
# 2) Sets the "domain" DHCP option thereby potentially setting the
#    domain of all systems configured by DHCP
# 3) Provides the domain part for "expand-hosts"
#domain=thekelleys.org.uk

# Uncomment this to enable the integrated DHCP server, you need
# to supply the range of addresses available for lease and optionally
# a lease time. If you have more than one network, you will need to
# repeat this for each network on which you want to supply DHCP
# service.
#dhcp-range=192.168.0.50,192.168.0.150,12h
dhcp-range=192.168.0.100,192.168.0.200,255.255.255.0,12h

# This is an example of a DHCP range where the netmask is given. This
# is needed for networks we reach the dnsmasq DHCP server via a relay
# agent. If you don't know what a DHCP relay agent is, you probably
# don't need to worry about this.
#dhcp-range=192.168.0.50,192.168.0.150,255.255.255.0,12h

# This is an example of a DHCP range with a network-id, so that
# some DHCP options may be set only for this network.
#dhcp-range=red,192.168.0.50,192.168.0.150

# Supply parameters for specified hosts using DHCP. There are lots
# of valid alternatives, so we will give examples of each. Note that
# IP addresses DO NOT have to be in the range given above, they just
# need to be on the same network. The order of the parameters in these
# do not matter, it's permissble to give name,adddress and MAC in any order

# Always allocate the host with ethernet address 11:22:33:44:55:66
# The IP address 192.168.0.60
#dhcp-host=11:22:33:44:55:66,192.168.0.60

# Always set the name of the host with hardware address
# 11:22:33:44:55:66 to be "fred"
#dhcp-host=11:22:33:44:55:66,fred

# Always give the host with ethernet address 11:22:33:44:55:66
# the name fred and IP address 192.168.0.60 and lease time 45 minutes
#dhcp-host=11:22:33:44:55:66,fred,192.168.0.60,45m

# Give the machine which says it's name is "bert" IP address
# 192.168.0.70 and an infinite lease
#dhcp-host=bert,192.168.0.70,infinite

# Always give the host with client identifier 01:02:02:04
# the IP address 192.168.0.60
#dhcp-host=id:01:02:02:04,192.168.0.60

# Always give the host with client identifier "marjorie"
# the IP address 192.168.0.60
#dhcp-host=id:marjorie,192.168.0.60

# Enable the address given for "judge" in /etc/hosts
# to be given to a machine presenting the name "judge" when
# it asks for a DHCP lease.
#dhcp-host=judge

# Never offer DHCP service to a machine whose ethernet
# address is 11:22:33:44:55:66
#dhcp-host=11:22:33:44:55:66,ignore

# Ignore any client-id presented by the machine with ethernet
# address 11:22:33:44:55:66. This is useful to prevent a machine
# being treated differently when running under different OS's or
# between PXE boot and OS boot.
#dhcp-host=11:22:33:44:55:66,id:*

# Send extra options which are tagged as "red" to
# the machine with ethernet address 11:22:33:44:55:66
#dhcp-host=11:22:33:44:55:66,net:red

# Send extra options which are tagged as "red" to
# any machine with ethernet address starting 11:22:33:
#dhcp-host=11:22:33:*:*:*,net:red

# Send extra options which are tagged as "red" to any machine whose
# DHCP vendorclass string includes the substring "Linux"
#dhcp-vendorclass=red,Linux

# Send extra options which are tagged as "red" to any machine one
# of whose DHCP userclass strings includes the substring "accounts"
#dhcp-userclass=red,accounts

# If this line is uncommented, dnsmasq will read /etc/ethers and act
# on the ethernet-address/IP pairs found there just as if they had
# been given as --dhcp-host options. Useful if you keep
# MAC-address/host mappings there for other purposes.
#read-ethers

# Send options to hosts which ask for a DHCP lease.
# See RFC 2132 for details of available options.
# Note that all the common settings, such as netmask and
# broadcast address, DNS server and default route, are given
# sane defaults by dnsmasq. You very likely will not need any
# any dhcp-options. If you use Windows clients and Samba, there
# are some options which are recommended, they are detailed at the
# end of this section.
# For reference, the common options are:
# subnet mask - 1
# default router - 3
# DNS server - 6
# broadcast address - 28

# Set the NTP time server addresses to 192.168.0.4 and 10.10.0.5
#dhcp-option=42,192.168.0.4,10.10.0.5

# Set the NTP time server address to be the same machine as
# is running dnsmasq
#dhcp-option=42,0.0.0.0

# Set the NIS domain name to "welly"
#dhcp-option=40,welly

# Set the default time-to-live to 50
#dhcp-option=23,50

# Set the "all subnets are local" flag
#dhcp-option=27,1

# Send the etherboot magic flag and then etherboot options (a string).
#dhcp-option=128,e4:45:74:68:00:00
#dhcp-option=129,NIC=eepro100

# Specify an option which will only be sent to the "red" network
# (see dhcp-range for the declaration of the "red" network)
#dhcp-option=red,42,192.168.1.1

# The following DHCP options set up dnsmasq in the same way as is specified
# for the ISC dhcpcd in
# http://www.samba.org/samba/ftp/docs/textdocs/DHCP-Server-Configuration.txt
# adapted for a typical dnsmasq installation where the host running
# dnsmasq is also the host running samba.
# you may want to uncomment them if you use Windows clients and Samba.
#dhcp-option=19,0           # option ip-forwarding off
#dhcp-option=44,0.0.0.0     # set netbios-over-TCP/IP nameserver(s) aka WINS server(s)
#dhcp-option=45,0.0.0.0     # netbios datagram distribution server
#dhcp-option=46,8           # netbios node type
#dhcp-option=47             # empty netbios scope.

# Send RFC-3397 DNS domain search DHCP option. WARNING: Your DHCP client
# probably doesn't support this......
#dhcp-option=119,eng.apple.com,marketing.apple.com

# Send encapsulated vendor-class specific options. The vendor-class
# is sent as DHCP option 60, and all the options marked with the
# vendor class are send encapsulated in DHCP option 43. The meaning of
# the options is defined by the vendor-class. This example sets the
# mtftp address to 0.0.0.0 for PXEClients
#dhcp-option=vendor:PXEClient,1,0.0.0.0

# Set the boot filename and tftpd server name and address
# for BOOTP. You will only need this is you want to
# boot machines over the network.
#dhcp-boot=/var/ftpd/pxelinux.0,boothost,192.168.0.3

# Set the limit on DHCP leases, the default is 150
#dhcp-lease-max=150

# The DHCP server needs somewhere on disk to keep its lease database.
# This defaults to a sane location, but if you want to change it, use
# the line below.
#dhcp-leasefile=/var/lib/misc/dnsmasq.leases

# Set the DHCP server to authoritative mode. In this mode it will barge in
# and take over the lease for any client which broadcasts on the network,
# whether it has a record of the lease or not. This avoids long timeouts
# when a machine wakes up on a new network. DO NOT enable this if there's
# the slighest chance that you might end up accidentally configuring a DHCP
# server for your campus/company accidentally. The ISC server uses the same
# the same option, and this URL provides more information:
# http://www.isc.org/index.pl?/sw/dhcp/authoritative.php
#dhcp-authoritative

# Set the cachesize here.
#cache-size=150

# If you want to disable negative caching, uncomment this.
#no-negcache

# Normally responses which come form /etc/hosts and the DHCP lease
# file have Time-To-Live set as zero, which conventionally means
# do not cache further. If you are happy to trade lower load on the
# server for potentially stale date, you can set a time-to-live (in
# seconds) here.
#local-ttl=

# If you want dnsmasq to detect attempts by Verisign to send queries
# to unregistered .com and .net hosts to its sitefinder service and
# have dnsmasq instead return the correct NXDOMAIN response, uncomment
# this line. You can add similar lines to do the same for other
# registries which have implemented wildcard A records.
#bogus-nxdomain=64.94.110.11

# If you want to fix up DNS results from upstream servers, use the
# alias option. This only works for IPv4.
# This alias makes a result of 1.2.3.4 appear as 5.6.7.8
#alias=1.2.3.4,5.6.7.8
# and this maps 1.2.3.x to 5.6.7.x
#alias=1.2.3.0,5.6.7.0,255.255.255.0


# Change these lines if you want dnsmasq to serve MX records.

# Return an MX record named "maildomain.com" with target
# servermachine.com and preference 50
#mx-host=maildomain.com,servermachine.com,50

# Set the default target for MX records created using the localmx option.
#mx-target=servermachine.com

# Return an MX record pointing to the mx-target for all local
# machines.
#localmx

# Return an MX record pointing to itself for all local machines.
#selfmx

# Change the following lines if you want dnsmasq to serve SRV
# records.  These are useful if you want to serve ldap requests for
# Active Directory and other windows-originated DNS requests.
# See RFC 2782.
# You may add multiple srv-host lines.
# The fields are <name>,<target>,<port>,<priority>,<weight>
# If the domain part if missing from the name (so that is just has the
# service and protocol sections) then the domain given by the domain=
# config option is used. (Note that expand-hosts does not need to be
# set for this to work.)

# A SRV record sending LDAP for the example.com domain to
# ldapserver.example.com port 289
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389

# A SRV record sending LDAP for the example.com domain to
# ldapserver.example.com port 289 (using domain=)
#domain=example.com
#srv-host=_ldap._tcp,ldapserver.example.com,389

# Two SRV records for LDAP, each with different priorities
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389,1
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389,2

# A SRV record indicating that there is no LDAP server for the domain
# example.com
#srv-host=_ldap._tcp.example.com


# Change the following lines to enable dnsmasq to serve TXT records.
# These are used for things like SPF and zeroconf. (Note that the
# domain-name expansion done for SRV records _does_not
# occur for TXT records.)

#Example SPF.
#txt-record=example.com,v=spf1 a -all

#Example zeroconf
#txt-record=_http._tcp.example.com,name=value,paper=A4


# For debugging purposes, log each DNS query as it passes through
# dnsmasq.
#log-queries

# Include a another lot of configuration options.
#conf-file=/etc/dnsmasq.more.conf

```

/etc/network/interfaces (on the server)
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

iface eth1 inet static
address 192.168.0.1
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255
```

/etc/network/interfaces (client machine)
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

Client is connected to server via crossover cable. When I do ifup eth0 on the client, it sends out DHCPDISCOVERs (the NIC lights blink on both machines):

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7

and it just keeps repeating.

Syslog shows nothing other than dnsmasq starting properly.

What is going on here?

---

### Post by az on 2006-07-24
Are you blocking ports 67 and 68?  You need them for dhcp.

Also, what network is your external lan (eth0, the one that conncts via dhcp to your router?  Both cannot be the same (192.168.0.0) AFAIK.

---

### Post by Kurt` on 2006-07-24
The server machine has no firewall yet, nothing is blocked.

eth0 is connecting directly to my cable modem, not a router. :)

cable modem -> (eth0)Ubuntu Machine(eth1) -> workstation/device

That's why I'm so confused. They're not on the same network (NICs), everything is setup correctly (to my knowledge), the NICs are blinking indicating traffic is passing through, but it's just not working! ](*,)

---

### Post by az on 2006-07-24
I just assumed your modem was also a router.  My bad.

I installed dnsmasq on a live session and tried to connect to it, but It would not get a lease.  I only had a few minutes to troubleshoot.

I'm interested in getting this working because it's supposed to be easy!

---

### Post by Kurt` on 2006-07-24
I've completely read over the documentation for dnsmasq, and I'm pretty sure everything else is setup correctly. I'm leaning towards a setting or something within Ubuntu that needs to be changed. ](*,) 

I do thank you for your continued effort, azz. We *will* figure this out! :)

EDIT:

I *DID* just get it working, after toying around with some settings in /etc/sysctl.conf. I think it had something to do with the tcp_syncookies value (in /proc/sys/net/ipv4/tcp_syncookies), but I'm going to verify! :)

EDIT (again):

I've been playing around with this setup here for a few hours, and I'm still not so certain about what I did change! After the tcp_syncookies change in sysctl.conf (and reloading it via # sysctl -p), it seemed to work.

I neglected to mention, but that router machine will eventually have more than 2 NICs in it, but apt-get install ipmasq sorted that out quickly. :)

---

### Post by az on 2006-07-25
> **Kurt` said:**
> but apt-get install ipmasq sorted that out quickly. :)

Be sure to add the ipmasq dhcp rule so that it can send and recieve dhcp offers and requests.

---

### Post by Kurt` on 2006-07-25
What do you mean? I just apt-get install'ed it and everything worked instantly. :???:

---


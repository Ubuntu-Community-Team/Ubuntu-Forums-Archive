---
title: "Ubuntu 9.10 Linux Terminal Server Project for public school"
date: 2009-11-22
forum: Server Platforms
---

### Post by Denbert on 2009-11-22
Hi,

My daughters school is planning new IT for the students.

They are looking for a Terminal Server solution in order to offer students to either use the terminals at the school, or use own laptop via RDP. In future they will also give the students the ability to connect their desktop from home via internet.

The local M$ sales dude is looking forward to receive the order (we are looking for a system with 150 users at the same time), but the School Headmaster has asked all parents if there where somebody who would help the school make the right decision.

I would like to suggest a Ubuntu LTSP solution, and in order to suggest this I've tried to make a small setup at home for testing.

First thing I've noticed is that the LTSP isn't a part of the Server ISO but is in the Alternate version - How come?

I have a quite powerful server running VMWare 2.0.1 and therefore I've downloaded the 9.10 Alternate ISO and installed with F4 choosing LTSP server Install.

First error I've noticed is the DHCP server making an error, as the server by default setup the system with an dynamic IP address, therefore this error is expected - I'm surprised that the installer doesn't give the ability to setup a static IP address and a planned scope for the DHCP Server, as the system wont work without these settings. Somebody should consider to implement this change in the installer process.

As my firewall is acting as DHCP server, i'm a bit stuck in getting a working server up and running, hence there has been no testing yet.

Anyone who can help me with an integration solution where an existing DHCP server on firewall is running?

---

### Post by CharlesA on 2009-11-22
It should just grab an IP from the DHCP server. I don't know about setting a static IP, but when I've installed the regular server version of Ubuntu it grabs an IP from the DHCP server (which is configured to give a specific IP to that machine based on its MAC address).

As for the it only being on the Alternate CD. I don't know.

However, I did a apt-cache search and found this:

```
charles@thor:~$  apt-cache search ltsp
ldm - LTSP display manager
ldm-ubuntu-themes - Themes for the LTSP Display Manager
ltsp-client - LTSP client environment
ltsp-client-core - LTSP client environment
ltsp-server - Basic LTSP server environment
ltsp-server-standalone - Complete LTSP server environment
ltspfs - Fuse based remote filesystem for LTSP thin clients
ltspfsd - Fuse based remote filesystem daemon for LTSP thin clients
python-tcm - control ubuntu LTSP connections
thin-client-manager-backend - control ubuntu LTSP connections
thin-client-manager-gnome - control ubuntu LTSP connections
ltsp-manager - Ubuntu LTSP server management GUI
mythbuntu-diskless-client - Mythbuntu-diskless client environment
python-ltsp - provides ltsp related functions
controlaula - Classroom management tool
ltsp-controlaula - Classroom management tool with ltsp clients

```

You can probably just run apt-get and install it from there.

Maybe give that a shot?

EDIT: Also since it's for a school, I would stick with LTS releases, but that's just IMHO. (I'll be switching to LTS when 10.4 is released)

---

### Post by Denbert on 2009-11-22
> **CharlesA said:**
>  Also since it's for a school, I would stick with LTS releases, but that's just IMHO. (I'll be switching to LTS when 10.4 is released)

Ok, I'll try to install 8.04 right away - Please stay tuned :-)

---

### Post by Denbert on 2009-11-22
I'm installing Ubuntu 9.10 due to it's LTSP-5 implementation: [http://www.ubuntu.com/products/whatisubuntu/serveredition/technologies/ltsp](http://www.ubuntu.com/products/whatisubuntu/serveredition/technologies/ltsp)

*If you use a machine with two network cards, your server will work directly out of the box*

Looks interesting :D

---

### Post by CharlesA on 2009-11-22
Good luck man. Keep us posted.

If it needs 2 NICs then one is probably DHCP and the other is static (guessing here). :-)

---

### Post by Denbert on 2009-11-22
Impressive.

It really worked out of the box, a network boot gave me this in a split second:

[IMG]http://hegnstoften.net/pictures/pxe-boot-in-vmware-terminal.png[/IMG]

Didn't even touch any conf file concerning dhcp server.

The School want's to offer students to use their own laptops - how do I implement RDP access?

---

### Post by crankyadm1n on 2009-11-22
> **Denbert said:**
> Impressive.
[IMG]http://hegnstoften.net/pictures/pxe-boot-in-vmware-terminal.png[/IMG]


Where is that login screen? I like!

---

### Post by CharlesA on 2009-11-22
> **Denbert said:**
> 
The School want's to offer students to use their own laptops - how do I implement RDP access?

That I don't know. Probably have to install the ltsp client on the laptops.

---

### Post by Denbert on 2009-11-22
> **crankyadm1n said:**
> Where is that login screen? I like!

The test setup was made in full virtual environment, hence the server and the client is in vmware 2.0.1 remote console.

runs rock steady.

---

### Post by Denbert on 2009-11-23
In order to implement this LTSP server to my existing setup where I have a Firewall I need a setup where the LTSP server uses existing DHCP scope from the Firewall. I've looked at this document: [ProxyDHCP]("https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP")

I've followed the steps, but the /etc/dnsmasq.conf looks very complicated to me :confused:

My LTSP Server has IP 192.168.9.12

Firewall/Router 192.168.9.254

Anyone who can help me out here?

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
#domain-needed
# Never forward addresses in the non-routed address spaces.
#bogus-priv


# Uncomment this to filter useless windows-originated DNS requests
# which can trigger dial-on-demand links needlessly.
# Note that (amongst other things) this blocks all SRV requests,
# so don't use it if you use eg Kerberos, SIP, XMMP or Google-talk.
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
# uncomment this.
#no-resolv

# If you don't want dnsmasq to poll /etc/resolv.conf or other resolv
# files for changes and re-read them then uncomment this.
#no-poll

# Add other name servers here, with domain specs if they are for
# non-public domains.
#server=/localnet/192.168.0.1

# Example of routing PTR queries to nameservers: this will send all 
# address->name queries for 192.168.3/24 to nameserver 10.1.2.3
#server=/3.168.192.in-addr.arpa/10.1.2.3

# Add local-only domains here, queries in these domains are answered
# from /etc/hosts or DHCP only.
#local=/localnet/

# Add domains which you want to force to an IP address here.
# The example below send any host in doubleclick.net to a local
# webserver.
#address=/doubleclick.net/127.0.0.1

# --address (and --server) work with IPv6 addresses too.
#address=/www.thekelleys.org.uk/fe80::20d:60ff:fe36:f83

# You can control how dnsmasq talks to a server: this forces 
# queries to 10.1.2.3 to be routed via eth1
# --server=10.1.2.3@eth1

# and this sets the source (ie local) address used to talk to
# 10.1.2.3 to 192.168.1.1 port 55 (there must be a interface with that
# IP on the machine, obviously).
# --server=10.1.2.3@192.168.1.1#55

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

# Set a different domain for a particular subnet
#domain=wireless.thekelleys.org.uk,192.168.2.0/24

# Same idea, but range rather then subnet
#domain=reserved.thekelleys.org.uk,192.68.3.100,192.168.3.200

# Uncomment this to enable the integrated DHCP server, you need
# to supply the range of addresses available for lease and optionally
# a lease time. If you have more than one network, you will need to
# repeat this for each network on which you want to supply DHCP
# service.
#dhcp-range=192.168.0.50,192.168.0.150,12h

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

# Give a host with ethernet address 11:22:33:44:55:66 or
# 12:34:56:78:90:12 the IP address 192.168.0.60. Dnsmasq will assume
# that these two ethernet interfaces will never be in use at the same
# time, and give the IP address to the second, even if it is already
# in use by the first. Useful for laptops with wired and wireless
# addresses.
#dhcp-host=11:22:33:44:55:66,12:34:56:78:90:12,192.168.0.60

# Give the machine which says its name is "bert" IP address
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

# Ignore any clients which are specified in dhcp-host lines
# or /etc/ethers. Equivalent to ISC "deny unkown-clients".
# This relies on the special "known" tag which is set when 
# a host is matched.
#dhcp-ignore=#known

# Send extra options which are tagged as "red" to any machine whose
# DHCP vendorclass string includes the substring "Linux"
#dhcp-vendorclass=red,Linux

# Send extra options which are tagged as "red" to any machine one
# of whose DHCP userclass strings includes the substring "accounts"
#dhcp-userclass=red,accounts

# Send extra options which are tagged as "red" to any machine whose
# MAC address matches the pattern.
#dhcp-mac=red,00:60:8C:*:*:*

# If this line is uncommented, dnsmasq will read /etc/ethers and act
# on the ethernet-address/IP pairs found there just as if they had
# been given as --dhcp-host options. Useful if you keep
# MAC-address/host mappings there for other purposes.
#read-ethers

# Send options to hosts which ask for a DHCP lease.
# See RFC 2132 for details of available options.
# Common options can be given to dnsmasq by name: 
# run "dnsmasq --help dhcp" to get a list.
# Note that all the common settings, such as netmask and
# broadcast address, DNS server and default route, are given
# sane defaults by dnsmasq. You very likely will not need 
# any dhcp-options. If you use Windows clients and Samba, there
# are some options which are recommended, they are detailed at the
# end of this section.

# Override the default route supplied by dnsmasq, which assumes the
# router is the same machine as the one running dnsmasq.
#dhcp-option=3,1.2.3.4

# Do the same thing, but using the option name
#dhcp-option=option:router,1.2.3.4

# Override the default route supplied by dnsmasq and send no default
# route at all. Note that this only works for the options sent by
# default (1, 3, 6, 12, 28) the same line will send a zero-length option 
# for all other option numbers.
#dhcp-option=3

# Set the NTP time server addresses to 192.168.0.4 and 10.10.0.5
#dhcp-option=option:ntp-server,192.168.0.4,10.10.0.5

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
# Note that the net: part must precede the option: part.
#dhcp-option = net:red, option:ntp-server, 192.168.1.1

# The following DHCP options set up dnsmasq in the same way as is specified
# for the ISC dhcpcd in
# http://www.samba.org/samba/ftp/docs/textdocs/DHCP-Server-Configuration.txt
# adapted for a typical dnsmasq installation where the host running
# dnsmasq is also the host running samba.
# you may want to uncomment some or all of them if you use 
# Windows clients and Samba.
#dhcp-option=19,0           # option ip-forwarding off
#dhcp-option=44,0.0.0.0     # set netbios-over-TCP/IP nameserver(s) aka WINS server(s)
#dhcp-option=45,0.0.0.0     # netbios datagram distribution server
#dhcp-option=46,8           # netbios node type

# Send RFC-3397 DNS domain search DHCP option. WARNING: Your DHCP client
# probably doesn't support this......
#dhcp-option=option:domain-search,eng.apple.com,marketing.apple.com

# Send RFC-3442 classless static routes (note the netmask encoding)
#dhcp-option=121,192.168.1.0/24,1.2.3.4,10.0.0.0/8,5.6.7.8

# Send vendor-class specific options encapsulated in DHCP option 43. 
# The meaning of the options is defined by the vendor-class so
# options are sent only when the client supplied vendor class
# matches the class given here. (A substring match is OK, so "MSFT" 
# matches "MSFT" and "MSFT 5.0"). This example sets the
# mtftp address to 0.0.0.0 for PXEClients.
#dhcp-option=vendor:PXEClient,1,0.0.0.0

# Send microsoft-specific option to tell windows to release the DHCP lease
# when it shuts down. Note the "i" flag, to tell dnsmasq to send the
# value as a four-byte integer - that's what microsoft wants. See
# http://technet2.microsoft.com/WindowsServer/en/library/a70f1bb7-d2d4-49f0-96d6-4b7414ecfaae1033.mspx?mfr=true
#dhcp-option=vendor:MSFT,2,1i

# Send the Encapsulated-vendor-class ID needed by some configurations of
# Etherboot to allow is to recognise the DHCP server.
#dhcp-option=vendor:Etherboot,60,"Etherboot"

# Send options to PXELinux. Note that we need to send the options even
# though they don't appear in the parameter request list, so we need
# to use dhcp-option-force here. 
# See http://syslinux.zytor.com/pxe.php#special for details.
# Magic number - needed before anything else is recognised
#dhcp-option-force=208,f1:00:74:7e
# Configuration file name
#dhcp-option-force=209,configs/common
# Path prefix
#dhcp-option-force=210,/tftpboot/pxelinux/files/
# Reboot time. (Note 'i' to send 32-bit value)
#dhcp-option-force=211,30i

# Set the boot filename for netboot/PXE. You will only need 
# this is you want to boot machines over the network and you will need
# a TFTP server; either dnsmasq's built in TFTP server or an
# external one. (See below for how to enable the TFTP server.)
#dhcp-boot=pxelinux.0

# Boot for Etherboot gPXE. The idea is to send two different
# filenames, the first loads gPXE, and the second tells gPXE what to
# load. The dhcp-match sets the gpxe tag for requests from gPXE.
#dhcp-match=gpxe,175 # gPXE sends a 175 option.
#dhcp-boot=net:#gpxe,undionly.kpxe
#dhcp-boot=mybootimage
 
# Encapsulated options for Etherboot gPXE. All the options are
# encapsulated within option 175
#dhcp-option=encap:175, 1, 5b         # priority code
#dhcp-option=encap:175, 176, 1b       # no-proxydhcp 
#dhcp-option=encap:175, 177, string   # bus-id 
#dhcp-option=encap:175, 189, 1b       # BIOS drive code
#dhcp-option=encap:175, 190, user     # iSCSI username
#dhcp-option=encap:175, 191, pass     # iSCSI password

# Test for the architecture of a netboot client. PXE clients are
# supposed to send their architecture as option 93. (See RFC 4578)
#dhcp-match=peecees, option:client-arch, 0 #x86-32
#dhcp-match=itanics, option:client-arch, 2 #IA64
#dhcp-match=hammers, option:client-arch, 6 #x86-64
#dhcp-match=mactels, option:client-arch, 7 #EFI x86-64 

# Do real PXE, rather than just booting a single file, this is an
# alternative to dhcp-boot.
#pxe-prompt="What system shall I netboot?"
# or with timeout before first available action is taken:
#pxe-prompt="Press F8 for menu.", 60

# Available boot services. for PXE.
#pxe-service=x86PC, "Boot from local disk", 0

# Loads <tftp-root>/pxelinux.0 from dnsmasq TFTP server.
#pxe-service=x86PC, "Install Linux", pxelinux 

# Loads <tftp-root>/pxelinux.0 from TFTP server at 1.2.3.4.
# Beware this fails on old PXE ROMS.
#pxe-service=x86PC, "Install Linux", pxelinux, 1.2.3.4 

# Use bootserver on network, found my multicast or broadcast.
#pxe-service=x86PC, "Install windows from RIS server", 1

# Use bootserver at a known IP address.
#pxe-service=x86PC, "Install windows from RIS server", 1, 1.2.3.4

# If you have multicast-FTP available,
# information for that can be passed in a similar way using options 1
# to 5. See page 19 of
# http://download.intel.com/design/archives/wfm/downloads/pxespec.pdf  

  
# Enable dnsmasq's built-in TFTP server
#enable-tftp

# Set the root directory for files availble via FTP.
#tftp-root=/var/ftpd

# Make the TFTP server more secure: with this set, only files owned by
# the user dnsmasq is running as will be send over the net.
#tftp-secure

# Set the boot file name only when the "red" tag is set.
#dhcp-boot=net:red,pxelinux.red-net

# An example of dhcp-boot with an external TFTP server: the name and IP
# address of the server are given after the filename.
# Can fail with old PXE ROMS. Overridden by --pxe-service.
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
# server for your campus/company accidentally. The ISC server uses
# the same option, and this URL provides more information:
# http://www.isc.org/index.pl?/sw/dhcp/authoritative.php
#dhcp-authoritative

# Run an executable when a DHCP lease is created or destroyed.
# The arguments sent to the script are "add" or "del", 
# then the MAC address, the IP address and finally the hostname
# if there is one. 
#dhcp-script=/bin/echo

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
# and this maps 192.168.0.10->192.168.0.40 to 10.0.0.10->10.0.0.40
#alias=192.168.0.10-192.168.0.40,10.0.0.0,255.255.255.0

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

# The following line shows how to make dnsmasq serve an arbitrary PTR
# record. This is useful for DNS-SD. (Note that the
# domain-name expansion done for SRV records _does_not
# occur for PTR records.)
#ptr-record=_http._tcp.dns-sd-services,"New Employee Page._http._tcp.dns-sd-services"

# Change the following lines to enable dnsmasq to serve TXT records.
# These are used for things like SPF and zeroconf. (Note that the
# domain-name expansion done for SRV records _does_not
# occur for TXT records.)

#Example SPF.
#txt-record=example.com,"v=spf1 a -all"

#Example zeroconf
#txt-record=_http._tcp.example.com,name=value,paper=A4

# Provide an alias for a "local" DNS name. Note that this _only_ works
# for targets which are names from DHCP or /etc/hosts. Give host
# "bert" another name, bertrand
#cname=bertand,bert

# For debugging purposes, log each DNS query as it passes through
# dnsmasq.
#log-queries

# Log lots of extra information about DHCP transactions.
#log-dhcp

# Include a another lot of configuration options.
#conf-file=/etc/dnsmasq.more.conf
#conf-dir=/etc/dnsmasq.d

```

---

### Post by memilanuk on 2009-11-23
My only experience with dnsmasq was during a brief stint with dd-wrt on a wifi router... and not a good experience either, so can't really help you there.

Just want to say kudos for being willing to step up and put in some time and effort for the school district.  Hopefully they will take the opportunity to try something different, and not just follow the herd (moo!) with M$. 

And you get an extra BZ for prototyping the concept inside a virtual machine ;)

---

### Post by Denbert on 2009-11-23
I think I'll go change the Firewall and integrate this as gateway for the dhcp3-server on the LTSP server.

I'll make a new install and post results later, as my kids are waiting at the dining table, with wide open mouths :D

---

### Post by Denbert on 2009-11-23
> **Denbert said:**
> I think I'll go change the Firewall and integrate this as gateway for the dhcp3-server on the LTSP server.


Ok, made a clean install of the LTSP server, with 2 nic's (the install fails with only one nic?)

After the install. disable eth0 in /etc/network/interfaces

```
nano /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

auto eth1
iface eth1 inet static
    address 192.168.9.12
    netmask 255.255.255.0
    network 192.168.9.0
    broadcast 192.168.9.255
    gateway 192.168.9.254

```

Updated the /etc/hosts file:

```
nano /etc/hosts

127.0.0.1	terminal-server.hegnstoften.net	localhost.localdomain	localhost
192.168.9.12	terminal-server.hegnstoften.net	terminal-server

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

then run this:

```
echo terminal-server.hegnstoften.net > /etc/hostname
```

Then I changed the dhcpd.conf file in /etc/ltsp/dhcpd.conf

```
nano /etc/ltsp/dhcpd.conf

#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.9.0 netmask 255.255.255.0 {
    range 192.168.9.100 192.168.9.250;
    option domain-name "hegnstoften.net";
    option domain-name-servers 208.67.222.222, 208.67.220.220;
    option broadcast-address 192.168.9.255;
    option routers 192.168.9.254;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}

```

reboot the server and then run this, as you have changed nic configuration:

```
sudo ltsp-update-sshkeys && sudo ltsp-update-image
```

You will see this:

```
Parallel mksquashfs: Using 2 processors
Creating 4.0 filesystem on /opt/ltsp/images/i386.img.tmp, block size 131072.
[===========================================================-] 25939/25939 100%
Exportable Squashfs 4.0 filesystem, data block size 131072
        compressed data, compressed metadata, compressed fragments
        duplicates are removed
Filesystem size 189612.69 Kbytes (185.17 Mbytes)
        41.33% of uncompressed filesystem size (458760.87 Kbytes)
Inode table size 352400 bytes (344.14 Kbytes)
        27.63% of uncompressed inode table size (1275468 bytes)
Directory table size 371407 bytes (362.70 Kbytes)

```

When finish, you can login to your client - Here in vmware remote console:

[IMG]http://hegnstoften.net/pictures/pxe-boot-in-vmware-terminal_02.png[/IMG]

And after correct user and pass:

[IMG]http://hegnstoften.net/pictures/Ubuntu_9.10_LTSP_Server_diskless_vmware.png[/IMG]

It' runs increadbly fast in vmware remote console - really looking forward to test it on a dedicated Thin Client  :guitar:

---

### Post by cdcoley on 2010-01-21
I too am in the process of testing LTSP under VMWare ESXi 4.0.   I was curious to know how much, disk, ram and CPU did you allocate to run LTSP on your systems.   As to the RDP question, I have been racking Google to see if a connection from an RDP client on an XP machine can connect to the LTSP Server as well.

---


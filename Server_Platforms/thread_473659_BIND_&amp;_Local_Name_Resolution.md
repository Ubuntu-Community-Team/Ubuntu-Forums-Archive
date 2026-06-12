---
title: "BIND &amp; Local Name Resolution"
date: 2007-06-14
forum: Server Platforms
---

### Post by a.d.gardiner on 2007-06-14
Hey all,

I'm really struggling getting my network setup so that LAN clients can view sites hosted on my Apache2 from inside my network.

Externally I can get access to my sites hosted on the Apache2 server (statically 192.168.1.113). My router forwards requests to the apache and everything works from outside. I need BIND to perform 'Local Name Resolution' as far I'm aware.

I have 'BIND9' installed, and 'Webmin' to help me configure it, but I can't find any really clear documentation for achieving what I want.

I know you can just place entries in each LAN clients hosts file, but I'd rather not have to. I understand that doing this means that all LAN clients will have to use my Apache2/BIND machine to resolve outside requests as well.

Any ideas? ;) (go easy on me, I'm still trying to figure the whole thing out)

---

### Post by keithweddell on 2007-06-14
I'd go for dnsmasq.  It's much easier to set up and will do what you need for your LAN.  Google for set up tutorials - I think I found some on Gentoo Wiki and Debian Administrator.

Keith

---

### Post by netlogic on 2007-06-14
If your organization is smaller than 1000, Dnsmasq is the right choice for the LAN. It takes less than 10 minutes to get it running. For all your web and mail servers, I would just outsource your DNS records. It isn't worth the headache.

---

### Post by Mr. C. on 2007-06-15
While I understand your basic intention, It is a stretch to conclude that dnsmasq is "the right choice" for orgs smaller than 1000.  There are many reasons, including running a mail server where building a large, robust local cache is critical for performance.

For a simple apache configuration, dnsmasq is fine.

Nonetheless, let's not be overly dramatic about bind being difficult or headache-inducing to configure.  A single locally authoritative setup is easy enough to configure; I've instructed a lab of students in setting up their own DNS servers within an hour.  Here are some lecture notes, a lab, and homework for DNS (Week 8: [http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)).

If you need more help, please let us know.

MrC

---

### Post by a.d.gardiner on 2007-06-18
Thanks for your support guys!

The lecture notes there are dead useful too. I think I'm beginning to understand the principals a bit better.

Thing is, I've been following the tutorial at [Ubuntu Geek]("http://www.ubuntugeek.com/local-dns-cache-for-faster-browsing-on-ubuntu-machine.html#more-43") but still seem to be having some issues getting DNSMASQ up and running.

I am in this case running my machine with a static IP which I take it means the configuartion will differ a little, but I'm not too sure which bit.  I don't need DNSMASQ's DHCP function in this instance, but would like it to work locally on my machine at 192.168.1.113.

---

### Post by netlogic on 2007-06-18
It is really simple if you read the man page. You have to read the options tags.
Based on the information you have given us, we can't really help with your configuration. This is a lot simpler than you assume. It is just using host files on the server to identify dns names for all the machines in the network.

please give following information
dns server ip
domain name
list of all the server ips
dhcp range
router ip
network 
netmask
wins (if you use them)
lease time
NTP (optional)
other dhcp options you want to assign to your client.

---

### Post by netlogic on 2007-06-18
Try this... I am just guessing based on what you said...
Add all your machines in your host file on the server.
Please make sure you restart your service after the config update

bogus-priv
expand-hosts
domain=yourdomain.com
dhcp-range=192.168.1.2,192.168.1.20,12h   #range and 12hrs

# change it if the router is a different address
# default router is your dnsmasq
dhcp-option=3,192.168.1.1

dhcp-option=19,0           # option ip-forwarding off
dhcp-option=44,xxx.xxx.xxx.xxx     # set netbios-over-TCP/IP nameserver(s) aka WINS server(s)
dhcp-option=45,xxx.xxx.xxx.xxx     # netbios datagram distribution server
dhcp-option=46,8           # netbios node type
dhcp-option=47             # empty netbios scope.

---

### Post by nymphaeles on 2007-06-18
You need to make an A record for your server.  In each client machine, specify your DNS server IP in their TCP/IP configuration.
Try an 

```

nslookup your_server

``` 

to see if the DNS server responds?
As far as outside name resolution, you can specify additional DNS servers for your clients.

---

### Post by nymphaeles on 2007-06-18
For a hardcore classic text book on BIND, try DNS and BIND 4th Edition by O'Reilly.
For an online tutorial quick start, try "Resolving Domains Internally And Externally With Bnd9 And Caching Nameserver" by go to [http://www.howtoforge.net/](http://www.howtoforge.net/)

---

### Post by a.d.gardiner on 2007-06-19
Okay I think this answers the relevant bits as best I can:

dns server ip - 192.168.1.113 (assuming this is the address of the machine that will be running DNSMASQ - otherwise I believe I primarily use BT's DNS at 194.72.6.57)
domain name - I'm running a couple of fun sites from my Apache2 box - [www.soundsessions.co.uk](www.soundsessions.co.uk) and [www.chevinstaffportal.co.uk](www.chevinstaffportal.co.uk) (If you mean domain locally then I didn't define anything yet)
list of all the server ips - 192.168.1.113 (local Apache2 server)
dhcp range 192.168.1.2 to 192.168.1.254
router ip - 192.168.1.1
network - Not sure what this relates to :(?
netmask - 255.255.255.0
wins (if you use them) - Nope
lease time - 1 Day exactly

Ultimately I'm aiming to make my Ubuntu webserver (Apache2)accessible locally/internally as well as externally on the web. At present external access to the sites I host from the internet works fine - examples are [www.chevinstaffportal.co.uk](www.chevinstaffportal.co.uk) and [www.soundsessions.co.uk](www.soundsessions.co.uk) - but obviously I can't get to my sites locally/internally without creating and maintaining a hosts file on every machine in my network to resolve the addresses to my webserver at 192.168.1.113. So the way I understand it 'DNSMASQ' will a) act as DNS cache to speed up internet access for all machines on my network and b) more importantly will allow the other machines on my network to resolve internal requests for sites that are hosted on the Apache2 at 192.168.1.113. (I know this probably sounds like primary school talk but I'm learning from scratch here). It is probably worth mentioning I wasn't planning on using DNSMASQ's DHCP server.. because my router already does that at 192.168.1.1.

I originally took a look at the 'how to forge article' on "Resolving Domains Internally And Externally With Bnd9 And Caching Nameserver", but no matter how many times I tried to follow the instructions I still seem to be struggling.

Cheers for all the replies so far btw. Much appreciated.

---

### Post by Mr. C. on 2007-06-19
> network - Not sure what this relates to ?

Network is the network part of the IP address (IPs are network part/host part, the split defined by your netmask), so your network is:

192.168.1.0

MrC

---

### Post by a.d.gardiner on 2007-06-23
:) Ahhh. Well that bit makes sense enough to me.

---

### Post by a.d.gardiner on 2007-06-25
Managed to sort it out. Its really not as hard as I thought it was going to be.. just like you all said. hehe

The thing I was having trouble with was getting my head round that it just works straight out of the box if you don't mess with the configuration file. I'd messed about with mine which has broken something. So I installed it on another Ubuntu box and copied the fresh dnsmasq.conf to my machine and boom.. restart DNSMASQ and everything works nicely. 

Thanks all :)

---

### Post by jdbg on 2007-06-26
Hi, 
I have a slightly different question, but is very similar to the first post:

I have my internal network and a Linksys wrt55ag wi-fi router. I have a ubuntu server behind the router, on which there is a webserver. From outside network I see all the websites that are hosted on the server, but from the inside network I can't see the websites - I see the router admin panel.

I though of running some DNS service on my server and make the router address this DNS first.
Would this dnsmasq or BIND do for my needs?

Thanks in advance!

---

### Post by a.d.gardiner on 2007-06-26
Pretty much the same question as I had initially and as I understand it you have three main options (there are more solutions out there).

**1) The Hosts file**

All you have to do is add the sites you serve to your host file at /etc/hosts

This is the simplest way of fixing what you are experiencing. If it is just one site you host and/or you have no other machines locally that need to get to it then this might be easiest?

My hosts file looks like this, notice the entry at the bottom:

```
127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.113 chevinstaffportal.co.uk soundsessions.co.uk
```

I'm no ubuntu guru, but I believe this basically just redirects your browser to the internal location of your apache server before it tries to resolve the website address with a DNS. 

**2) BIND9**

You could setup BIND, but I couldn't manage it easily. I get the impression it has more features and is more scalable, but isn't necessarily as quick and easy to configure as DNSMASQ.  [B]

3) DNSMASQ (What I did)[/B]

I setup DNSMASQ as follows (I might not be bang on but it works for me)

Install DNSMASQ with:

```
sudo apt-get install dnsmasq
```

Now configure your hosts file on your server as before. You need to do this so that requests for your sites internally are handled and redirected to your apache2 inside the network. This file will act on behalf of all other machines in your network.

Now redirect all machines on your network to use your apache/dnsmaqs box for DNS. DONE.

If you need to configure DNSMASQ or add any features that it won't run out of the box like its DHCP server then you need to edit the file at /etc/dnsmasq.conf.

HOWEVER, the bit that threw me before, you don't necessarily need to mess with the dnsmasq.conf to start with!

I left mine looking like this:

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

# Override the default route supplied by dnsmasq, which assumes the
# router is the same machine as the one running dnsmasq.
#dhcp-option=3,1.2.3.4

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

# Send RFC-3442 classless static routes (note the netmask encoding)
#dhcp-option=121,192.168.1.0/24,1.2.3.4,10.0.0.0/8,5.6.7.8

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

Hope that is of some help :p

---

### Post by jdbg on 2007-06-27
Kind of the installation didn't work. Here is what I got:

```
jd@erebus:~$ sudo apt-get install dnsmasq
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  resolvconf
The following NEW packages will be installed:
  dnsmasq
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 191kB of archives.
After unpacking 606kB of additional disk space will be used.
Get:1 http://bg.archive.ubuntu.com feisty/universe dnsmasq 2.37-1 [191kB]
Fetched 191kB in 0s (409kB/s)
Selecting previously deselected package dnsmasq.
(Reading database ... 108964 files and directories currently installed.)
Unpacking dnsmasq (from .../dnsmasq_2.37-1_i386.deb) ...
Setting up dnsmasq (2.37-1) ...
configuration error - unknown item 'FAIL_DELAY' (notify administrator)
Starting DNS forwarder and DHCP server: dnsmasqdnsmasq: failed to create listening socket: Address already in use
 (failed).
invoke-rc.d: initscript dnsmasq, action "start" failed.

```

After the installation I tried to run the dnsmasq command and here is what I got
```

jd@erebus:~$ sudo dnsmasq
dnsmasq: failed to create listening socket: Permission denied

```

Any ideas what's wrong?

---

### Post by startlinuxtoday on 2007-09-21
yes. try installing AFTER you # sudo su. it's odd but even if you logged in as root, you sometimes get denied. another reason for failure may be that the socket address is already in use- and i have no solution as yet, i am fairly new to this dns. meanwhile, if you are running a server with dns, install lwresd.

---


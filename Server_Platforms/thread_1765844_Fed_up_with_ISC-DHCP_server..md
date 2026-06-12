---
title: "Fed up with ISC-DHCP server."
date: 2011-05-23
forum: Server Platforms
---

### Post by leej23 on 2011-05-23
Hi could someone please help me i am trying to setup a DHCP server with ubuntu server 11.
i have installed webmin but done the conf for DHCP with SSH.

the problem is the server dont start on boot but is set to do so, works fine once the server is booted an start in maualy, here is the error am getting in syslog.
```
dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
May 23 21:34:56 proxy dhcpd: ** Ignoring requests on eth0.  If this is not what
May 23 21:34:56 proxy dhcpd:    you want, please write a subnet declaration
May 23 21:34:56 proxy dhcpd:    in your dhcpd.conf file for the network segment
May 23 21:34:56 proxy dhcpd:    to which interface eth0 is attached. **
May 23 21:34:56 proxy dhcpd: 
May 23 21:34:56 proxy dhcpd: 
May 23 21:34:56 proxy dhcpd: Not configured to listen on any interfaces!

```my LAN network config: 

router 192.168.1.1
DHCP leasse's from 192.168.1.10 - 192.168.1.250

on the server i have setup eth0 as follows in interfaces file.

```
# The primary network interface
iface eth0 inet static
    address 192.168.1.2
    netmask 255.255.255.0
    broadcast 192.168.1.255
    network 192.168.1.0
    post-up iptables-restore < /etc/iptables.up.rules
    gateway 192.168.1.1
```

in resolv.conf i have set its nameserver to it's self on 192.168.1.2

my DHCPD.conf

```
option broadcast-address 192.168.1.255;
option routers 192.168.1.1;
#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "hexracecourse.net";
option domain-name-servers 192.168.1.2;

default-lease-time 600;
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
# hexrace subnet
subnet 192.168.1.0 netmask 255.255.255.0 {
    authoritative;
    ddns-updates on;
    option domain-name-servers 192.168.1.2;
    option broadcast-address 192.168.1.255;
    option subnet-mask 255.255.255.0;
    option routers 192.168.1.1;
    range 192.168.1.3 192.168.1.254;
    }

```i just cant understand whats going on.
hope someone can help.

cheers lee

---

### Post by trozamon on 2011-05-23
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

Try that link, should start you from the beginning 'til the end in setting up a server as a router.

---

### Post by SeijiSensei on 2011-05-24
Try removing the "authoritative" and "ddns-updates" directives from the subnet declaration and see if that resolves the problem.  Otherwise you've got a pretty vanilla configuration.

---

### Post by Lars Noodén on 2011-05-24
If you are just trying to serve up DHCP, then I would recommend taking a look at [dnsmasq](http://www.thekelleys.org.uk/dnsmasq/doc.html) before spending more time on the ISC DHCPd.  It's wonderfully simple to configure.  

It can also do DNS caching and PXE booting.

---

### Post by koenn on 2011-05-24
SeijiSensei +1
Lars Noodén +1

and make sure you restart dhcpd after editing its conf file, so it reads the new config. 

Also, when your dhcp server is up, it's going to conflict with the dhcp service from your router.

---

### Post by leej23 on 2011-05-24
Hi thanks for the reply's, i have sorted it i installed ubuntu 9.04 server. and worked straight away. i always seem to find problems with 11.

---

### Post by volkswagner on 2011-05-24
> **leej23 said:**
> Hi thanks for the reply's, i have sorted it i installed ubuntu 9.04 server. and worked straight away. i always seem to find problems with 11.


Did you try 10.04?  Ubuntu 9.04 [reached end of life]("https://wiki.ubuntu.com/Releases") 10/23/2010.  I would not be building any server with 9.04, especially one that will run my network infrastructure.  8.04.2 is supported until April/2013, which would be a better choice than 9.04, as far as support goes.

---

### Post by leej23 on 2011-05-27
Hi i have just relised the and have installed 10.04, was having a problem with sources.list not working anyway,
but now am back to the exact same error with it not starting on boot, dhcp is setup the exact same way. maybe DHCP is trying to start before networking is started and not picking up the setting from eth0. 

realy not sure what to do. really fed up now lol

---

### Post by Termz on 2011-08-02
Very late reply, but anyway,

The server is not starting up because it starts before network-manager is bringing up the network interface.

A solution is to write a script with "/etc/init.d/isc-dhcp-server start" in /etc/network/if-up.d/ for that particular interface

There is probably another solution for it too tho :)

---

### Post by ajpeters on 2011-08-12
1.  I believe that the recommendation for Ubuntu 11.04 is to leave webmin and go to eBox.

2.  The default configuration files in 11.04 seem to have changed. Does anyone have a good map of the current configuration files?  They do not seen to be under /etc/dhcp, and there is not any /etc/dhcp3 files or /etc/isc-dhcp files.  

3.  I have my server running as a router for a class I am teaching.  I am concerned that the changes to my dhcp server may effect this if I do not do it by hand.  Any suggestions for not screwing this up with a web based solution?

I would be glad to re post this in another link if deemed advisable.  I put it here because it seemed applicable to the current question.

---

### Post by thisspaceleftblank on 2011-10-02
I just installed this server, though the package I installed was dhcp3-server, what I got is ISC-dhcp-server. The problem for me wass that all the instructions on setting it up referred to configuration files in /etc/dhcp3 when they are in /etc/dhcp and there isn't a "dhcp3-server" service it is now "isc-dhcp-server" and you can see this in /etc/init.d directory.
After that confusion, I got it going pretty much as explained in the various HOW-TO web pages.

I don't understand why I haven't seen anything on these changes documented.

---

### Post by grafted_scion on 2011-10-24
> **ajpeters said:**
> 
2.  The default configuration files in 11.04 seem to have changed. Does anyone have a good map of the current configuration files?  They do not seen to be under /etc/dhcp, and there is not any /etc/dhcp3 files or /etc/isc-dhcp files.  
.

I spent many late nights trying to get this working but no luck

Edit the config file: /etc/dhcp/dhcpd.conf
Edit this file to include interfaces /etc/default/isc-dhcp-server

> No subnet declaration for wlan1 (no IPv4 addresses).
** Ignoring requests on wlan1.  If this is not what
you want, please write a subnet declaration
in your dhcpd.conf file for the network segment
to which interface wlan1 is attached. **
Not configured to listen on any interfaces!
this is my dhcp.conf

```
default-lease-time 600;
max-lease-time 7200;
subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.3 192.168.0.254;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
option routers 192.168.0.2;
option domain-name-servers home;
}
```this is my isc-dhcp-server

```
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/isc-dhcp-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#    Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="wlan1"
```

---

### Post by newbie-user on 2011-10-24
> **leej23 said:**
> Hi i have just relised the and have installed 10.04, was having a problem with sources.list not working anyway,
but now am back to the exact same error with it not starting on boot, dhcp is setup the exact same way. maybe DHCP is trying to start before networking is started and not picking up the setting from eth0. 

realy not sure what to do. really fed up now lol

The DHCP server has to be set up to run on a specific network interface.  Initial installation of the DHCP server requires you to tell it what interface to serve requests on.  Edit your /etc/default/dhcp3-server file to add the name of the interface on which to serve requests.  Here's my config file from my 10.04 server:

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"


Looks like grafted_scion beat me to it!  =)

---

### Post by grafted_scion on 2011-10-24
I got it working now on 11.04

Here is what i did:

```
# /etc/dhcp/dhcpd.conf
#
default-lease-time 600;
max-lease-time 7200;
subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.3 192.168.1.254;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.2;
option domain-name-servers home;
}
``````
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/isc-dhcp-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#    Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="wlan1"

``````
# location /etc/network/interfaces

auto lo
iface lo inet loopback

auto wlan1
iface wlan1 inet static
    address 192.168.1.2
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.1.1

``````
sudo ifup wlan1
sudo service isc-dhcp-server start

```

---

### Post by Vegan on 2011-10-24
I found I saved at least 1000 grey hairs by using my router to do DHCP so I can use my Linux VM for something else like applications

---

### Post by grafted_scion on 2011-10-25
I am with you about the grey hairs.
Still need to tweak my configurationfiles its not working.
At least i can start isc-dhcp-server without errors now so i made some progress.
Will report back when i got it working 100%

---

### Post by Kerberos79 on 2012-11-22
Hello everybody,

For Ubuntu 11.04:

sudo mv /etc/dhcp/dhcpd.conf /etc/dhcp/dhcpd.confbackup
sudo cp /etc/dhcp3/dhcpd/dhcpd.conf /etc/dhcp/dhcpd.conf

Try...

---


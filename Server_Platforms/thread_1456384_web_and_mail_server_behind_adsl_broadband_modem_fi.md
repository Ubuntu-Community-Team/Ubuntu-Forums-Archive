---
title: "web and mail server behind adsl broadband modem fixed IP address"
date: 2010-04-17
forum: Server Platforms
---

### Post by computer_guy2000 on 2010-04-17
I would like to host some domains from a ubuntu server running behind an adsl modem with a fixed IP address.  I am running software which needs LTS so I am using Ubuntu 8.04 LTS.

my domains (for example) are:
[www.abc.com]("http://www.abc.com")
[www.def.com]("http://www.def.com")
[www.ghi.com]("http://www.ghi.com")

my outward facing (external) IP address is 203.123.134.145 (not real)

I install ubuntu with the netcfg/disable_dhcp=true so that I can set a fixed IP address for the server.   A fixed IP address is reqired so that I can forward ports from the adsl modem to the server.

There are some setup questions when installing...

IP address: 192.168.0.212
Netmask: 255.255.255.0
Gateway: 192.168.0.1
Nameserver: 192.168.0.212 203.123.134.145 203.123.72.99
Notes:
192.168.0.212 - this server because I want to run a nameserver
203.123.134.145 - my outward facing (exernal) IP address
203.123.72.99 - the name server for my broadband provider

hostname: myserver1
domain name: localnet.net

**Question: **does domain name have to a be registered domain or can I just make up a fake one? For example, can I use localnet.net or should I use abc.com? 
Which is easier?

The results of some commands:

hostname -s
myserver1

hostname -f
myserver1.localnet.net

**the contents of /etc/hostname**
myserver1

[B]the contents of /etc/hosts
[/B]127.0.0.1    localhost
192.168.0.212    myserver1.localnet.net    myserver1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

[B]the contents of /etc/resolv.conf
[/B]search localnet.net
nameserver 192.168.0.212
nameserver 203.123.134.145
nameserver 203.123.72.99

[B]the contents of /etc/network/interfaces
[/B]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.0.212
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
    gateway 192.168.0.1
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.0.212 203.123.134.145 203.123.72.99
    dns-search localnet.net

Before I install bind I was just wondering if this looks like it is going to work.

If there are any changes to make, I can make them now before I go any further.

If you need to see any other configuration files or want the results of any commands, please let me know.

Thanks very much for your time.

---


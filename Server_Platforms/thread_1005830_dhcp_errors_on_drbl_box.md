---
title: "dhcp errors on drbl box"
date: 2008-12-08
forum: Server Platforms
---

### Post by Aximilli on 2008-12-08
Hello All,
     I am setting up an ubuntu server to use clonezilla. I have run through the drbl set up and I think everything is correct, except my DHCP3 server. Whenever I try to manually start the server I get the following error.

```

alex@acit-images:/etc/dhcp3$ /etc/init.d/dhcp3-server start
dhcpd self-test failed. Please fix the config file.
The error was:
alex@acit-images:/etc/dhcp3$


```

Informative right? I reverted back to the original dhcpd.conf file and get the same message. However, there are a few other files I have edited. 

this box has two NIC cards. eth0 is on the board, and is the connection to the rest of the network. eth1 is connected to my pushing switch. I believe I have it set so that the dhcp server only runs on eth1. To do so, I made the following changes to these files:

/etc/network/interfaces

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


# The cloning NIC
auto eth1
iface eth1 inet static
        address 192.168.14.100
        netmask 255.255.255.0
        network 192.168.14.0
        broadcast 192.168.14.255
        gateway 192.168.1.1


```


/etc/default/dhcpd.conf

```

 Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"


```

currently /etc/dhcp3/dhcpd.conf is using the default config. also, this is the result of route -n (in case this helps)

```

alex@acit-images:/etc/dhcp3$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.14.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
10.2.0.0        0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         10.2.0.1        0.0.0.0         UG    100    0        0 eth0
alex@acit-images:/etc/dhcp3$


```


Does anyone see why my dhcp server is failing to start? If any other information would be useful I'd be glad to post it. 

As always, I am very appreciative of Ubuntu's excellent community support.


Alex



P.S. I lied, the following changes are in my dhcpd.conf file:

```


# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;



# A slightly different configuration for an internal subnet.
subnet 192.168.14.0  netmask 255.255.255.0
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}


```

However, I have tried with that last entry commented out as well, with no change.

---


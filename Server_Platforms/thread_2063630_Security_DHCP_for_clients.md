---
title: "Security DHCP for clients"
date: 2012-09-27
forum: Server Platforms
---

### Post by qubaa on 2012-09-27
1. Server is installed.
2.Configuration interfaces for ISP (eth0) and clients (eth1) is done.
3. I configured dhcpd for one user (my laptop)
================
host tassman {
  hardware ethernet 00:21:70:76:d8:8b;
  fixed-address 172.22.22.100;
================

4. Laptop was plugged and ubuntu gives IP 172.22.22.100
5. Laptop was unplugged.
6. For testing purposes I reconfigure hdcpd.conf to
================
host tassman {
  hardware ethernet 08:21:70:76:d8:8b;
  fixed-address 172.22.22.5;
================
I change IP adres and MAC
7.  service isc-dhcp-server restart was done
8. I plugged laptop again and ... laptop get adress 172.22.22.100

Is there something like to flush leases for clients or something?

---

### Post by lykwydchykyn on 2012-09-27
I'm not clear on why you changed the MAC; did you change the NIC on the laptop or something?

---

### Post by qubaa on 2012-09-27
> **lykwydchykyn said:**
> I'm not clear on why you changed the MAC; did you change the NIC on the laptop or something?
I was curious what will happend if anonymous user will connect another device wich will not be registered in dhcpd.conf.

---

### Post by sandyd on 2012-09-28
you need something like
```

class "private-hosts" {
match if substring (option hardware,1,11) = "mac_address";
match if substring (option hardware,1,11) = "mac_address2";
}

pool {
range 192.168.1.31 192.168.1.254;
allow members of "private-hosts";
}
```

---

### Post by qubaa on 2012-09-28
I did some changes but i have error
```
dhcpd self-test failed. Please fix the config file.
The error was:
Internet Systems Consortium DHCP Server 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
/etc/dhcp/dhcpd.conf line 120: pool declared outside of network
pool
 ^
Configuration file errors encountered -- exiting
```

Thats my config. I would be grateful for help.

```
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "ccc.com";
option domain-name-servers 80.191.8.5, 8.8.8.8;

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
subnet 172.22.22.0 netmask 255.255.255.0 {
  range 172.22.22.2 172.22.22.254;
  option routers 172.22.22.1;
}

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

#host tassman {
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

host tassman {
  hardware ethernet 02:21:70:76:d8:8b;
  fixed-address 172.22.22.2;
}
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


#Ustawienia dla adresów MAC

class "private-hosts" {
    match if substring (hardware, 1, 8) = "02:21:70:76:d8:8b";
}

pool {
range 172.22.22.2 172.22.22.254;
allow members of "private-hosts";
}
```

---

### Post by sandyd on 2012-09-28
try this
```

#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "ccc.com";
option domain-name-servers 80.191.8.5, 8.8.8.8;

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
subnet 172.22.22.0 netmask 255.255.255.0 {
  range 172.22.22.2 172.22.22.254;
  option routers 172.22.22.1;
}

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

#host tassman {
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

#host tassman {
#  hardware ethernet 02:21:70:76:d8:8b;
#  fixed-address 172.22.22.2;
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


#Ustawienia dla adresów MAC

class "private-hosts" {
    match if substring (hardware, 1, 8) = "02:21:70:76:d8:8b";
}

pool {
range 172.22.22.2 172.22.22.254;
allow members of "private-hosts";
}
```

---

### Post by qubaa on 2012-09-29
But now Im I lose static configuration for clients...

Hmmm... one class to one client? (loudly thinking)


The same error
```
Configuration file errors encountered -- exiting^M
dhcpd self-test failed. Please fix the config file.^M
The error was: ^M
Internet Systems Consortium DHCP Server 4.1-ESV-R4^M
Copyright 2004-2011 Internet Systems Consortium.^M
All rights reserved.^M
For info, please visit https://www.isc.org/software/dhcp/^M
/etc/dhcp/dhcpd.conf line 120: pool declared outside of network^M
pool ^M
 ^^M
Configuration file errors encountered -- exiting^M
```

---

### Post by sandyd on 2012-09-30
Im not sure about this.
Lets see if we can get dhcp working again, before we get the static back.

Try this
```

#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "ccc.com";
option domain-name-servers 80.191.8.5, 8.8.8.8;

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

#host tassman {
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

#host tassman {
#  hardware ethernet 02:21:70:76:d8:8b;
#  fixed-address 172.22.22.2;
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
# This is a very basic subnet declaration.
class "private-hosts" {
    match if substring (hardware, 1, 8) = "02:21:70:76:d8:8b";
}

shared-network 172-22 {
   subnet 172.22.22.0 netmask 255.255.255.0 {
   option routers 172.22.22.1;
   }
   pool {
     allow members of "private-hosts";
     range 172.22.22.3 172.22.22.250;
   }
}

```

---


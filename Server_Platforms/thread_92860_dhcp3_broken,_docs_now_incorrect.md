---
title: "dhcp3 broken, docs now incorrect"
date: 2005-11-20
forum: Server Platforms
---

### Post by pksings on 2005-11-20
The version of dhcp3 that ships with Breezy is broken.

A config file that works fine with Gentoo, does not work with Breezy.

If I enter the subnet IP to be the same as eth0 then it rejects the whole file, as the subnet mask is invalid.
If I enter the subnet IP as the whole network (0) then it never accepts any interface and will not answer.

The following entry is with the invalid subnet mask failure config.

# dhcpd.conf
#
# Sample configuration file for ISC dhcpd
#
INTERFACES="eth0";
option domain-name "pksings.com";
option domain-name-servers phred.pksings.com ;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
default-lease-time 21600;
max-lease-time 21600;
use-host-decl-names     on;
ddns-update-style ad-hoc;
authoritative;

# Workstations at pksings.com
shared-network WORKSTATIONS {
        authoritative;
        allow client-updates;
        allow unknown-clients;
        ddns-updates on;
        subnet 192.168.1.5 netmask 255.255.255.0 {
                range 192.168.1.200 192.168.1.220;
                option routers 192.168.1.1;
                }
        }



This next entry is  no interface assigned failure.

# dhcpd.conf
#
# Sample configuration file for ISC dhcpd
#
INTERFACES="eth0";
option domain-name "pksings.com";
option domain-name-servers phred.pksings.com ;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
default-lease-time 21600;
max-lease-time 21600;
use-host-decl-names     on;
ddns-update-style ad-hoc;
authoritative;

# Workstations at pksings.com
shared-network WORKSTATIONS {
        authoritative;
        allow client-updates;
        allow unknown-clients;
        ddns-updates on;
        subnet 192.168.1.0 netmask 255.255.255.0 {
                range 192.168.1.200 192.168.1.220;
                option routers 192.168.1.1;
                }
        }

---


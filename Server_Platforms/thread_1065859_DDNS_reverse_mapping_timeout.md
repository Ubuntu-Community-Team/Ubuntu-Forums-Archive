---
title: "DDNS reverse mapping timeout"
date: 2009-02-10
forum: Server Platforms
---

### Post by ScottEChapman on 2009-02-10
I am getting the following error in my DHCP.log:
unable to add reverse map from 30.1.168.192.in-addr.arpa to squeezebox.local.lan: timed out

```
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
server-identifier       192.168.1.75;
ddns-updates on;
ddns-update-style interim;
update-static-leases on;
ddns-domainname "local.lan";
ddns-rev-domainname     "in-addr.arpa";
ignore  client-updates;
include "/var/lib/bind/keydef";

# option definitions common to all supported networks...
option domain-name "local.lan";
option domain-name-servers 192.168.1.75, 192.168.1.1;

default-lease-time 4320;
max-lease-time 8640;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the
# DHCP server to understand the network topology.

zone local.lan. {
  primary 127.0.0.1;
  key DHCP_UPDATER;
}

zone 1.168.192.in-addr.arpa. {
  primary 127.0.0.1;
  key DHCP_UPDATER;
}


subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.200 192.168.1.250;
  option broadcast-address 192.168.1.255;
  option routers 192.168.1.1;

host squeezebox {
    hardware ethernet 00:04:20:06:c2:9f;
    fixed-address 192.168.1.30;
    option host-name="squeezebox";
    ddns-hostname "squeezebox";
  }

}

```

Any ideas?

---

### Post by ScottEChapman on 2009-02-10
Figured it out.

My file name in names.conf.local had a type-o in it.

Sheesh. Wish the error was better!

---


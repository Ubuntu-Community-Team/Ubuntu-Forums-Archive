---
title: "DHCP3-SERVER Will Not Start"
date: 2007-12-13
forum: Server Platforms
---

### Post by lee_connell on 2007-12-13
I have read many posts about other issues people are having and mine doesn't seem to be related.  This is actually running on Debian Sarge fully up to date as of today.  I cannot start the dhcp3-server as it says "It's not configured to listen on any interfaces"

Can someone look at my configs here and let me know what I am missing.  This is for an internal DHCP server, very basic.

-----------interfaces---------------
auto eth0
iface eth0 inet static
        address 207.185.177.132
        netmask 255.255.255.192
        gateway 207.185.177.129
        hostname email


----------dhcpd.conf---------------
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "thedomain.org";
option domain-name-servers 207.185.177.132, 216.107.205.2;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# This is a very basic subnet declaration.

subnet 207.185.177.0 netmask 255.255.255.192 {
  range 207.185.177.20 207.185.177.60;
  option routers 207.185.177.129;
}


------------/etc/default/dhcpd3-server---------------
INTERFACES="eth0"

------------------startup-----------------------------
/etc/init.d/dhcp3-server restart
Stopping DHCP server: dhcpd3.
Starting DHCP server: dhcpd3 failed to start - check syslog for diagnostics.

-----------------/var/log/syslog---------------------

Dec 13 13:14:39 localhost dhcpd: Wrote 0 leases to leases file.
Dec 13 13:14:39 localhost dhcpd:
Dec 13 13:14:39 localhost dhcpd: No subnet declaration for eth0 (207.185.177.132).
Dec 13 13:14:39 localhost dhcpd: ** Ignoring requests on eth0.  If this is not what
Dec 13 13:14:39 localhost dhcpd:    you want, please write a subnet declaration
Dec 13 13:14:39 localhost dhcpd:    in your dhcpd.conf file for the network segment
Dec 13 13:14:39 localhost dhcpd:    to which interface eth0 is attached. **
Dec 13 13:14:39 localhost dhcpd:
Dec 13 13:14:39 localhost dhcpd:
Dec 13 13:14:39 localhost dhcpd: Not configured to listen on any interfaces!

---

### Post by koenn on 2007-12-13
I think this is due to the fact that the dhcp server address is not in the subnet you declared.

More important : are you sure you know what you're doing ? 
If you are not 
```

OrgName:    ADP Autonet
OrgID:      AUTO
Address:    175 Jackson Plaza
City:       Ann Arbor
StateProv:  MI
PostalCode: 48106
Country:    US

NetRange:   207.184.0.0 - 207.187.255.255

```
then you shouldn't be giving out addresses in that range

---

### Post by lee_connell on 2007-12-13
Hi Koenn,

I realize those IP's are routable, this is how ADP does things.  It is required for my client to connect to ADP services, use ADP printers etc...

We don't like it this way but unfortunately this is the ADP way.

I used 207.185.177.128 for the subnet and it now starts up the way it should.

I do know what I'm doing, I just am not well versed in the whole ip classing and routing scheme of things.  I am so use to using "c" class and using 192.168.1.0 / 255.255.255.0 without thinking about it.

Thanks!

---

### Post by koenn on 2007-12-14
a rogue dhcp server on a network can really mess things up, so I thought I'd better check. 
Glad to see you have things working now

---


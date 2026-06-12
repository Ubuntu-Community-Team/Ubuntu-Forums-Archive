---
title: "DHCPD questions"
date: 2009-08-11
forum: Server Platforms
---

### Post by jfmanamtr on 2009-08-11
Ok. I run an ubuntu server & use it to do the DHCP for my house. I want to use the server to lease out only sticky IP addresses for my personal computers. I am wondering how this can be done. I have tried it once & it doesn't seem to work correctly & I am not sure what I am doing wrong. I will post my dhcpd.conf when I get home. I just wanted to see if you guys had any ideas. Thanks for all the help in advance!

~John

/etc/dhcp3/dhcpd.conf
> #
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
ddns-update-style none;

# option definitions common to all supported networks...
default-lease-time 600;
max-lease-time 7200;
option domain-name "my-network";
option routers 192.168.1.1;
option domain-name-servers 192.168.1.3;
option broadcast-address 192.168.1.255;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# This is a very basic subnet declaration.
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.100 192.168.1.150;
}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.

#sticky static IP for john-pc
host john-pc {
  hardware ethernet 00:1F:C6:5D:81:9E;
  fixed-address 192.168.1.95;
}

---

### Post by noway2 on 2009-08-12
What makes you say that it is not working?  Did you run an ifconfig?

The configuration declares the DHCP as authoritative, which is correct, but you also have a router.  Routers tend to default to also being a DHCP.  Did you make sure you don't have a conflict by turning that off?

Otherwise, the jist of your conf file looks correct.  At home, I have a page book marked to an excellent how-to on combining DNS and DHCP for a LAN, so you don't have to use static IPs if you don't want to and still access everything by name.  I don't recall what it was, but I found it by googling for DNS (or bind) and DHCP.

---

### Post by jfmanamtr on 2009-08-12
Ok. This configuration does work, but it doesn't do what I want it to do. What I want is for this DHCP server to only hand out the static IPs that I assign to my computer's MAC address. 

Ex:
```
#sticky static IP for john-pc
host john-pc {
  hardware ethernet 00:1F:C6:5D:81:9E;
  fixed-address 192.168.1.95;
} 			 		
```

Right now with the way I have it set it gives out IPs in the range of 192.168.1.100 through 192.168.1.150. 

This is the line of code that does that:
```
# This is a very basic subnet declaration.
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.100 192.168.1.150;
}
```

The thing is that I don't want it to just give out the IPs. I want it to just give out the sticky statics I assigned. Trouble with this is if I remove the above subnet declaration, the whole thing stops working. If I take out the line for the range, will it continue working?

~John

---

### Post by Iowan on 2009-08-12
You could tighten up the range to one or two addresses, but then you'd still have one or two machines that could "sneak in".

---

### Post by jay.parnaby on 2009-08-12
It's been a while since I played around with DHCP so I may be wrong on this, but I thought that the sticky addresses still had to be within the range that was specifed, effectively you are reserving one of the available addresses for a specific host.

If you take out the range declaration then it should only assign the sticky addresses that you have specified

The link below is not entirely relevant but if you look at the second subnet that is defined there is no range declaration.
[https://help.ubuntu.com/community/dhcp3-server]("https://help.ubuntu.com/community/dhcp3-server")

---

### Post by jfmanamtr on 2009-08-12
@jay.parnaby:

 Actually what you showed me there looks like what I want to do. 

```
subnet  10.152.187.0 netmask 255.255.255.0 {

        option routers                  10.152.187.1;
        option subnet-mask              255.255.255.0;
        option broadcast-address        10.152.187.255;
        option domain-name-servers      194.168.4.100;
        option ntp-servers              10.152.187.1;
        option netbios-name-servers     10.152.187.1;
        option netbios-node-type 2;

        default-lease-time 86400;
        max-lease-time 86400;

        host bla3 {
                hardware ethernet 00:KK:HD:66:55:9B;
                fixed-address 10.152.187.2;
        }
}
```

This section here show a subnet declaration without a range associated with it. 
From the looks of it the entire setup is done through the sticky statics like I want to do. I will test this out when I get home. Thanks for the link!

~John

---

### Post by jay.parnaby on 2009-08-12
No problem, hope it works for you

---


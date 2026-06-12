---
title: "Security for static adresses from network"
date: 2012-10-27
forum: Server Platforms
---

### Post by qubaa on 2012-10-27
I configured dhcpd
```
# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;
# option definitions common to all supported networks...
option domain-name "xxxx.com";
option domain-name-servers xxx.xxx.xxx.xxx, xxx.xxx.xxx.xxx;
default-lease-time 600;
max-lease-time 7200;
# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the.
# DHCP server to understand the network topology.

subnet 172.22.22.0 netmask 255.255.255.0 {
}
```

When I connect PC with automatic condifuration everything is OK: PC don't get adress. BUT when I set configuration on PC manually to 172.22.22.10 and set gateway and DNS and plug it into ubuntu PC has internet connection.
Is there any way to denied such action from local network?

---

### Post by FrankT-Qc on 2012-10-27
Hey !

DHCP is just in charge of providing configuration to hosts who are not statically configured. Per say, you could take it off the network after it's job is done; it has nothing to do with routing things or deciding who's allowed to talk.

If you want to control who's allowed to use the network, weither you address commes from DHCP or not is irrelevant. What you want to setup is probably a firewall.

A quick explanation :
[https://help.ubuntu.com/8.04/serverguide/firewall.html](https://help.ubuntu.com/8.04/serverguide/firewall.html)

I personnaly prefer iptables :
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

For the absolute beginner or for simple systems, there is "Firestarter" which is GUI and has the advantage of listing most of what it blocks (so you know why something just stopped working...)

There is also a software called "Firewall Builder" in the repos. It's a nice graphical way to build iptables scripts.

have fun

---


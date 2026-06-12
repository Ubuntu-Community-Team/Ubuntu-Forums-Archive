---
title: "Clean install of isc-dhcp-server on clean install of 12.04"
date: 2012-05-27
forum: Server Platforms
---

### Post by jsylvia007 on 2012-05-27
I just got through installing Ubuntu 12.04, and configured Apache and Bind, both of which are working flawlessly.

I'm attempting to configure isc-dhcp-server, and although I can finally get the service to start, I can't get it to hand out any addresses.

Below is my config...  Am I missing anything?  Is there a known bug?  I've looked through the syslog and I don't see anything out of the ordinary...

####START_CONFIG####

```
ddns-update-style interim;
authoritative;
log-facility local7;
allow unknown-clients;

subnet 192.168.0.0 netmask 255.255.0.0 {
        range 192.168.10.1 192.168.11.254;
        option domain-name-servers 192.168.2.20;
        option domain-name "lindongroup.com";
        option routers 192.168.2.20;
        option broadcast-address 192.168.255.255;
        default-lease-time 600;
        max-lease-time 7200;
}

```
####END_CONFIG####

SO - SOLVED...  I never had a problem.  Because I am remote and testing with a VMWare Machine, I decided to use DHCPING...  Evidently you can't use DHCPING from the same machine running the DHCP Server.  On a hunch I tried installing DHCPING on another machine on the network and it worked first shot...  :Cue the 'the more you know' music:

---


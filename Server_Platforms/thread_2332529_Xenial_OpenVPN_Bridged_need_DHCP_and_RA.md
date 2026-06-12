---
title: "Xenial OpenVPN Bridged need DHCP and RA"
date: 2016-08-01
forum: Server Platforms
---

### Post by GizahNL on 2016-08-01
I'm trying to set up my laptop as an bridged OpenVPN (TAP) client for my home network. To register myself to my home network for DNS reasons I need the client to work as an DHCP client. For IPv6 I need router advertisements to work to statelessly set-up IPv6 adresses. 

However the NetworkManager applet does not allow me to enable running a DHCP client nor does it allow me to allow router advertisements. 

Running dhclient from commandline works, however due to the connection being managed by networkmanager the settings are overridden immediately.

The same goes for accepting router advertisements: /proc/sys/net/ipv6/conf/tap0/accept_ra is immediately reset to 1 where (according to a guide I read) it should be on 2 for RA to work.

Anyway around this? As the point and click way of Networkmanager is desirable over running a command line script.

---

### Post by wildmanne39 on 2016-08-01
*Thread moved to **Server Platforms**.*

---

### Post by GizahNL on 2016-08-11
well turns out FreeBSD doesn't hand out link-local adresses to bridge interfaces without explicitly being told to. RA is working now. 

DHCP still is not however: I know of no way to configure networkmanager to treat the OpenVPN tap0 device it creates to be managed by DHCP

---


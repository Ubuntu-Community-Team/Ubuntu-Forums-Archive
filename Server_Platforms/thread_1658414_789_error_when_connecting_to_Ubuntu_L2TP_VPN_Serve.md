---
title: "789 error when connecting to Ubuntu L2TP VPN Server"
date: 2011-01-02
forum: Server Platforms
---

### Post by bogdan_5844 on 2011-01-02
Hi all. I have a server running Ubuntu 10.04 LTS, with xl2tpd/openswan/ppp IPSec/L2TPD VPN Setup that I'm trying to make work. This server is behind a DD-WRT firmware router, if that matters, and the router has fixed internet IP.

I've tried to set up this VPN using this guide: [http://www.jacco2.dds.nl/networking/openswan-l2tp.html#L2TPconfigLinux](http://www.jacco2.dds.nl/networking/openswan-l2tp.html#L2TPconfigLinux) , but when I try to connect to the VPN using Windows 7, it throws out 789 error - the security layer encountered a processing error during the initial negotiations with the remote computer.

I've double checked the xl2tp configuration, and the ipsec configuration. The ppp configuration I've generated using xl2tppp-config, but I am not sure that I've selected the right things, since a google search returned me setting ppp for connecting to the internet through a modem, nothing VPN related.

I do believe that the problem is somewhere between the l2tp tunnel and the ppp connection - maybe l2tp doesn't pass the correct information to ppp?

Any help?

---


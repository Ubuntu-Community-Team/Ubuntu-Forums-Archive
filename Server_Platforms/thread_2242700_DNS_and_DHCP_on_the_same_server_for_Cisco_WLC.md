---
title: "DNS and DHCP on the same server for Cisco WLC"
date: 2014-09-03
forum: Server Platforms
---

### Post by DravenHavok on 2014-09-03
Greetings Ubuntu community,

It's been many years since I've delved in the Linux world and I am now trying to set up a lab with a Ubuntu server that can provide DNS and DHCP to a wireless network. I have a 2500 series Cisco wireless LAN controller and some of the things I need to be able to do are static DNS entry for WLC so that the Access Points can resolve their broadcast to an IP address, and DHCP option 150 for the access points to get their TFTP. 

Would it be a good idea to put both DNS and DHCP on the same server? I have a single physical server with VMWare 5.1 installed, so far 1 virtual machine (Ubuntu 14.04) with the DHCP service package installed. 

I feel like I am trying to do something really simple in an overly complicated way, but I wasn't able to find anything other than the following resources:

[https://help.ubuntu.com/community/isc-dhcp-server](https://help.ubuntu.com/community/isc-dhcp-server)
[https://help.ubuntu.com/14.04/serverguide/dns-configuration.html](https://help.ubuntu.com/14.04/serverguide/dns-configuration.html)

Thank you for any suggestions or help in advance.

~Draven

---


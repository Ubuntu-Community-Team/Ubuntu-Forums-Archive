---
title: "ubuntu 16043 live server does not get an address from the dhcp server but desktop"
date: 2017-11-22
forum: Server Platforms
---

### Post by bigsigh on 2017-11-22
Trying to install 16.04.3 server to a supermicro x11ssh-f 4 nic board.

Tested with the 64 bit desktop live cd, booted fine and as I plugged the ethernet cable into each nic one at a time, each nic would pull an address from the network dhcp server, assumed all was good.

During the install of server 16.04.3 using a cd the installer would not pull an address via dhcp.
I went ahead with the install thinking I'd fix it at the cli but none of the typical commands for ip setup work. 
In syslog there are dhcpdiscover entries for the nic that's plugged in but no response.


Is there something basic I'm missing that the desktop iso has and the server iso does not?


I checked a 14.04 server install cd I've used before and it did not pull an address either.
I want to use the server install iso because I want raid1.

---


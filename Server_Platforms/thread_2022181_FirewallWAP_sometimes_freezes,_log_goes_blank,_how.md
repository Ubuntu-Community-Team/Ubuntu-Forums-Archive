---
title: "Firewall/WAP sometimes freezes, log goes blank, how do I troubleshoot?"
date: 2012-07-10
forum: Server Platforms
---

### Post by RyanRahl on 2012-07-10
I have an Ubuntu server 12.04 (64bit 3.2.0-26) set up as a firewall, wireless access point (hostapd daemon & atheros ar928x with ath9k driver), openvpn server, samba server (500GB software RAID1), dhcp server (udhcpd) and DNS forwarder (BIND). For some reason it will randomly freeze up and the syslog file will go blank and it will have to be power cycled manually to get it back up. It was happening more frequently before I switched to the 3.2 kernel. When I was on the 3.0 kernel and I would check the syslog after a power cycle it would always lock up right after Apple equipment (specifically a new MacBook Pro, and iPad and and and iPhone 4 [not my equipment btw :\]) attempted to connect to the wireless access point. So I upgraded the kernel and everything was all good and I had a 31 day uptime when it did it again, only this time when I checked the syslog after the power cycle it went blank while it was handling some normal DNS requests and even looking at that the time doesn't exactly match up. So I guess my questions are: Can I increase the verbosity of the log file to give me more information, will a more detailed log file actually help me here and how would I go about changing the log file settings to an appropriate level for this situation? Also if there is any troubleshooting tips that anyone has for this I would appreciate it a lot. Is there some sort of system monitoring software that would be good for this? Thanks.

---


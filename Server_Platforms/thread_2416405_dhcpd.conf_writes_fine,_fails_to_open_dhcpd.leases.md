---
title: "dhcpd.conf writes fine, fails to open dhcpd.leases for append, chmod has not worked"
date: 2019-04-09
forum: Server Platforms
---

### Post by red-squiggly-line on 2019-04-09
Hello,
I'm coming up short for the reason I'm unable to get DHCP leases written to /var/lib/dhcp/dhcpd.leases.  


[LIST]
[*]I have found a few resources which mentioned creating the file via touch, however the file is already present.  I have also removed it then created it via touch, just to be sure. 
[*]Per the dhcpd.leases manpage I altered the apparmor file for /etc/apparmor.d/usr.sbin.dhcpd which did nothing as it already seemed to be configured correctly. 
[*]I have now stopped apparmor completely and restarted DHCP, this did not seem to make any difference. 
[*]I have executed a chmod to 0664 on /var/lib/dhcp/dhcpd.leases just as an experiment but whenever DHCP is restarted, the file is rewritten as 0644 permissions, which seems like it should still be ok? 
[*]I am able to write to /etc/dhcp/dhcpd.conf through a Python3 script run via Crontab.  dhcpd.conf looks to have the same permissions as dhcpd.leases, so I am at a loss there? 
[*]The Crontab script is of course run as root so it may write to /etc/* 
[/LIST]
 
This is a virtual box living inside a DMZ so I can't just apt-get any packages, but not sure I need anything else.

I'm not using netplan as this box has some specific vendor-class declarations in the dhcpd.conf file and b/c a few other reasons related to our org's knowledge base.  So I'm still using /etc/network/interfaces for config.

What other info can I provide?  This seems like it may be something simple I'm missing but I'm out of ideas.

Any help is very appreciated, thank you for reading!

EDIT: Solved with the following:

(Forgot to mention in OP I'm working with two NICS which complicated things a bit.)

dhcp was not opening leases file, yet permissions all looked fine, fixed by:

edited /etc/default/isc-dhcp-server interfacev4 is set to only <device-facing-nic>  

$ sudo ip a flush <device-facing-nic>
$ sudo systemctl restart networking.service
$ sudo systemctl restart isc-dhcp-server

checked /var/log/syslog and all seems well now.  

hopefully this helps somebody out there! cheers!

---


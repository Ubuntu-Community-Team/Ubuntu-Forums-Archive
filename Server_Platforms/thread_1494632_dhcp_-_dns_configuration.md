---
title: "dhcp - dns configuration"
date: 2010-05-27
forum: Server Platforms
---

### Post by chinna saaeb on 2010-05-27
I want to configure a server using 10.04 and with following

server1.server.com   main server web and mail server, dns/dhcp server. could also be cnfigured as a internet gateway.

server2.server.com  database sever on windows 2003


client1       a client machine to tests programs. Has lamp installed and will 

I need a static IP for server 2 and client 1. Rather server1 should give it the same ip addrees. Alternatively it shoud be accessible by a independent domain name.



other clients  ip from dhcp. use various windows (xp, vista etc)
i gone through ubuntu documentation / wiki. But couldn't
can somebody guide particularly about dns/dhcp configuration

---

### Post by terazen on 2010-05-27
If the guides available on the internet aren't working for you, then you should read through the man pages for dhcpd and named.conf.  Also these sites have some good links to information.
[http://www.isc.org/software/](http://www.isc.org/software/)
[http://www.bind9.net/](http://www.bind9.net/)

---

### Post by Iowan on 2010-05-27
I'm especially fond of DNSMasq for DNS/DHCP server. For my small network, it does wonderful a job of linking the two functions.
It's in Repos... [Here]("https://help.ubuntu.com/community/Dnsmasq") is a help page

---


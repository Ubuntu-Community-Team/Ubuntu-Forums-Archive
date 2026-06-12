---
title: "dhcp3-server problem"
date: 2010-05-14
forum: Server Platforms
---

### Post by mituw16 on 2010-05-14
Hello all, 
This isnt really a problem as much as it is annoying.

to start, the router and dhcp server for my network is a pc with 2 nics running ubuntu 10.04 server. 

Now i just recently upgraded to 10.04, and back when it was under 9.10, if i read the dhcp3-server logs it would say something like 

"DHCPREQUEST blah blah blah from (nomad)"
"DHCPACK blah blah blah" 

anyways, in this format, nomad was my macbook pros hostname on the network. 

since upgrading, the dhcp3-server logs now read 

"DHCPREQUEST blah blah blah from (my macbook pro's mac address)"
"DHCPACK blah blah blah" 

So basically what im asking is why since upgrading to 10.04, are the dhcp3-server logs now saying dhcp syn/ack from a computers mac address instead of a syn/ack from the hostname of said computer? 

As an interesting side note, in the logs on 10.04, it does show from the host name of windows computers, its only mac's where it shows the mac address instead of the hostname.

---

### Post by mituw16 on 2010-05-15
Bump

---


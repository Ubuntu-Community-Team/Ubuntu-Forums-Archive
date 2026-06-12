---
title: "Shorwall issue : unable to forward port"
date: 2010-06-27
forum: Server Platforms
---

### Post by jagnikam on 2010-06-27
Hi all,


I am trying to forward port from gateway server to local machine. Config file parameters are as following ....
net : 123.122.121.111 
fw  : 172.16.1.1
local machine IP  : 172.16.1.2

/etc/shorewall/rules
ACCEPT  net     fw      tcp     389
DNAT    net     loc:172.16.1.2:389     tcp     389

/etc/shorewall/shorewall.conf
IP_FORWARDING=On
MARK_IN_FORWARD_CHAIN=Yes

from outside network 
#telnet 123.122.121.111 389
Trying 123.122.121.111
telnet: Unable to connect to remote host: Connection refused


Please guide me for setting up port forwarding. Thanks in advance.

---


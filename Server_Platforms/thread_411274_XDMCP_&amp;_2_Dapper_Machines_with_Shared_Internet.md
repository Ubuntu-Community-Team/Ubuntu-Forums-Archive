---
title: "XDMCP &amp; 2 Dapper Machines with Shared Internet Connection - Black Screen"
date: 2007-04-16
forum: Server Platforms
---

### Post by srangelov on 2007-04-16
Hi!
I am trying to log in to Ubuntu 1 from Ubuntu 2 using XDMCP, but after selecting the IP address I get black screen with white X cursor.
The connection is as follows:
Internet -> Voice Router -> Ubuntu Dapper (machine 1) ---(shared internet connection)--> Ubuntu Dapper (machine 2)
Here is the IP scheme:
Router - 192.168.0.1
Ubuntu 1 Eth0 - 192.168.0.10
Ubuntu 1 Eth1 - 192.168.1.1
Ubuntu 2 - 192.168.1.2
Ubuntu 1 has Firestarter with shared Internet connection to Ubuntu 2 and allowed all connections from 192.168.1.2
If I try to log in to Ubuntu 1 from Ubuntu 2 using XDMCP the only thing I get is black screen with white X cursor. The strange thing is that if I try to remotely log in to Ubuntu 2 from Ubuntu 1, after selecting the IP address instead of either the login screen on Ubuntu 2 or the black screen I am forwarded back to login screen on Ubuntu 1.
Probably the problem is in the shared Internet connection, because I tried XDMCP with 2 machines connected with a router and it just works fine.
Do I need to forward port 177 and/or 6000? Or it has anything to do with the xhost?
Any help would be highly appreciated!

---

### Post by srangelov on 2007-07-03
I got the answer:
Just go to the System > Administration > Networking > and add to the Hosts:
the corresponding IP of the PC - localhost. e.i.
For the first Ubuntu I entered:
192.168.1.1 - localhost
and for the other ubuntu:
192.168.1.2 - localhost.

---


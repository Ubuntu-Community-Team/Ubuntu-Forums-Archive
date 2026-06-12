---
title: "internet settings"
date: 2010-08-12
forum: Server Platforms
---

### Post by speedygarth on 2010-08-12
hi all i`ve been fighting with my new server for days now i`m trying to share an internet connection from the modem/router to the local network. i`ve set up everything on the squid acl and given the machine an IP address on the network and it is now visible on the network.

the problem is no users can access the internet via the server but its odd coz i`ve followed (tried) some useful guides/tutorials on the matter but to no avail.
i`ve got two network cards on my server to be. both have been set up with IP addresses from the local network 192.168.1.0/24 i`ve been through all likely setting the whole day.

i`ve got an ethernet cable connecting the server to the modem/router and another cable running to the LAN from the server`s second nic.
maybe i missed something,could somebody assist coz i`m about to give in to the dreaded Windows!!

---

### Post by spynappels on 2010-08-12
Your problem is possibly due to both NICs having addresses on the LAN. One should have a WAN or router LAN  address. The details of this will depend on how you get your Internet. But you should probably be running 2 separate LANs with different subnets, one to connect to the modem/router and one to connect to the LAN proper.

---

### Post by speedygarth on 2010-08-12
thanks for the reply..i connect through a modem/router which does not have linux support (its a chinese brand) so right now the modem drivers are installed on a windows machine which is plugged in through a usb cable from the modem, the ethernet link port on the modem is currently connected to the LAN switch, meaning all computers on the LAN can browse directly by using the modem/router as a gateway and dns server.

but that means that the traffic/usage is not controlled from a central point in terms of bandwidht management i`m  very interested in filtering the traffic with Squid and blocking certain websites..its sad coz i know what i`d like to achieve in principle but i cannot make it work!! somebody HELP!!!!
maybe some help on setting up the second nic (eth2) to have an IP address from the Modem/router.
from there i think i`ll be home!

---


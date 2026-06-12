---
title: "How to change default network interface to eth0:1"
date: 2008-05-27
forum: Server Platforms
---

### Post by pongtawat on 2008-05-27
Dear all,

As the title say, could anyone please tell me how could I change the default network interface to eth0:1?

For some reason, on my network a static IP can only receive connections from outside but cannot initiate connections to outside. A DHCP IP is the reverse: it can only initiate connections out, but not receive connection. So, my server need to have 2 IP addresses, one static (A) for accepting connection and one DHCP (B) for getting updates.

The problem is, if I set eth0 to static IP and eth0:1 to DHCP IP, Ubuntu will try to use IP A and eth0 to connect out, which will fails. On the other hand, if I set eth0 to DHCP and eth0:1 to static IP, things will work as expected. But sometime eth0:1 will just disappeared, making my server inaccessible.

So, I think I have to set eth0 to static IP and found a way for my server to connect out using eth0:1.

Any other solutions are also welcome :)

Thank you,
Pongtawat

---

### Post by gtdaqua on 2008-05-27
basically you two have routes that you want to connect. Your internet route is always called the 'default' route

say for e.g. eth0 will be 192.168.1.0/24 network - 
do not configure the default gateway for this connection. By ARP broadcast you can simply connect to any other machine in 1.0 network.


say your second connection is for internet - 192.168.2.0/24 network
configure the default gateway. All internet traffic will exit out this route.

If you have a router 192.168.1.10 pointing to 172.17.1.0/24 then you need to add an explicit route entry in ubuntu like this:
> 
/sbin/route add -net 172.16.1.0 netmask 255.255.255.0 gw 192.168.1.10 eth0


you have to do it manually unless your default gateway (2nd network) has a route to 172.16.1.0 network. By default, for routes where no manual entry exists, routes will go to default gateway.

---


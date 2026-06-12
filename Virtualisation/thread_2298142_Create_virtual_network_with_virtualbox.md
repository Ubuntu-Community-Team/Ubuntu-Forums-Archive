---
title: "Create virtual network with virtualbox"
date: 2015-10-09
forum: Virtualisation
---

### Post by chris137 on 2015-10-09
Hi,

This acutally is a virtualbox-related question so I hope I'll get help here anyway.
I am currently trying to create a test-setup for my firewall.
For this I got 4 virtual boxes running ubuntu-server. Let's call them A, B, C and D.
Here a quick view if it helps:
A 192.168.1.1
B 192.168.5.235
C 10.65.66.130
D with 3 interfaces:
  eth0 192.168.1.254
  eth1 10.65.66.131
  eth2 10.65.66.129
All 10.65.66.xx-adresses are actually static IPs accessible from the internet.

My issue right now is that I'm not sure how to link those virtual machines.
I  want to create a network where only these 4 machines and maybe a fifth  for testing have access to (no access to the host-network).

Any ideas?

---

### Post by SeijiSensei on 2015-10-09
[https://www.virtualbox.org/manual/ch06.html#network_hostonly](https://www.virtualbox.org/manual/ch06.html#network_hostonly)

---

### Post by chris137 on 2015-10-10
Thanks a lot.

That's what I tried.
The host can ping/ssh to all of them but the guests can't communicate with each other.
I set static IPs manually in /etc/network/interfaces
ifconfig shows the setup I want.
Do I need to create certain routes by myself?
How would e.g. B communicate with C if I don't?

---

### Post by SeijiSensei on 2015-10-10
The hosts can only communicate with each other if you either put them all in the same IP subnet, or designate one of them as a router and set up the appropriate routes.  The method described is designed for all the virtual machines to reside behind a single host.  If you want to be able to reach them from the external network, you need routing and masquerading as well.  

Basically think of them as all connected to a single network switch that itself is connected to a router, in this case the VB host.  Put all the virtuals in the same subnet, like 192.168.168.0/24.

---

### Post by chris137 on 2015-10-11
Well that was very helpful now.
Actually it's not that complicated to think of it. Maybe I just needed some distance from the issue.

One of these hosts is the firewall with 192.168.1.254
Am I right in setting the default route of all servers to that IP?
Is there anything I need to do on the firewall-guest in terms of routes?

---

### Post by SeijiSensei on 2015-10-11
One of the virtuals needs to have two interfaces, one of which would be shared with all the other virtuals and them pointing to it as their default gateway.  I'd set up the second interface to use NAT and have it route out through the host.  

The virtual guests will not be visible from the other side of the host using this arrangement.  If you need to reach them, you can use port forwarding on the VB host, or abandon the virtual networking approach all together and put each machine on the same network as the host using bridged interfaces rather than NAT or host-only.

---

### Post by chris137 on 2015-10-13
As you suggested I created a VM with one host-only- and one NAT-interface.
I now set up all the necessary routes and everything works as desired.

Sadly I have a new issue now which isn't related to virtualisation though (I think..)

Thanks for your help!

---


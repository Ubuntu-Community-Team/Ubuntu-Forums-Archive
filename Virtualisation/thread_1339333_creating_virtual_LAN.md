---
title: "creating virtual LAN"
date: 2009-11-27
forum: Virtualisation
---

### Post by memilanuk on 2009-11-27
Hello,

I am running Virtualbox 3.0.12 with Windows Vista as the host OS and a handful of Linux distros as the guest machines.  What I would like to do is create a virtual LAN where only *one* machine has actual 'direct' access to the real network (that the host is on).

I was envisioning something where my existing physical LAN would become 'the Internet', and the virtual machine acting as a gateway with two NICs would be the connection between the physical LAN and the internal virtual LAN.  The object here is to get some experience setting up and running various services on the virtual gateway machine (firewall, proxy, port forwarding, port knocker, VPN, etc.) and then do other interesting things with the guest machines inside the virtual LAN.

So... the first machine would be the gateway machine, with two NICs: the first one I was thinking of using a bridged connection vs. a NAT connection, so that it can access the real world network but also be reachable (i.e. offer services to) from the physical LAN.  The second one, the 'inward facing' NIC is where I'm a little less confident of what I want/need.  I've been looking at the Virtualbox manual and at the article [here]("http://www.dedoimedo.com/computers/virtualbox-network-sharing.html") and I'm still not entirely sure of the difference between 'host only' and 'internal network' for this application.  

If anyone has any tips or suggestions, I'm open.  In the mean time I'll keep reading & searching... ):P

Thanks,

Monte

---

### Post by bodhi.zazen on 2009-11-27
Give your first VM two nic, the first bridged with an IP on your LAN.

The second nick you set on your virtual lan, you can use what you want, 10.0.0.0/8 or what you will.

Use that first machine then as a firewall, router, what have you.

---

### Post by memilanuk on 2009-11-27
Here is a 'map' of what I have in mind...

[IMG]http://i12.photobucket.com/albums/a210/milanuk/NetworkDiagram.png[/IMG]

Any insight to the pros or cons of using 'host-only adapter' vs. 'internal network' for the virtual LAN connections?

The bits and pieces I've been able to glean indicate that the 'host-only adapter' includes the host OS in the virtual LAN (which might be nice for accessing machines vis VRDP, but not strictly necessary). There are some places that allude to there being a difference in how the machines are connected together in their virtual LAN i.e. router or switch but I can't get a real clear picture as to what exactly is going on.

Thanks,

Monte

---


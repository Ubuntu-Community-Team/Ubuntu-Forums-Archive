---
title: "Virtual server Gateway question"
date: 2016-08-06
forum: Virtualisation
---

### Post by brent1975 on 2016-08-06
Hello - We are a small company and thinking about purchasing a new server to run Hyper-V on it. I am going to have a 2012 R2 VM, DNS VM, and a print server VM. I was thinking about standing up a Ubuntu VM as well. I am wanting to set the server up using iptables and all VM's and host go through the ubuntu server for incoming and out going traffic. I would have to treat this server like a gateway. Is this possible to do? We are trying to eliminate some overhead costs with multiple servers if we can do all this on a single server.

How would I go about doing this? I am semi moderate with iptables.  Would the server need two NIC cards?

Thanks in advance

---

### Post by SeijiSensei on 2016-08-06
No, you can have just one NIC unless you're intending to route traffic through the box as well.

Do you mean you intend to treat the host computer as a gateway, or use an Ubuntu VM as the gateway with the other VMs connecting through it?  That's probably doable; the gateway VM would need two virtual NICs though.

For simple services like printing and DNS, though, I'd just set up the machine to have a "bridged" adapter so it gets an address on the main network (the one the host is on) and let clients talk directly to it.  Routing everything through a gateway seems like a lot of work, and I'm not convinced it's any more secure.

---

### Post by brent1975 on 2016-08-07
I would like if possible use the Ubuntu VM as the gateway and all traffic go through that.

---


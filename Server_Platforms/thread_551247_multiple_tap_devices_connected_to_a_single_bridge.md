---
title: "multiple tap devices connected to a single bridge"
date: 2007-09-14
forum: Server Platforms
---

### Post by ranamalo on 2007-09-14
Hey all,
I am trying to use my server (dual xeon ubuntu feisty two nics) as four or five (or more) different virtual servers using virtualbox.  I have a 192.168.0 network netmask 255.255.0.0

I want all the virtual servers to be available on the network as different kinds of servers (file server, invoice system server, dhcp server, testing server, etc.)

My question is: is it possible with only two nics to have each of the four or five virtual servers to have it's own unique ip address on the regular 192.168.0 network?

Could I, for example, connect multiple tap devices to a single bridge?  Or perhaps if someone has another way of solving this issue, I'd be interested in hearing it.

Thanks in advance.....

---

### Post by ranamalo on 2007-09-17
Does anyone know if I am going to need a nic for each virtual server in order to have them basically fully available for all services.  I know I could do port forwarding, but I'd rather have all ports available for each virtual machine.

Anyone?

---


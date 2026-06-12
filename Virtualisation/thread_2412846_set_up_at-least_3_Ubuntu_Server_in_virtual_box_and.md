---
title: "set up at-least 3 Ubuntu Server in virtual box and each have different NAT IP"
date: 2019-02-18
forum: Virtualisation
---

### Post by cheekeat97 on 2019-02-18
How to modify each into different Ip address

---

### Post by dmnur on 2019-02-19
From VirtualBox User Manual, section 6.3 (emphasis mine):
> A virtual machine with NAT enabled acts much like a real computer that connects to the Internet through a router. The router, in this case, is the Oracle VM VirtualBox networking engine, which maps traffic from and to the virtual machine transparently. **In Oracle VM VirtualBox this router is placed between each virtual machine and the host. This separation maximizes security since by default virtual machines cannot talk to each other.**

So the standard NAT won't help you in your case. But you can use **internal networking** (see section 6.6 of the manual) plus **the NAT service** (section 6.4):
> The Network Address Translation (NAT) service works in a similar way to a home router, grouping the systems using it into a network and preventing systems outside of this network from directly accessing systems inside it, but letting systems inside communicate with each other and with systems outside using TCP and UDP over IPv4 and IPv6.

A NAT service is attached to an internal network. Virtual machines which are to make use of it should be attached to that internal network. The name of internal network is chosen when the NAT service is created and the internal network will be created if it does not already exist.

---

### Post by SeijiSensei on 2019-02-19
You might be better off using bridged networking, unless there's some reason to hide the servers behind the host operating system.

---

### Post by deadflowr on 2019-02-19
*Thread moved to **Virtualization** *

---


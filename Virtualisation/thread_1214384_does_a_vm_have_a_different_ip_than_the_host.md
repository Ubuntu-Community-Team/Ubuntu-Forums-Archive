---
title: "does a vm have a different ip than the host?"
date: 2009-07-15
forum: Virtualisation
---

### Post by Dustin2128 on 2009-07-15
I feel that would be quite important when setting up a virtual server. My host is a pretty heavily modified ubuntu 8.04 desktop edition system, and the guest is an 8.10 server (didn't feel like waiting another 30 minutes to try the setup) I don't have apache or any web server software, just a load of kde crap, and 3 desktop environments. Using virtualbox 2.2.4 closed source.

---

### Post by veloce on 2009-07-15
> **Dustin2128 said:**
> I feel that would be quite important when setting up a virtual server. My host is a pretty heavily modified ubuntu 8.04 desktop edition system, and the guest is an 8.10 server (didn't feel like waiting another 30 minutes to try the setup) I don't have apache or any web server software, just a load of kde crap, and 3 desktop environments. Using virtualbox 2.2.4 closed source.

There are three ways of networking virtual machines:
host only
nat
bridged

In all cases the vm perceives a different ip to the host - two of them on a different subnet.

For a server, you want to use bridged networking. This gives the vm a separate ip on the hosts network.

---

### Post by Dustin2128 on 2009-07-15
bridged networking? sorry I'm new to servers. Could you explain a little more in depth? :)

---

### Post by doas777 on 2009-07-15
a bridge is a device that connects two physical networks as though they were one. in this case, it bridges the guest virtual network switch to your hosts physical network connection, and thus to the rest of the hosts. so your virtual network will be part of your local network. it's probably the best way. the default in vmware is nat, but not sure about vbox.

good luck

---

### Post by Dustin2128 on 2009-07-15
so let me get this straight: it would be an actual physical thing? I'd prefer to stick with software.

---

### Post by PilotJLR on 2009-07-15
No, these networks are in software.

So (random example), your host would be 192.168.1.100 and your VM could be 192.168.1.200

---

### Post by doas777 on 2009-07-16
> **Dustin2128 said:**
> so let me get this straight: it would be an actual physical thing? I'd prefer to stick with software.

no it is a virtualization of hardware. the terms "Physical Network" "Logical network" and "Virtual Network" are very important to the core of network theory. a bridge is an OSI Layer 1 and 2 Device, meaning it operates at the "Physical Layers" (hubs, bridges, switches). layers 3-4 are "logical" (routers, etc), and layers 4 and above are "virtual" (software). 

in your software, the VMnetwork is pretending to be 3 or 4 physical devices. it just pretends to be a real network.
the area being served by a switch is called a physical network, even if its all just software running inside your PC.

VMs really confuse terminology

---

### Post by veloce on 2009-07-16
> **Dustin2128 said:**
> I feel that would be quite important when setting up a virtual server. My host is a pretty heavily modified ubuntu 8.04 desktop edition system, and the guest is an 8.10 server (didn't feel like waiting another 30 minutes to try the setup) I don't have apache or any web server software, just a load of kde crap, and 3 desktop environments. Using virtualbox 2.2.4 closed source.

Do a search on "virtualbox bridged networking".  There's bound to be a good howto that explains the concepts as well as the practice.

---


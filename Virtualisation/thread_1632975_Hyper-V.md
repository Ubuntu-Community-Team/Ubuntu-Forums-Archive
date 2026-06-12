---
title: "Hyper-V"
date: 2010-11-28
forum: Virtualisation
---

### Post by sean1980 on 2010-11-28
Hi everyone,

I need some help with virtual networking in QEMU/KVM.  

Whenever  I provision a VM, it wants me to assign an IP address from a "virtual  network."  I've got a very basic setup at home (1 server, 1 linksys  router, 1 NIC on the server).  

I've tried bridging the virtual  interfaces to the host's interface.  This allows the VM(s) to "get out"  of their network because it is NATed.  However, I am unable to "touch"  the VM(s) from outside of the virtual network because it is NATed.    

How can I configure QEMU/KVM to "pull (DHCP)" from my home router network vice the "virtual network"?

Side  note: I've used Microsoft's Hyper-V to build and network VM(s).  Making  the VM(s) externally accessible was very easy to set up...I could  assign an IP address from the private network of my home router.  I'm  trying to accomplish the same functionality with QEMU/KVM.

Any help will be greatly appreciated!

---

### Post by gdahlm on 2010-11-28
You need to create a bridge interface 

Look for the Configuring Bridged Networking section in the following URL.

[https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

---

### Post by rubylaser on 2010-11-29
This doesn't answer your question, but I don't even bother setting this myself anymore.  I use Proxmox VE [http://pve.proxmox.com/wiki/Main_Page]("http://pve.proxmox.com/wiki/Main_Page").  It supports both KVM and OpenVZ guests and is built on Debian 5.0.  Just my two cents, but it takes care of all the networking issues, and scales from a single server to an enterprise environment.

---

### Post by sean1980 on 2010-11-29
You're my hero!  Thanks, man.

---


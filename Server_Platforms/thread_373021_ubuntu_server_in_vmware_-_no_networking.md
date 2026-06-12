---
title: "ubuntu server in vmware - no networking"
date: 2007-02-28
forum: Server Platforms
---

### Post by nix4me on 2007-02-28
Hi,

I have a windows 2003 machine running vmware workstation.  I installed ubuntu 6.10 server as a virtual machine.  Ubuntu installed with no problems and it boots and runs just fine.  The problem is, it has no networking.  An ifconfig shows only the loopback of 127.0.0.1.  Shouldn't it have detected a dhcp or something?  Other vmware installs I have done worked perfectly with networking, granted they were other os's.

So does anyone have any idea what I can do to get networking up?

Thanks,
nix4me

---

### Post by veloce on 2007-02-28
So your vmware host has some virtual networks already set up?

Does your vm have virtual network cards connected to the virtual networks?

I have a virtual firewall with two virtual network cards, one connects to the "host only" network the other to the "bridged network" (the host's card).  Works perfectly. And virtual networks are much easier to set up on a windows host.

---


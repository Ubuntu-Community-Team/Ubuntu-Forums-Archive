---
title: "Qemu ARM emulator problem on Ubuntu that is a Guest on Virtualbox"
date: 2011-11-28
forum: Virtualisation
---

### Post by _vov_ on 2011-11-28
Hi,

I use Virtualbox to run Ubuntu 11.10 as Guest on Windows 7 Host.
On Ubuntu I am running Qemu ARM system emulator.
The problem is that Qemu fails to start TAP interface when I run it.
(sudo qemu-system-arm -M versatilepb  -nographic -net nic,vlan=0 -net tap,vlan=0,ifname=tap0   -kernel u-boot.versatilepb)

It supposed to work well on 'normal' Ubuntu. 
Is there any reason why Qemu doesn't start correctly on Virtualbox Guest Ubuntu?
Has anybody tried to use the similar setup?

Thanks for any feedback.

---


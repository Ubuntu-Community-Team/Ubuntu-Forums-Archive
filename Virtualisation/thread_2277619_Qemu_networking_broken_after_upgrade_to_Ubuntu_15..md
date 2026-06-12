---
title: "Qemu networking broken after upgrade to Ubuntu 15.04?"
date: 2015-05-10
forum: Virtualisation
---

### Post by eezacque on 2015-05-10
I remember I went through a bit of puzzles to get my qemu guest up and running, so that I could connect to my guest from the host, through setting up a tap interface.
However, after the upgrade to Ubuntu 15.04, this is no longer working. I can get my guest to network in user mode, but that's it, so I suspect something changed in the new qemu 2.2 or elsewhere in Ubuntu networking.

I am starting my guest through:

 qemu-system-x86_64 -enable-kvm [...] -net nic,model=e1000,vlan=0  -net tap,ifname=tap0,vlan=0,script=no

Any help in troubleshooting is appreciated...

---

### Post by eezacque on 2015-05-10
Problem solved. The upgrade had deleted tunctl, used to set up tap interface, and my iptables rules had not been reloaded...

---

### Post by TheFu on 2015-05-11
Thanks for saying the solution. Could you please mark the threat as SOLVED to save others from looking if they want to help and let other people with the same issue know it was SOLVED?

---


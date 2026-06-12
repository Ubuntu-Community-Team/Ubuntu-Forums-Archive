---
title: "Best Virtualisation OS for local management?"
date: 2014-04-23
forum: Virtualisation
---

### Post by Nightcreeper on 2014-04-23
I have decided to to change some things up and use a box (2x quad Xeons w/ 20GB RAM and sas raid) to run 2x servers, one is FreeNAS, the other is going to be a game server. The machine has everything attached like a desktop, and, I would rather deal with it as easily locally as I would remotely. Which OS's for virtualisation support this? Proxmox-VE? ESXi? I am lost and am looking to play with it to figure it out. Thanks.

---

### Post by heiko_s on 2014-04-24
Xen or KVM, aside from the commercial VMware. Both Xen and KVM can be installed via packages from the software repository. Just install Ubuntu 14.04 (it has major improvements for Xen, but probably also for KVM) and then the hypervisor of choice, as well as the openssh server to enable remote access (use keys, not passwords).

You didn't explain how you are going to use the machine? Will it also be your desktop / workstation? Do you plan on gaming on this machine?

When going with virtualisation, make sure your hardware (CPU and motherboard/BIOS) support VT-d (for Intel) and that it's enabled in the BIOS.

---


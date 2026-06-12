---
title: "Virt-Manager VNC Error"
date: 2008-07-07
forum: Virtualisation
---

### Post by e30power on 2008-07-07
Alright, so here is the situation:
Host: 8.04 server, running KVM. Guest is WinXP.
I am trying to connect to the machine via my Linux workstation (a second computer). I finally got around the ssh on different port using virt-manager -c qemu+ssh://rob@server:2224/system Win_XP.
Now I can see the virtual machine under the manager, but it gives me this error when I click on it to connect to the graphical console:

VNC Connection to hypervisor host got refused or disconnected!

Anyone else have this problem? Is this stemming from the fact that my SSH login uses keys with passwords?

---


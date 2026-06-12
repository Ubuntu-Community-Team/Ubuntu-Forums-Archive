---
title: "[SOLVED] Host IP address (VMWare and VirtualBox NAT networking)"
date: 2008-06-10
forum: Virtualisation
---

### Post by quadra on 2008-06-10
I use VMWare (1.0.5 Server) and VirtualBox (1.5.6 OSE) to boot the same virtual machine. I use them alternatingly, NOT simultaneously. NAT networking is enabled and working in both cases.

VMWare uses the address 192.168.17.1 for the host, whereas
VirtualBox uses the address 10.0.2.2 for the host!

Therefore I'd like to change the host IP address either on VMWare, or on VirtualBox (whatever is easier, it doesn't matter), so that the address is the same regardless of the environment.

It looks simple, but I couldn't achieve this! Can somebody help?

---

### Post by fjgaude on 2008-06-10
Funny, it would seem that your router would do the assigning of local addresses. Afterall the router is a NAT device that sees the host and it is the host that requires a local address, eh?

---

### Post by quadra on 2008-06-11
Sorry, I mean the address of the virtual adapter, in the network between the Ubuntu host and the virtual (Win2k) guest. Even if the host has no network connection to the world (so possibly no IP address), the guest should access SMB file shares on the host.
So, when I run the machine under VirtualBox, the SMB shares are accessible but under a different address than they were in VMWare. That requires config changes and causes network timeouts. (Shared folders can't be the solution, as they also work differently in both environments)
Hence I'd like to either change the subnet created by VirtualBox to 192.168.17.x, or the one created by VMWare to 10.0.2.x.

---

### Post by quadra on 2008-06-16
I could solve the problem by accessing the host machine not using its (various) IP addresses, but its (unique) network name.
e.g. \\machinename\share, as configured in Ubuntu's Network Settings

---


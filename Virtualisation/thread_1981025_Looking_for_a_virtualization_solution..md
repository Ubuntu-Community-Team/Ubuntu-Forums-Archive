---
title: "Looking for a virtualization solution."
date: 2012-05-16
forum: Virtualisation
---

### Post by Cheesemill on 2012-05-16
Hi there guys,

I'm looking for a VM solution, but have a couple of specific requirements.

First of all the host machine must be running Ubuntu as I only have the one machine to work with, it has to act as my workstation as well as the VM host, support for the 3.4 kernel would be ideal as I'm testing Quantal although this isn't a deal breaker, I could always revert to Precise.

I must be able to create a virtual network interface on the host machine that can use DHCP to get its network information from a VM that acts as my router.

USB pass-through - It isn't feasible to have a wired network connection to the host machine. Instead I need to use USB pass-through to present my WLAN dongle to the virtual router machine.

Also it would be nice to have either a GUI or a Web UI to manage the VM's as well as support for automatically starting machines in a specific order when the host boots (although I can script this if I have  to).

At work I usually just go straight for ESXi or Proxmox but neither of these will let me use the host machine as a Ubuntu desktop as well. I would have used VMware Server but it's no longer supported. I've tried both the current version and the Technology Preview versions of VMware workstation, and although it could be a solution I really don't want to have to spend any money.

Before you all say VirtualBox I can't create a virtual network interface on the host machine without having to specify a fixed IP address for it in the VirtualBox settings. If there is a way round this then I've found my answer.

Any ideas and input are welcome folks.

---

### Post by rai4shu2 on 2012-05-17
I'm not sure what you're attempting, but have you considered qemu?

[http://wiki.qemu.org/Documentation/Networking](http://wiki.qemu.org/Documentation/Networking)

---

### Post by dcstar on 2012-05-18
> **Cheesemill said:**
> 
........
I've tried both the current version and the Technology Preview versions of VMware workstation, and although it could be a solution I really don't want to have to spend any money.


That's why VMware Player exists.

---


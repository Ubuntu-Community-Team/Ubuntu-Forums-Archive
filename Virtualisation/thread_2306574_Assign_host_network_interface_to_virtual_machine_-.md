---
title: "Assign host network interface to virtual machine - Virt-Manager"
date: 2015-12-16
forum: Virtualisation
---

### Post by Tadaen_Sylvermane on 2015-12-16
I'm looking to upgrade what my server does and use virtualization to do it. For now just looking at a virtualized PfSense router, and maybe a Squid proxy as well. I'd like to pass one of my ethernet interfaces directly to a virtual machine. I don't want the host to have any access to this interface if possible. This passed through interface would be my WAN. I would bridge the other interface to be the LAN and run to a switch.

I have been googling awhile now and it seems there isn't much info on this. Virt-Manager has 4 settings for Network interfaces but I can't find explanations for 2 of them. Bond and Ethernet respectively. I know what Bridge and VLANS is. What is Bond and Ethernet in Virt-manager network interfaces setup and if those aren't useful in this situation then how can I accomplish my goal?

---

### Post by T.J. on 2015-12-17
Virt-manager is for folks starting out, and hides a lot of settings.

It would be far easier if you simply used to the virtio NIC device, but yes, it is possible.  You can bind a PCI device directly to a VM.  This means that Linux drivers for the device have to be blocked first or you can cause the VM to lock up. Without knowing more about your hardware and your Linux install, I can't give you the specifics.

To answer your other questions, I'd need to know what version of virt-manager you are using.  In very non-specific terms, bonding is a process where two NICs card are merged into one. The idea is that the OS sees one interface, and that if one card/connection in the bond fails, it automatically rolls over to the other, with no interruption of service.

---


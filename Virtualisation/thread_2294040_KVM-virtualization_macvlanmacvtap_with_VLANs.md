---
title: "KVM-virtualization: macvlan/macvtap with VLANs"
date: 2015-09-09
forum: Virtualisation
---

### Post by marteng on 2015-09-09
Hello,

I've got two questions:

1. How can I configure a "macvlan" network adapter for the communication between the VMs and the host (ubuntu server 15.04 kvm hypervisor) in "the ubuntu way"?
Is it possible to implement this with some clean entries in /etc/networking/interfaces? It should be save for restarts and distribution upgrades (e.ex. 15.04 -> 15.10)

2. How is the correct usage of VLANs in combination with KVM (Ubuntu server) and virtual machines? My primary network interface is a macvlan created adapter from a bond0 -interface (LACP connection of eth0 and eth1 to a managed switch from cisco, working great).

Do I have to create VLAN network interfaces derived from macvlan0 or bond0?

Example: macvlan0.100 or bond0.100

How to connect the VLANs with the virtual machines? Do I need a separate macvtap network adapter created on the kvm-host for every VLAN in a virtual machine? Or is it possible to create ONE macvtap adapter on the host per virtual machine and divide the VLANs inside the virtual maschine?

Thank you in advance.

Best regards,
Martin

---

### Post by marteng on 2015-09-10
No one?

---


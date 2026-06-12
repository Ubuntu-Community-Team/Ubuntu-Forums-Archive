---
title: "virt-manager, KVM and eth0 briged problem"
date: 2008-04-29
forum: Server Platforms
---

### Post by insulae on 2008-04-29
i want to create a VM with virt-manager and KVM, but when i going to select the connection method i want to select "Shared physical device" because i want to see the VM from my local network, but when i choose this option i see all my networks like this:

wlan0 (Not bridged)
wmaster0 (Not bridged)
eth0 (Not bridged)

and i can't select anything (i am connected via eth0 with static ip).

i googled but i can't find any information about this problem.

if i can't use virt-manager to create a VM with bridged network what i can use? (i don't want Xen or Vmware or another, only KVM+something) is the solution is via manual configuration is ok!.

Grettings
insulae

---

### Post by geertn on 2008-04-29
Not sure about virt-manager, never used it. You need to:

- Make a new bridge
- Make a new Tap interface
- Add your to-be-bridged interface to it
- Add your tap interface to the bridge
- Reassign your IP to the bridge interface since the eth0 interface is in the bridge now
- Start qemu making sure your tap interface maps to eht0- in the VM

There is a howto located here:
[http://wiki.centos.org/HowTos/KVM](http://wiki.centos.org/HowTos/KVM)

---

### Post by insulae on 2008-04-29
(sorry for my english :D )

geertn thanks for the quick response. i resolv my problem installing bridge-utils and then editing /etc/network/interfaces and then i put:

```

auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_stp off
bridge_maxwait 5

```

then i restart the service: networking, kvm and libvirt and then in virt-manager wizard i see the new virtual network br0, with this network i can use the option "Shared physical device".

Grettings
insulae

---


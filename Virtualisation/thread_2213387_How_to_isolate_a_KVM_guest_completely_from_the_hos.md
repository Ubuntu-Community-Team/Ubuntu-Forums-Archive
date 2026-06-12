---
title: "How to isolate a KVM guest completely from the host?"
date: 2014-03-26
forum: Virtualisation
---

### Post by Erik-NA on 2014-03-26
I have just recognised that my KVM dmz-guest connected to an isolated virtual network is always reachable from the KVM host. How can I **completely** isolate the guest from the host?

I have another KVM guest, a virtualised firewall which is bridged to physical interfaces and also to the virtual network.
I want that my KVM host is accessing the dmz-guest through my virtualised firewall. How is that possible?

My next concern is that this feature is affecting my bridges? For example, has the KVM host access to my external network connected to Internet without passing through my virtualised firewall? I have not configured a IP-address for the KVM host on the bridged networks in etc/networking/interfaces.

---

### Post by TheFu on 2014-03-26
No. The host will always be able to shutdown the VM, control PCI passthru, control storage passthru.

I wouldn't trust bridged network connections either. The OS doing the bridging MUST see all the traffic, right?
 Use PCI passthru to the NIC. [http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM](http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM)

---

### Post by Erik-NA on 2014-03-29
Thanks for reply!
The host is doing all the bridging yes. But the host has no IP address on the bridged interfaces where the host shall not have direct access. This works! But yes, the host OS is handling the connectivity on the NIC:s which is something you can questioning.

However, this problem is about the virtual networks. When doing a "route -print" I can confirm that the host have IP-access to these networks. I am not sure if I can set up firewall rules in virsh to block direct access without going through the default gateway. I have to look into that.

The other thing you are mentioning about security and PCI passthrough is interesting. If going that way I have to have a dedicated hardware to run my firewall on and then let my VM:s and the host to have separate NIC:s for each network, the VM:s have dedicated LAN access via PCI passthrough.

---

### Post by Erik-NA on 2014-04-06
Well, I have done some more digging.

I have found that it is possible to remove the route to the isolated networks on the host by using 
```
route del -net <network> netmask <netmask> dev virbr<number>
```

Next step is to make virsh/libvirt **not** to add the route in the hosts routing table when creating the virtual network.

---


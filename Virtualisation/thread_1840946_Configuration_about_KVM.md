---
title: "Configuration about KVM"
date: 2011-09-08
forum: Virtualisation
---

### Post by node2network on 2011-09-08
hi, I installed kvm on Ubuntu10.04, and installed ubuntu11.04 as guest os on kvm.

I enjoy virtualization with kvm. But I have some questions about KVM.

First Question:
The number of virtual cpus is limited because of depending on the kind of host cpu.
I want guest os to have more than 2 cpus. Hwo to confirm this on host? I looked for such commands, but I couldn't find.

Second Question:
When I edit /usr/libvirt/qemu/domain.xml for adding ethernet(eth1).

```

    <interface type='bridge'>
      <mac address='XX:XX:XX:XX:XX:XX'/>
      <source bridge='br0'/>
      <target dev='vnet0'/>
      <model type='virtio'/>
    </interface>
    <interface type='network'>
      <mac address='YY:YY:YY:YY:YY:YY'/>
      <source network='default'/>
      <target dev='vnet1'/>
      <model type='virtio'/>
    </interface>

```What is vnet? Is vnet different from each other?

Third Question:
How to recognize windows os's usb flash memory and cd drive on guest os(ubuntu11.04)?

Could you help me?

---


---
title: "Can't setup VM with bridged networking (using libvirt)"
date: 2012-04-27
forum: Virtualisation
---

### Post by anthony.canucks on 2012-04-27
I am trying to setup a VM with bridged networking and I cannot get it to work.

```
virsh start dc1
error: Failed to start domain dc1
error: Network not found: no network with matching name 'br0'
```

but the bridge is working fine
```
brctl show
bridge name     bridge id               STP enabled     interfaces
br0             8000.001bfca0bbf0       no              eth0
virbr0          8000.000000000000       yes   
```

and I granted the capabilities as shown here [https://help.ubuntu.com/community/KVM/Networking#Bridged_Networking]("https://help.ubuntu.com/community/KVM/Networking#Bridged_Networking")
and gave the capability to libvirt-qemu 

here is the network section of my xml file
```
<interface type='network'>
      <mac address='52:54:00:cf:cf:4d'/>
      <source network='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
```

---

### Post by cmccauley on 2012-05-02
This thread is marked as [Solved] but I can't see any explicit mention of what fixed the original problem ...

---


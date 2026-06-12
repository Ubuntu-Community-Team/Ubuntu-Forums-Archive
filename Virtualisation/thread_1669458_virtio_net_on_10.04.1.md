---
title: "virtio_net on 10.04.1"
date: 2011-01-17
forum: Virtualisation
---

### Post by bradleyd on 2011-01-17
I am lost here.  I used to setup the vm guests via virt-install and adjust guest xml to include interface model type='virtio'.  It appears not to be working after a fresh vanilla install of 10.04.1 and an upgrade.  When the guest boots, it is stuck on the default net driver--which is 100MB--switching to e1000 works, but the net speed is not as good as it is with virtio_net.  Anyone have any knowledge of modules not being in the new kernel?
Thanks for your time.

Here are some info on the host server.


05:00.0 Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)

ii  kvm                                     1:84+dfsg-0ubuntu16+0.12.3+noroms+0ubuntu9.3    dummy transitional pacakge from kvm to qemu-
ii  kvm                                     1:84+dfsg-0ubuntu16+0.12.3+noroms+0ubuntu9.3    dummy transitional pacakge from kvm to qemu-

Here is the interface section in the xml file for the guest

```
    <interface type='bridge'>
      <mac address='52:54:00:3b:78:a6'/>
      <source bridge='br0'/>
      <target dev='vnet0'/>
      <model type='virtio'/>
    </interface>
```

---

### Post by werru on 2011-06-16
+1 the same problem

---


---
title: "is there any possibility to redirect whole HDD to kvm VM ?"
date: 2018-07-31
forum: Virtualisation
---

### Post by alex346 on 2018-07-31
I just have tried 

```
 <disk type='block' device='disk'>      <driver name='qemu' type='raw' cache='none'/>
      <source dev='/dev/sdc'/>
      <target dev='sda' bus='sata'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>

```

I see QEMU ... hdd in Virt Machine.

And it looks great. But I would like to get access to physical hdd under kvm VM - I would like to see name, model, smart data etc.
Also, maybe running dd or testdisk commands will be safe and possible
Is that possible?

---

### Post by TheFu on 2018-07-31
You can exclusively pass a disk controller (and connected disks) into a VM using VT-d capabilities.  People do this for video cards and network adapters too.

The key to all these methods is exclusive access to 1 OS at a time.  The other OS cannot, no-way, no-how, gain access to the device being passed through to the guest VM.

For the things you describe, I keep a $100 PC around. 100x easier than dealing with VMs and passthru.

---

### Post by alex346 on 2018-08-01
> **TheFu said:**
> You can exclusively pass a disk controller (and connected disks) into a VM using VT-d capabilities.  People do this for video cards and network adapters too.

The key to all these methods is exclusive access to 1 OS at a time.  The other OS cannot, no-way, no-how, gain access to the device being passed through to the guest VM.

For the things you describe, I keep a $100 PC for.

Thank you for your answer.

That is exactly what I need :) 

Have you seen any good tutorial for Ubuntu which describes hw passing through VT-d?

regarsd

---


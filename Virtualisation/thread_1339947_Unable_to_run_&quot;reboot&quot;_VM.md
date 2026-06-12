---
title: "Unable to run &quot;reboot&quot; VM"
date: 2009-11-28
forum: Virtualisation
---

### Post by satimis on 2009-11-28
Hi folks,

KVM
host - Debian 5.0
guest, VM - Ubuntu 9.04

On running following command;

@vm0:~$ sudo virsh --connect qemu:///system reboot vm18```

libvir: error : this function is not supported by the hypervisor: virDomainReboot
error: Failed to reboot domain vm18

```

VM is running without problem.  Following commands work without problem;

sudo virsh --connect qemu:///system start vm18
sudo virsh --connect qemu:///system shutdown vm18

Please advise how to fix the problem.  TIA

B.R.
satimis

---

### Post by Yann2 on 2009-11-29
Do you have enabled ACPI for this particular vm?

---

### Post by satimis on 2009-11-29
> **Yann2 said:**
> Do you have enabled ACPI for this particular vm?

Hi Yann2

I ran following command to create the VM```

$ sudo virt-install --connect qemu:///system -n vm13 -r 512 --vcpus=2 -f ~/vm13.qcow2 -s 12 -c ~/mini.iso --vnc --noautoconsole --os-type linux --accelerate --network=bridge:br0 --hvm

```

I ran following command to start the VM```

$ sudo virsh --connect qemu:///system start vm13

```

Which option/flat should be up?  TIA


B.R.
satimis

---


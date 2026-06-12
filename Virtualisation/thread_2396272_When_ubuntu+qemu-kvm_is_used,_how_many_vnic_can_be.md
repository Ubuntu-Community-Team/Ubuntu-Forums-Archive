---
title: "When ubuntu+qemu-kvm is used, how many vnic can be created on a VM?"
date: 2018-07-13
forum: Virtualisation
---

### Post by vne9000 on 2018-07-13
When ubuntu+qemu-kvm is used, how many vnic can be created on a VM?

The VM uses the virtio vnic.

---

### Post by TheFu on 2018-07-13
Libvirt might have limits since they are trying to provide virtual hardware and PCI slots ARE limited.
[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_host_configuration_and_guest_installation_guide/chap-virtualization_host_configuration_and_guest_installation_guide-virtualization_restrictions#sect-chap-Virtualization_Host_Configuration_and_Guest_Installation_Guide-Virtualization_Restrictions-KVM_Restrictions](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_host_configuration_and_guest_installation_guide/chap-virtualization_host_configuration_and_guest_installation_guide-virtualization_restrictions#sect-chap-Virtualization_Host_Configuration_and_Guest_Installation_Guide-Virtualization_Restrictions-KVM_Restrictions)
> This gives users a supported functional maximum of 30 PCI device slots per virtual machine. 
I don't know of any practical limits for the number of virtual NICs a system can have. I vaguely remember 32K being the limit somewhere in the kernel headers. Posts elsewhere claim they did over 1000 themselves and they'd seen reports of over 5,000.

Short of setting them up yourself and seeing if you get enough, I doubt you will find a definitive answer.

libvirt and GUIs used to manage it, might have their own limitations.

---


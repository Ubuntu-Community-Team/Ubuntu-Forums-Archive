---
title: "emulex HBA modules in guest VMs,is it possible?"
date: 2010-02-19
forum: Virtualisation
---

### Post by chakoshi on 2010-02-19
Hi,
I have emulex HBA modules on some hp servers, I use  ubuntu 9.04 host os that automatically detected those devices. I install kvm virtual machines on these hosts and want to know if it is possible to access those HBA on the guests VMs in order to give VM guests access to the SAN storage through the HBA. right know when I install a guest vm (ubuntu as the guest os) and use the lspci command, there is no emulex device found on the guest. any suggestions?

---

### Post by PilotJLR on 2010-02-21
I have not personally done this... and I've only used KVM on Fedora and CentOS... BUT, I can point you to page 187 here:
[http://www.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/5.4/pdf/Virtualization_Guide.pdf](http://www.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/5.4/pdf/Virtualization_Guide.pdf)

You can pass through a PCI device to a single guest using this manual.

Of course, pass through is a 1:1 mapping, so only one guest can use the HBA. If the VM doesn't need hardware level access, it would be better to use LVM or qcow or an image to create a virtual block device instead.

---

### Post by chakoshi on 2010-02-23
> **PilotJLR said:**
> 
You can pass through a PCI device to a single guest using this manual.


let me try this and I'll post the results.thank you for the reply.

---


---
title: "vmware network problem"
date: 2008-01-12
forum: Virtualisation
---

### Post by cypry on 2008-01-12
I have a vmware machine with a modified ubuntu on it(a college project). At home, i had internet conectivity trough nas0 interface(on the real machine, not on the virtual one). Here at college, i'm connected through eth0, and my virtual machine doesn't have conectivity. I already try to remove it's network interface and create a new one, but still no conectivity. Please help.
Thanks.

---

### Post by veloce on 2008-01-16
> **cypry said:**
> I have a vmware machine with a modified ubuntu on it(a college project). At home, i had internet conectivity trough nas0 interface(on the real machine, not on the virtual one). Here at college, i'm connected through eth0, and my virtual machine doesn't have conectivity. I already try to remove it's network interface and create a new one, but still no conectivity. Please help.
Thanks.

Is the host ubuntu or windoze?

You need to edit the virtual network settings for the system, not for the vm.  In windoze there is a gui for this.

On ubuntu you need to run vmware-network-config.pl or similar. (Find it with "locate vmware" in a console.

---


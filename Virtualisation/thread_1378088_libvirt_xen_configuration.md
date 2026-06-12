---
title: "libvirt xen configuration"
date: 2010-01-11
forum: Virtualisation
---

### Post by amarnatha.86 on 2010-01-11
In the ubuntu server 9.04 version 

I have installed xen 3.3 hypervisor and libvirt-bin packages for eucalyptus-nc 

the command ```
xm list 
``` displays the domains running in xen

but when i use ```
virsh list 
``` it says > error::failed to connect to the hypervisor the ```
virsh version
``` gives the using api : qemu 0.6.1

> **[SIZE=4]how to configure virsh to use xen api  instead of qemu[/SIZE]** since i cannot resolve this problem i am unable to start an instance from my cloud controller 

please help me[-o<

---

### Post by cariboo on 2010-01-11
Moved to Virtualization, as you will probably get a better answer here.

---


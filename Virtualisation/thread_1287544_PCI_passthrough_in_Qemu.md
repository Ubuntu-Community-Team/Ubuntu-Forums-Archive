---
title: "PCI passthrough in Qemu"
date: 2009-10-10
forum: Virtualisation
---

### Post by fabien29200 on 2009-10-10
Hello !  I have installed Ubuntu 9.04 in order to virtualize an Hardened Gentoo as a server.  I would like to use the PCI passthrough offered by Qemu. But when I launch qemu, it tells me that it don't know the option "-pcidevice".  I read the man page and I don't see anything about this option. Is it something not already included in Ubuntu ?  Thanks for help.

---

### Post by gaZooGA on 2009-10-27
I don't have an answer for you, and I am trying to do the exact same thing.

I am trying to pass through my digium asterisk card. 

03:01.0 Ethernet controller: Digium, Inc. TDM400P (rev 11)

After unloading the modules on the host I tried manually starting the virtual machine start up just hung.

```
/usr/bin/kvm ...... -pcidevice host=03:01.0
```

I also tried adding this to the xml file

```
<hostdev mode='subsystem' type='pci'>
   <source>
       <address bus="0x03" slot="0x01" function="0x0"/>
   </source>
</hostdev>
```


Jaunty should support this as the site quote:

> PCI passthrough feature of KVM allows to assign PCI devices directly to a given guest (up to 8 guests per PCI with supporting PCI devices), bringing performance to an unprecented level.


I have tried finding the option in virt-manager and no luck there either. 

Anyone had any success yet?

---

### Post by lopb on 2010-08-13
Hi, i have the same problem.
Did u solve it?
and one single question, is possible to made the pci passthrough without hardware support (virtualization hardware support?

---


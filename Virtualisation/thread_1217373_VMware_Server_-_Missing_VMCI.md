---
title: "VMware Server - Missing VMCI"
date: 2009-07-19
forum: Virtualisation
---

### Post by JerommekeH on 2009-07-19
Hello,
I want to set up a virtual machine in VMware server, so I installed VMware server and everything worked until I wanted to start up the machine. I got the message that he couldn't find the "vmci" kernel module. I'm working on an Ubuntu 9.04 and have an AMD Turion 64-bit.
Is there someone who could help me please :confused:

---

### Post by Cheesemill on 2009-07-20
Try running:
```
sudo vmware-config.pl -d
```
This should rebuild the modules for your current kernel.

---


---
title: "How to restore saved virtual machine?"
date: 2010-09-11
forum: Virtualisation
---

### Post by amturnip on 2010-09-11
Once upon a time, I bought Windows 7 and installed it using Virtual Machine Manager.

Later, I reinstalled Ubuntu.  Before doing so, I saved the /etc/libvirt/qemu/xxx.xml file for my virtual machine, and I saved the disk image.

Question:  How do I plug that XML and that image file into the Virtual Machine Manager so I can resume using my virtual machine?

---

### Post by drumbug1 on 2010-09-12
1) Check your xxx.xml file and make sure the <source file='/path/to/xxx.qcow2'/> is correct.
2) Run the command: 'sudo virsh define /etc/libvirt/qemu/xxx.xml'

You should now see your VM in the Virtual Machine Manger :D

---


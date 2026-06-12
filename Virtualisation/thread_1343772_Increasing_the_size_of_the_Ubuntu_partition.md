---
title: "Increasing the size of the Ubuntu partition"
date: 2009-12-02
forum: Virtualisation
---

### Post by Johnsie on 2009-12-02
I had a virtual machine that had 20gb hard disk space allocated to it.

I've now increased that available space so that 30gb is available on the machine. That leaves me with about 10gb of unused space on the VM which I want to add to the existing ext3 partition. How do I go about increasing the size of the partition to use this unused space? I'm doing this in Server Edition so need to do this using the command line. Normally I would use GPARTED. I don't have physical access to the server.

---

### Post by fouadatmeh on 2009-12-02
Hello,

If the extra space is added to the ext3 partition (sda1 for example), then you can simply do something like:

> resize2fs /dev/sda1 30G

** I only did this once in a test enviroment, so please be careful with it.

---

### Post by dcstar on 2009-12-03
> **Johnsie said:**
> I had a virtual machine that had 20gb hard disk space allocated to it.

I've now increased that available space so that 30gb is available on the machine. That leaves me with about 10gb of unused space on the VM which I want to add to the existing ext3 partition. How do I go about increasing the size of the partition to use this unused space? I'm doing this in Server Edition so need to do this using the command line. Normally I would use GPARTED. I don't have physical access to the server.

VM resizing depends on the VM you are using.

---


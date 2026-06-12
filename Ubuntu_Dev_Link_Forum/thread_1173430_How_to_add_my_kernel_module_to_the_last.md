---
title: "How to add my kernel module to the last"
date: 2009-05-29
forum: Ubuntu Dev Link Forum
---

### Post by Linu on 2009-05-29
Hi all,

How do I add my kernel module to the last of kernel module list? I have tried with initramfs tools by adding my kernel driver to module file, in initramfs.conf [module=most] and calling update-initramfs -u -v. update-initramfs including my module in the zip (built) file, but during boot up my driver is loaded very early. Basically I want to load it as last module, but dont want to load from /etc/modules. 

However I could build update-initramfs successfully - following way, But it does not look quite right.

1) update-initramfs -u -v > abc     [with module=most]
2) get all the module from abc in the same order (I tried lsmod to list, it did not work)
3) appended the list to initramfs-tools\module
4) append my module name to initramfs-tools\modules [last]
5) in initramfs.conf, module=list
6) update-initramfs -u -v

This is the only one workaround I coud use. 

Thanks in advance

---


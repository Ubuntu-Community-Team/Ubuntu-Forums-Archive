---
title: "KVM worked in Beta but not in Stable"
date: 2008-04-26
forum: Virtualisation
---

### Post by zadkeo on 2008-04-26
I followed this wiki:

[https://wiki.ubuntu.com/KvmVirtManagerEtc](https://wiki.ubuntu.com/KvmVirtManagerEtc)

and set up a virtual machine in 8.04 64-bit beta. Everything worked without problem.

Now that I did a fresh install of the 8.04 64-bit non-beta release I have followed the exact same steps and can open the Virtual Machine Manager, but when creating a new virtual system, it gets stuck on the "Assigning storage space" step. I can type in the partition to use or the file to use, but when I click on forward it does nothing. The button pushes down, but nothing happens.

Can anyone suggest why this might be and a possible remedy?

Thanks.

---

### Post by zadkeo on 2008-04-26
I installed qemu and was able to set up a qemu vm with virt-manager by unchecking "Enable kernel / hardware acceleration", but for some reason KVM stalls in the same place I mentioned before.

---

### Post by mshu on 2008-04-26
I am experiencing the exact same problem.
Just install my Ubuntu via Wubi. I think a lot of people are experiencing the same problem see [http://ubuntuforums.org/showthread.php?p=4787995](http://ubuntuforums.org/showthread.php?p=4787995) a bug have been place [https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/221746](https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/221746).

Without hardware acceleration, it totally defeat the purpose of KVM

---


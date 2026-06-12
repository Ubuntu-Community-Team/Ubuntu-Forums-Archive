---
title: "Running KVM with e4300, c2d w/o Intel Virtualization Technology?!"
date: 2007-11-09
forum: Virtualisation
---

### Post by ZanexGt on 2007-11-09
So I have an e4300 c2d running at 3150Mhz on a Gigabyte DS3 MB. 

I was following the instructions here [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM) in order to install windows XP inside Ubuntu. 

When I inpu  'sudo modprobe kvm-intel'  into the terminal, I get the following error:

FATAL: Error inserting kvm_intel (/lib/modules/2.6.22-14-generic/kernel/drivers/kvm/kvm-intel.ko): Operation not supported

Now, since my e4300 doesn't support the new Intel virtualization technology, can I even use KVM? If I can't use KVM should I try VMWARE or something else? 

Thanks for the help!

---


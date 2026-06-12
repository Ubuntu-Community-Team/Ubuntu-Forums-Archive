---
title: "KVM guest image corruption solution?"
date: 2014-05-19
forum: Virtualisation
---

### Post by ridah2 on 2014-05-19
hi all,


I recently setup qemu/kvm guests in ubuntu 12  x86_64. Now my kvm guests were working fine until suddenly all of the got corrupted. These all were qcow2 images. I searched quite a bit and this is what i found

[https://groups.google.com/forum/#!msg/s2e-dev/mH3x0yO6B_Q/XDNmyKFqHeEJ](https://groups.google.com/forum/#!msg/s2e-dev/mH3x0yO6B_Q/XDNmyKFqHeEJ)

Either i can take a backup of the images or i can shift to S2E format (i found very little material on this format...really donot think it is a good idea for me).


Could someone provide an alternate and reliable solution? Also if i use raw image instead, would my problem go away?

Any help would be appreciated.

---

### Post by TheFu on 2014-05-21
I wouldn't deploy a new VM host with 12.04 today. I'd use the latest LTS release which is 14.04. The KVM support is much, much, much better in 14.04.

I don't use QCOW, so don't know anything about corruption. There are many considerations when selecting which method of storage to be used.  I use raw always, but for performance reasons, I'd only consider using partition passthru with LVM.  QCOW2 may have improved with sparse allocations, but I've never used them and in 2012, QCOW was 50% slower than raw.

Oh .. almost forgot.  I've never seen corruption in VM storage that wasn't a failing HDD.  OTOH, I use very simple storage models for production systems.  The K-I-S-S principal is a core value here.

---

### Post by Doug S on 2014-05-22
> **TheFu said:**
> I wouldn't deploy a new VM host with 12.04 today. I'd use the latest LTS release which is 14.04. The KVM support is much, much, much better in 14.04.+1, I couldn't agree more.

---


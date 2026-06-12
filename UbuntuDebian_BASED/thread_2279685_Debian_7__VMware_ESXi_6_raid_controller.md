---
title: "Debian 7 / VMware ESXi 6 raid controller"
date: 2015-05-25
forum: Ubuntu/Debian BASED
---

### Post by Drenriza on 2015-05-25
Hi all

I am currently researching a home build, for a home network storage using VMware ESXi 6 and Debian 7.
My question is in this regard if anyone has some good experiences with a decent hardware raid controller that function with the above.

My last purchase was a Highpoint Rocketraid 272x which was a damn disastor. I cant get it to work with **_anything_**.
So this time i would like to end more in the right direction, thus this thread asking for advice / experience.

I am looking for a raid controller for raid 5 (4 disks + 1 spare), wake on lan and good quality.

Hope someone can point me in the right direction.

Thanks on advance
Kind regards

---

### Post by TheFu on 2015-05-26
You'll need to check the HCL for the VMware virtualization product you are purchasing. 
Also - don't forget to budget for backup software too. There are no effective free backup tools for ESXi.  Veeam and Trilead ... 

Any chance you are willing to use KVM instead? It won't help with cheap RAID cards, but it does support many, many, many more hardware setups and there's the entire F/LOSS ecosystem for backup tools (including LVM+snapshots).

---

### Post by Drenriza on 2015-05-27
> **TheFu said:**
> You'll need to check the HCL for the VMware virtualization product you are purchasing. 
Also - don't forget to budget for backup software too. There are no effective free backup tools for ESXi.  Veeam and Trilead ... 

Any chance you are willing to use KVM instead? It won't help with cheap RAID cards, but it does support many, many, many more hardware setups and there's the entire F/LOSS ecosystem for backup tools (including LVM+snapshots).

Thank you very much for the reply and suggestion.

Does kvm have a compatibility list for raid controllers? I cant seem to find one through google, their website of faq.

---

### Post by howefield on 2015-05-27
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by TheFu on 2015-05-27
> **Drenriza said:**
> Thank you very much for the reply and suggestion.

Does kvm have a compatibility list for raid controllers? I cant seem to find one through google, their website of faq.

KVM is part of the Linux kernel. If a RAID controller is compatible with the kernel, then it works with KVM.  If there are issues with a specific RAID controller in Linux, then there will issues with that controller on a system running KVM too.

There are good reasons to use ESXi and there are good reasons to use KVM. Mostly these are around gaining skills that will pay well for a job. On a technology level, unless you are running 50+ physical VM host machines, I can't think of any reason to prefer ESXi over KVM - plus in the ESXi ecosystem, everything has a cost - everything is an add-on option needing budget. If you are mostly Windows, have lots of budget, plan to run 50+ physical hosts, don't want self-service, then VMware ESXi is the tool for you.  

For KVM, there are excellent free answers for almost everything. Plus if you want to be a cloud hosting/VPS provider, there is openstack - based on KVM. Got 20,000 physical VM hosts - openstack is for you. Of course, it is very complicated and hardly worth the trouble for less than 50 physical VM hosts.  For less than that, and if a pretty web interfaces is desired, check out proxmox.  For home use, with just a few VMs - perhaps 30 and only 5 or fewer VM hosts, KVM + virt-manager easily suffice.

BTW, I have a PROMISE RAID controller - it never worked as RAID thanks to poor support for current Linux kernels. If I needed HW RAID, I'd look to an LSI RAID controller and carefully verify linux support.  When shipped to me, the promise RAID card supported a 2 yr old Linux kernel and they had ZERO plans to provide any support for newer kernels. Just sayin'.  Linux SW-RAID is slower, but extremely flexible and not tied directly to any hardware. I've moved mdadm-RAID disks across 3 very different Linux systems and many different versions of the OS without any issues. It sorta just works.  If a MB or RAID card fails, we better hope for perfect backups, cause that data is effective gone. I've seen it.

RAID is never a replacement for backups, as we all know.

Oh ... google found this: [https://www.linuxquestions.org/hcl/](https://www.linuxquestions.org/hcl/) Linux HCL. Sadly, the LSI RAID section doesn't seem to be current. I didn't search too hard. At work, we generally get the RAID card(s) with the server purchase and the vendor knows which Linux we are running. At home, I avoid HW-RAID like the plague. Don't need the hassles or that level of performance.

---


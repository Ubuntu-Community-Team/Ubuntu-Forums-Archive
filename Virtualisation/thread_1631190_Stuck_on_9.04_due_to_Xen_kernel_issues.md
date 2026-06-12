---
title: "Stuck on 9.04 due to Xen kernel issues?"
date: 2010-11-26
forum: Virtualisation
---

### Post by PC_Nerd on 2010-11-26
Hiya,

I'm currently running 9.04 on a virtual server, which I beleive is running on xen platform.

Admitedly - I havent attempted to upgrade the server to a new release in quite a few months. However when I did, I had issues upgrading/booting the new version.  When discussing this with tech support I was told it was somethign to do with the kernel used, because xen runs a non-standard kernel ( or something?)

Assuming that this non-standard kernel thing is correct I have two questions:
1) Is there any way to upgrade ubuntu version with this non-standard kernel, preferably avoiding having to recompile my own kernel etc because I know little about the kernel (as you've probably gathered).
2) If they are "upgrading the kernel... to patch a vulnerability".. is this likely to bring the kernel into line with a supported ubuntu one (or, the other way round.. bah.. "ie.. make it work")?

I've looked around but most posts/discussions seem to be on installing xen on ubuntu, not the other way around.

Thanks for any help on this.  I would really like to start being able to use the 10.10 packages!

Cheers,
PC_Nerd

---

### Post by agent8131 on 2010-11-27
If I understand correctly you should be fine.  I believe all versions of Ubuntu since 8.04 will work as a Xen guest (DomU) operating system.  When people talk about Ubuntu not working for Xen they mean on the host system (Dom0).  However, being a virtual system it is always wise to perform a snapshot backup of your system before any significant upgrade.

---

### Post by PC_Nerd on 2011-01-07
Hi,

After a bit of a lazy/extended christmas break I'm back to this problem... and I've got the following from tech support:

"Also, we only support up to 9.4 due to Kernel requirements for anything higher then 9.4, 10.X cannot run due to instabilities within the requirements for the LTS 10.0 Kernel, this could potentially effect other clients on the host node, which is why I have advised our Technicians not to try deploy it."

I'm starting from scratch after a full back up - so at this stage I'm on a clean install/image of 9.04 (provided from the hypervm control panel).

As per this tech support response, is there any chance of effecting "other clients on the host node" if I upgrade fo a 10.xx install by a dist-upgrade?

Thanks,
PC_Nerd

EDIT:
This was posted on their customer support forum... seems relevant.
"The reason for that is that from release version 9.10 (not 9.04) upwards, Ubuntu has required a newer Kernel version to be installed.
Each VPS on our Linux VPS Solution uses the Kernel of the host node. We run Centos 5 on our host node's. We run the latest stable centos kernel on them, however even the latest stable kernel of Centos is not supported by Ubuntu 9.10 or 10.04 or 10.10."

---

### Post by bodhi.zazen on 2011-01-07
Personally I would either run supported hosts and guests or switch to an alternate technology (kvm, vbox, vmware, openvz, or LXC).

---

### Post by PC_Nerd on 2011-01-07
The trouble is that I cant choose the host/client technology, since I'm just given access to a client node. And given that I know relatively little regarding kernel versions and virtualisation, I don't know how far I can "push" my dist-upgrades.

---

### Post by bodhi.zazen on 2011-01-07
> **PC_Nerd said:**
> The trouble is that I cant choose the host/client technology, since I'm just given access to a client node. And given that I know relatively little regarding kernel versions and virtualisation, I don't know how far I can "push" my dist-upgrades.

You can push them till they break. Just do so on a test installation.

I know it is not what you want to hear, but, ...

IMHO Xen was nice, but it is now depreciated and I would spend more time looking at migrating to a new technology then pushing and testing the limits of Xen. It is what it is.

If you have questions on Xen, use the Xen mailing list you will get much better information there as my guess is there are minimal Xen users here (some, but very few).

---

### Post by PC_Nerd on 2011-01-07
Well I tried to get to 9.10 and it exploded spectacularly - and refused to mount drives, could barely do anythign when dropped in as root...  so I think I'll just have to stick with a release that is 18 months old over the 10.04 LTS :'(

Thanks.

---

### Post by bodhi.zazen on 2011-01-07
> **PC_Nerd said:**
> Well I tried to get to 9.10 and it exploded spectacularly - and refused to mount drives, could barely do anythign when dropped in as root...  so I think I'll just have to stick with a release that is 18 months old over the 10.04 LTS :'(

Thanks.

That would be my advice, do not upgrade, and spend your effort on considering an alternate (I think even RHEL is dropping Xen, so good luck to you ... ).

---


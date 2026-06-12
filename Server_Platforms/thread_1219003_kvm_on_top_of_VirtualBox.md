---
title: "kvm on top of VirtualBox"
date: 2009-07-21
forum: Server Platforms
---

### Post by dragos2 on 2009-07-21
I installed an ubuntu Server 8.0464 bit in VirtualBox 3.0.2, then I instaled kvm properly.
The problem is that sudo kvm says that hardware acceleration is disabled, probably
there is a VirtualBox trick.

Anyone tryed kvm inside Ubuntu running on top of VirtualBox ?

---

### Post by bacil on 2009-07-21
i am using qemu inside vbox machine no problem at all. have you got virtualisation enabled in vbox for your virtual machine ? it is in advanced options for VM

---

### Post by dragos2 on 2009-07-21
> **bacil said:**
> i am using qemu inside vbox machine no problem at all. have you got virtualisation enabled in vbox for your virtual machine ? it is in advanced options for VM

Yes, it was enabled at the installation time.

Any other ideas ?

---

### Post by bacil on 2009-07-21
kvm is using qemu as base for its cpu emulation did you try to run qemu machine ? just to check where problem lay

i know for example that ESX is checking instruction set on cpu to determine if it is virutalised itself and if so it refuses to boot (it installs without error).

so i just wonder if there is similar check in kvm

---

### Post by vpadro on 2009-07-22
Are you talking about nested virtualisation?
AFAIK this only works using the kvm-84or newer version and an AMD processor with svm extensions.
[http://www.linux-kvm.com/content/kvm-nested-virtualization-works]("http://www.linux-kvm.com/content/kvm-nested-virtualization-works")

---

### Post by windependence on 2009-07-23
I wouldn't suggest doing this with ANY virtualization solution. You are adding much more complexity than you need and you are just asking for trouble in the virtualization translation layers.

Of course this is just MHO.

-Tim

---

### Post by dragos2 on 2009-07-23
> **vpadro said:**
> Are you talking about nested virtualisation?
AFAIK this only works using the kvm-84or newer version and an AMD processor with svm extensions.
[http://www.linux-kvm.com/content/kvm-nested-virtualization-works](http://www.linux-kvm.com/content/kvm-nested-virtualization-works)

Yes. Thanks for clarification.

---

### Post by dragos2 on 2009-07-23
> **windependence said:**
> I wouldn't suggest doing this with ANY virtualization solution. You are adding much more complexity than you need and you are just asking for trouble in the virtualization translation layers.

Of course this is just MHO.

-Tim

You are right. Someone posted yesterday about FreeXenServer from Citrix so I installed
the hypervisor on a test machine and I must say that I am impressed - a very good solution.

I think I will go with FreeXenServer for serious virtualization now.

---

### Post by windependence on 2009-07-23
Let me know how you make out with that. I don't like Citrix at all so I try to shy away from that. Also, with Vmware I can use my physical CDROM either locally or remotely. Last I tried Xen, you could not do that, you had to load the OS from an ISO.

-Tim

---

### Post by dragos2 on 2009-07-23
> **windependence said:**
> Let me know how you make out with that. I don't like Citrix at all so I try to shy away from that. Also, with Vmware I can use my physical CDROM either locally or remotely. Last I tried Xen, you could not do that, you had to load the OS from an ISO.

-Tim

Yes, this is still annoying. I hope to test ESXi in the future too, until then I can't say which
one is better.

As overall features the FreeXenServer is richer than ESXi except the above mentioned.

I don't like Citrix either but they surely did a good if not great free hypervisor.

I will let you know of my impression of it.

---


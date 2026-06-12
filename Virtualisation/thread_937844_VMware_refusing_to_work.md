---
title: "VMware refusing to work"
date: 2008-10-04
forum: Virtualisation
---

### Post by Vadi on 2008-10-04
I'm trying out VMware, but it's refusing to work for me. It gives the following error:

> The virtualization capability of your processor is already in use. Disable any other running hypervisors before running VMware Player.

I do have VirtualBox installed, but I set it to use software virtualization, not hardware. There's also the kvm-intel module which I have to unload each time after a reboot though (even after I uninstalled kvm, the module stayed).

After that error, vmware gives these ones:

> Failed to initialize monitor device.

Error while powering on: Cannot find a valid peer process to connect to.



Can anyone help out?

---

### Post by fjgaude on 2008-10-04
It would seem you can't have two hypervisors installed at the same time. If you like VBox leave VMware alone. If not, uninstall VBox and then try to install VMware. Also find out what it takes to completely remove all elements of KVM.

---

### Post by jimkeeley on 2009-03-01
I'm having the exact same problem - I haven't installed VirtualBox but also haven't uninstalled any of the std programs that come with Ubuntu.

Any one got any thoughts?

Thanks,

Jim

---

### Post by bodhi.zazen on 2009-03-01
This is an old thread, but you can use both VirtualBox and VMware without a problem.

My guess is that the conflict is with KVM. The KVM hypervisor is enabled in your BIOS, not by installing the KVM modules.

So , yes you can remove the kvm package, but what you really need to do, if you want to use vmware, is go into your bios and disable KVM.

The trick here is that every BIOS is different, and of course they do not lable the hypervisor "KVM". In my bios, for example, it we in the security tab of all places.

So you will have to re-boot and look very carefully through your BIOS and disable the hardware virtulization useb by KVM.

---


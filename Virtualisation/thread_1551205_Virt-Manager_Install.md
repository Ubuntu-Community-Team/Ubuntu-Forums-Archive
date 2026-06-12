---
title: "Virt-Manager Install"
date: 2010-08-12
forum: Virtualisation
---

### Post by Nemasis on 2010-08-12
I am experimenting with all the various virtualization packages available and I am working with KVM now. I have done a ton of reading, and KVM seems the way to go. I use Hyper-V(ile) in my day job and absolutely hate it; also ESXi once upon a time. I have installed Virt-Manager on a Lucid desktop through the Software Center. I want to use Virt-Manager to manage only remote servers, however it looks to have installed qemu-kvm, libvirt and some other bits  for virtualization as well as Virt-Manager. Are these necessary to run Virt-Manager to connect to remote hosts? When I open Virt-Manager I do see the connection to the local libvirtd. Is there a way to install only Virt-Manager and no the virtualization bits? I assume libvirt is required as Virt-Manager will import it?

btw I have been using linux for only about 6 months but getting quite comfortable with it.

Thanks in Advance
Nemasis

---

### Post by dzponce11 on 2012-04-19
Not really. You can't just install one component. Your best bet would probably be VirtualBox.

---


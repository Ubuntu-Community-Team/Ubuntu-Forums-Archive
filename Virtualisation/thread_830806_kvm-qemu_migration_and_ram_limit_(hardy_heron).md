---
title: "kvm-qemu migration and ram limit (hardy heron)"
date: 2008-06-16
forum: Virtualisation
---

### Post by funkgui on 2008-06-16
Hi to all,

I've just configured few virtual machine using kvm-qemu system, it seems so good...

but I've noticed 2 things:

[LIST=1]
[*]there's a 2gb ram limit for domain... is it possible???
[*]I didn't found how to make a live migration (actually I do it with ssh copy of xml conf file and filedisk)
[/LIST]

Hi to everyone.
mARCO

I installed ubuntu 64bit and the 2gb limit go away!

---

### Post by NaughtyusMaximus on 2008-08-29
Did you ever find a solution to how to do a live migration?  I'm trying to set this up now, and the only guide I can find doesn't seem to apply to Ubuntu as the host.

---

### Post by redbrain on 2008-09-18
i have some tutorials written up on my blog on kvm/qemu.

Migration is confusing but it works! and the ram problem make sure you have the prarvirtulised guest support drivers installed on your host system for more memory for each virtual machine:
 [http://redbrain.co.uk]("http://redbrain.co.uk")

Paravirt Guest KVM code is: Processor Type and Features -> Paravirtulised guest support -> kvm para. clock + kvm guest support.

---

### Post by NaughtyusMaximus on 2008-09-18
Very cool!  I'll take a look at your guide asap!

---


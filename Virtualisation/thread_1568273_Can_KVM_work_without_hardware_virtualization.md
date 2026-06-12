---
title: "Can KVM work without hardware virtualization?"
date: 2010-09-05
forum: Virtualisation
---

### Post by bitteralmond on 2010-09-05
I'm using Ubuntu 10.04 Server, and I want to have a virtual Ubuntu server as a guest. When I googled KVM system requirements, it looks like it requires virtualization hardware, which I don't think I have. I tried to install xen, but it has a broken xen-tools dependency.

Is there any way I can use virtualization on Ubuntu 10.04 Server, or is it impossible because my box lacks the hardware?

---

### Post by Dedoimedo on 2010-09-05
You can use virtualization of all kinds, you just won't benefit from some of the extended features that modern chips offer. You can try other products as well, which can run both with VT enabled/disabled.
Dedoimedo

---

### Post by bitteralmond on 2010-09-05
KVM requires libvirt, and the [Ubuntu Server Guide]("http://doc.ubuntu.com/ubuntu/serverguide/C/libvirt.html") says:
> Before getting started with **libvirt** it is best to make sure your hardware supports the necessary      virtualization extensions for **KVM**.My hardware does not support the "necessary virtualization extensions for KVM", so I cannot use KVM, correct? Xen is no longer compatible or supported, so which free, non-graphical virtualization software can I use that is compatible with Ubuntu 10.04 Server? VirtualBox installs x11-common (and probably X).

Thank you.

---

### Post by HermanAB on 2010-09-06
Correct.

If your have a sub-par CPU, then you have to use VMware or Virtualbox.

---

### Post by spidee on 2011-09-23
KVM requires hardware support. Xen can run guests without hardware support iff  the guest is paravirtualized.

---

### Post by jerrrys on 2011-09-23
anyone wanting to know if your computer can run kvm, open a terminal and ask it:

kvm-ok

---

### Post by guy-rouillier on 2012-12-04
root@xxxxxxxx:~# kvm-ok
-bash: kvm-ok: command not found

---


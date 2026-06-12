---
title: "can Xen be install before OS?"
date: 2008-03-31
forum: Virtualisation
---

### Post by Rick Z on 2008-03-31
Does any one know if a Virtual Software (Xen, Vmware, or any other) can be install before any OS like Ubuntu?

---

### Post by piousp on 2008-03-31
Do you mean a bare-metal installation?
I guess VMWare have a ESX server or something like that, that it can.
Not sure about xen

---

### Post by mrsteveman1 on 2008-03-31
As far as i know Xen relies on the Linux kernel to function on bare hardware, so in effect you have to have an OS installed first.

Even VMware ESX uses the linux kernel, though they seem to have gone out of their way to make it look like they aren't relying on it for anything significant.

---

### Post by Rick Z on 2008-03-31
I understand now.  Thank you for the clarification.  I am wondering if the next release 8.04 will support the bare-metal installation.

R

---

### Post by fjgaude on 2008-03-31
> **Rick Z said:**
> I understand now.  Thank you for the clarification.  I am wondering if the next release 8.04 will support the bare-metal installation.

R

Well, from what I can see in looking at KVM, the default for Hardy, it certainly requires an OS install to work.

---

### Post by Rick Z on 2008-04-01
Does KVM required GUI to be install?  It seems like the GUI slows down the system.  

The GUI doesn't really get loaded unless we login to it right?  If this is the case, I will just remote login using ssh or web interface administration.  I am also wondering if the VM (under kvm, vmware, and etc) needs to power up first before guest can login remotely.

---


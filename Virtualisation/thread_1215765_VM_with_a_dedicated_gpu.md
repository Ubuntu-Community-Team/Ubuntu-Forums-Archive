---
title: "VM with a dedicated gpu?"
date: 2009-07-17
forum: Virtualisation
---

### Post by keenish27 on 2009-07-17
I have been searching all over the web and haven't found anything worth noting and was just wondering if anyone here has heard of something like this.

I have 2 nvidia geforce 9800 gt's in my box.  I normally run windows with sli to do gaming.  I would like to switch full time to ubuntu but the gaming is holding me back.  Does anyone know if there is a vm out there such as virtual box or vmware that can take full advantage of one of my gpus.  I mean is there one that I can give direct access to my second gpu so that gaming would be possible in the vm?

Thanks.

---

### Post by bodhi.zazen on 2009-07-17
No this is not possible, virtualilzation does not directly use your hardware.

VMWare workstation (non-free) and VirtualBox (free) are your best options.

---

### Post by Wiebelhaus on 2009-07-17
> **bodhi.zazen said:**
> No this is not possible, virtualilzation does not directly use your hardware.

VMWare workstation (non-free) and VirtualBox (free) are your best options.

As suggested , [Virtual Box]("http://www.virtualbox.org/") has made great strides in regards to 3D performance with the latest version (3.+) It's hands down the best VM software for people like us , for a corporate level IT management application someone may want to look into VMware , but I'd probably still settle on Virtual box , it's just so incredibly good.

---

### Post by juancarlospaco on 2009-07-17
KVM is working on PCI Bus pass trought, 
*so a card connected to pci-xpress is seen "as is" on the VM*

---

### Post by keenish27 on 2009-07-21
> **juancarlospaco said:**
> KVM is working on PCI Bus pass trought, 
*so a card connected to pci-xpress is seen "as is" on the VM*

That would be nice.  As I said, I have two cards and I really don't see that big of a performance gain from sli.  I would be totally happy dedicating one of my cards to a vm.  It would solve like 99% of my linux problems.

---

### Post by juancarlospaco on 2009-07-21
Yes, its designed for speciallized hardware on servers, 
in example Digium Cards on Asterisk boxes, 
but gamers and designers can take some advantage from this incoming feature.
And Ubuntu support KVM, so time to time...

---


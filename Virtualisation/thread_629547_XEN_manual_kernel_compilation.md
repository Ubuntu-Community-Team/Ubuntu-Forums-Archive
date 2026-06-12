---
title: "XEN manual kernel compilation"
date: 2007-12-02
forum: Virtualisation
---

### Post by thund3rman on 2007-12-02
Well... My line of work is usually related to Oracle, as my everyday work is done on Oracle Database and related products...

As all of you must have heard, Oracle released Oracle VM, a virtualization appliance based on XEN... Being a virtualization enthusiast, that caught my attention... I've been mostly using Qemu, KVM, VMWare and Virtual Box... But now I wanted to try XEN...

Like any kernel compilation and costumization junkie, I started immediatelly looking for patches to apply to the latest source... I run a custom made 2.6.23.9, patched with apparmor (to follow ubuntu lines), latest mac80211 (10.0.2) and latest iwlwifi (1.2.22)... Also, I'm using fglrx 7.11 (or is it 8.43.3 :p).

But I couldn't find one!!! :( According to official information from xensource, the pathes that exist are for 2.6.18 kernel... (rather old, if you consider that KVM has entered mainline in 2.6.20...)

So, how did the ubuntu guys made available a 2.6.22 compiled for xen (dom0 plus domU)? Where can I get such patches? Does anyone know?

---


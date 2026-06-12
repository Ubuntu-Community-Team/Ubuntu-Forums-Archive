---
title: "Need native performance in virtual machine.. Maybe install lightweight host?"
date: 2007-12-20
forum: Virtualisation
---

### Post by systemintheglitch on 2007-12-20
So sometimes an OS will suck at having drivers for your computer, but another computer may rule at having drivers for your computer.. How can I use that to make a very decent virtual machine of the one that sucks at having drivers?

Suppose I want to install os X which doesn't work right natively, but in a VM it rocks! How do I make this appear native in performance and boot time?

Can I install a very very lightweight host that has minimally just the GTK to run vmware? Which distro should I pick? Which distro has very lightweight load time/performance but good driver support? 

Am I going about this the right way?

Does increasing ram really help too?

---

### Post by Delvien on 2007-12-20
Its not gtk, but try Fluxbox.

a lightweight host does help. but its still virtualized, theres only so fast it can go.

---

### Post by bodhi.zazen on 2007-12-20
Well, consider install a server host and try either Xen or OpenVZ

VMWare / Qemu / Vbox will give you more of a performance hit then Xen or OpenVZ , no matter how light the host or window manager.

---

### Post by fjgaude on 2007-12-20
A technical article I read sometime back stated that Xen ran apps at about 90% of native, which VMware and others like it took a 50% hit. Xen is a revolution when it comes to virtualization, but somewhat behind in getting to be user friendly. It's coming though.

---


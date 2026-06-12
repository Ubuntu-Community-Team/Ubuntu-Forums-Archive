---
title: "Virtualizing on Ubuntu Server"
date: 2010-07-24
forum: Server Platforms
---

### Post by ankurTheKing on 2010-07-24
Hi,
There are lots of technologies which are used for virtuaizing such as OpenVZ, Xen, VMWare, KVM.

I tried all except KVM. Is there any web gui control pane which can be used for KVM virtualization ?
Like, HyperVM is used for openvz and xen, vmware have their own control panel web gui

---

### Post by Vegan on 2010-07-24
You missed a few. Microsoft has one now for Windows Server.

---

### Post by ankurTheKing on 2010-07-24
I dont consider microsoft in Linux family

---

### Post by ankurTheKing on 2010-07-26
Any help would be appreciated.

---

### Post by Pioden on 2010-07-27
> **ankurTheKing said:**
> Hi,
Is there any web gui control pane which can be used for KVM virtualization ?


Not heard of a web gui for KVM but IIRC VirtManager can control KVM virtualisation over a network. Great for LAN's but I'd been careful about using it over an insecure connection. A VPN and VirtManager would probably work fine I guess.

HTH

Huw

---

### Post by CharlesA on 2010-07-27
I believe there is a web UI for VirtualBox:

[http://code.google.com/p/phpvirtualbox/](http://code.google.com/p/phpvirtualbox/)

I've not heard of a webUI for KVM tho.

---

### Post by Sporkman on 2010-07-27
One of these guys might have a web UI:

[http://www.linux-kvm.org/page/Management_Tools](http://www.linux-kvm.org/page/Management_Tools)

EDIT: Missed the "UI Type" column. :)  There are several web UIs listed.

---


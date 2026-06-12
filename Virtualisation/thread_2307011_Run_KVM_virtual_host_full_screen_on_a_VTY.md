---
title: "Run KVM virtual host full screen on a VTY?"
date: 2015-12-21
forum: Virtualisation
---

### Post by Steve_Freegard on 2015-12-21
Hi,

Is it possible to run the console of a KVM virtualized host on a virtual console?

e.g. X runs on /dev/tty7 by default and I'd like to be able to run Win10 on /dev/tty8, so I can swap between Ubuntu and Windows 10 quickly.

Kind regards,
Steve.

---

### Post by MAFoElffen on 2015-12-22
> **Steve_Freegard said:**
> Hi,

Is it possible to run the console of a KVM virtualized host on a virtual console?

e.g. X runs on /dev/tty7 by default and I'd like to be able to run Win10 on /dev/tty8, so I can swap between Ubuntu and Windows 10 quickly.

Kind regards,
Steve.
Ah... Well??? ***Never***.

A bit on "Symantics..." 

A KVM "Host" would would be the server that is running your KVM hypervisor. You can hot-key over to any tty session and still be interactive to that host.

Guests run in virtuals in the hypervisor. With KVM, you connect to that virtual session either ssh or vnc. If I am running a GUI guest, I tend to use virt-manager or sometimes a remote desktop from another PC... Not from the server that I am running KVM on.

---


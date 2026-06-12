---
title: "I'm trying to run a custom kernel based on hardy's linux-source package as guest OS i"
date: 2008-05-19
forum: Server Platforms
---

### Post by gnuthor on 2008-05-19
I'm trying to run a custom kernel based on hardy's linux-source package as guest OS in VirtualBox 1.5.6 (standard ubuntu hardy host, ubuntu-server hardy guest), to try out some kernel patches.



As final result, I'd like to run ubuntu-server with a module-less kernel

(module loading support disabled), which shouldn't usually require an initial ram disk.



But when I boot a kernel without an initrd, the system hangs at /etc/init.d/keyboard-setup and after a while produces "out of memory" errors for process udevtrigger.



Seems that udevd isn't started before console setup when you don't run an initrd-kernel, and that keyboard-setup somehow requires udev to be running.



Has anyone managed to boot initrd-less Kernel with Hardy? How? ;-)



   Thanks

---

### Post by windependence on 2008-05-19
Have you tried VMware Server? It's free.

-Tim

---

### Post by gnuthor on 2008-05-19
> **windependence said:**
> Have you tried VMware Server? It's free.

Nope, but I suspect that the problem here really isn't caused by VirtualBox (I've just mentioned that for completeness' sake) but rather Ubuntu refusing to start without an initrd kernel.

Also VBox is included in Ubuntu and is OSS.

But I could certainly try on some other machine, maybe it's a VBox problem after all.

---


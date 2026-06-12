---
title: "xen-desktop vs xen-server?"
date: 2009-07-16
forum: Virtualisation
---

### Post by champi0n on 2009-07-16
I can't find anywhere that has an explanation of either.

I have ubuntu installed and now i want to install XEN.

But if i install xen-server (which I think is what I want), do i lose my current desktop as the dom0 and it just becomes a terminal? (I want to run a bunch of virtual machines to do a bunch of different server workloads but still have access to my current desktop to do various development etc).

If i install xen-desktop, is it more like vmware player or virtualbox?

---

### Post by lukeiamyourfather on 2009-07-16
What do you want to do with it? If you are going to consolidate servers then Xen is probably the way to go. If you're a desktop user and want to run another Linux or Windows virtual machine your best bet is VirtualBox. Cheers!

---

### Post by champi0n on 2009-07-16
I want to install XEN but I can't figure out the difference between the desktop and server variants on the ubuntu install.

---

### Post by lukeiamyourfather on 2009-07-16
> **champi0n said:**
> I want to install XEN but I can't figure out the difference between the desktop and server variants on the ubuntu install.

Only difference is one comes with a GUI for setting up virtual machines and one doesn't, the desktop version is the one that comes with the GUI (xenman).

Like I already said if you aren't consolidating servers you probably won't like Xen. Generally speaking Xen is not made for end users, for example it won't work with binary video drivers since Xen requires a modified kernel. Or many other drivers for that matter. Performance and overhead wise VirtualBox 3.0.0 (just released) is very competitive with Xen, up to 32 processors and 16GB for the guest and hardware virtualization of the video card for some guests.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
[http://www.virtualbox.org/wiki/Screenshots](http://www.virtualbox.org/wiki/Screenshots)

As an end user I think VirtualBox is much better suited than Xen for desktop users, give it a try if you haven't already. Cheers!

---

### Post by juancarlospaco on 2009-07-17
[if you want to use the lastest version of Convirt]("http://www.tecnicoslinux.com.ar/livecd/auto-repo-cnvrt_1_all.deb") *(ex-xenman)*

xen-desktop=xen for desktop kernel
xen-server=xen for server kernel

:)

---


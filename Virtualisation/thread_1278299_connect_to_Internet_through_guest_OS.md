---
title: "connect to Internet through guest OS"
date: 2009-09-29
forum: Virtualisation
---

### Post by pytheas22 on 2009-09-29
Imagine this scenario: I have a guest operating system in VirtualBox running Windows XP on an Ubuntu host.  I have a USB wireless card that gets passed directly to the guest operating system, and works there using the Windows drivers.  It won't work in Linux no matter how hard I try.

Is there any way to use the wireless Internet connection in the Windows guest to give connectivity to the Ubuntu host?  It seems like you should be able to do something like--it would basically just be a reverse bridge of the normal setup where the guest receives connectivity through the host--but I've never heard of it.  I've tried searching but I'm not sure which terms to use.  If anyone has any suggestions, I'd be grateful for them.

---

### Post by __p1n__ on 2009-09-29
> **pytheas22 said:**
> Imagine this scenario: I have a guest operating system in VirtualBox running Windows XP on an Ubuntu host.  I have a USB wireless card that gets passed directly to the guest operating system, and works there using the Windows drivers.  It won't work in Linux no matter how hard I try.

Is there any way to use the wireless Internet connection in the Windows guest to give connectivity to the Ubuntu host?  It seems like you should be able to do something like--it would basically just be a reverse bridge of the normal setup where the guest receives connectivity through the host--but I've never heard of it.  I've tried searching but I'm not sure which terms to use.  If anyone has any suggestions, I'd be grateful for them.

If the card works in the guest os then the only reason that it wouldn't work in the host os is configuration.  Have you tried manually configuring the wifi device in the host os?  If you can't find a linux wifi driver for that device then try running the windows driver in ndiswrapper.

Note: I'm not familiar with virtualbox - I use xen for HVM isolation - however the reverse bridge approach seems to be a non-starter with respect to the intent and implementation of vm's.

---


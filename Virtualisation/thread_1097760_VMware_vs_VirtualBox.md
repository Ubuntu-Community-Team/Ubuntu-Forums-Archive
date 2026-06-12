---
title: "VMware vs VirtualBox"
date: 2009-03-16
forum: Virtualisation
---

### Post by JerryI on 2009-03-16
I'm having difficulty installing VMware server 1.0.6 in Hardy, so someone  suggested that I should install VirtualBox instead.  I went to the VirtualBox website and encountered the first snag:

Note: The package architecture has to match the Linux kernel architecture, that is, if you are running a 64-bit kernel, install the appropriate AMD64 package (it does not matter if you have an Intel or an AMD CPU). Mixed installations (e.g. Debian/Lenny ships an AMD64 kernel with 32-bit packages) are not supported. To install VirtualBox anyway you need to setup a 64-bit chroot environment.

How do I figure out my linux kernel architecture and whether it is a 64-bit kernel to select the right package?  And how do I set up a 64-bit chroot environment, whatever that is?  All I know is that my computer has an AMD64 dual-core processor.  This is very confusing to someone who couldn't even spell linux a week ago.

---

### Post by binbash on 2009-03-16
uname -m if you see like x86_64 then it is 64 , i686 =32

---

### Post by dcstar on 2009-03-18
> **JerryI said:**
> I'm having difficulty installing VMware server 1.0.6 in Hardy, so someone  suggested that I should install VirtualBox instead.  I went to the VirtualBox website and encountered the first snag:
........

Why go to a website when the correct software is in the repositories?

---

### Post by JerryI on 2009-03-18
Issue resolved.  Thanks for all your help.  As I recall, I finally ignored the reported snag and the installation program didn't seem to care.

---

### Post by HankB on 2009-03-18
> **dcstar said:**
> Why go to a website when the correct software is in the repositories?
Very true if the OSE version (of VirtualBox) in the repositories meets your needs. I needed USB support and according to what I read, I need to use the commercial version of the product to get that support. Fortunately that is free for individual use. In fact, Sun maintains their own repositories so it can be managed by apt and synaptic as is done with the other Ubuntu S/W. You only need to add their repository to your sources.

Using Ubuntu 8.10 and VirtualBox 2.1.4 I am not aware of any requirement for a chroot.

-hank

Edit: This is on a 64 bit host running 64 bit S/W.
```
hbarta@cypress:~$ uname -m
x86_64
```

---


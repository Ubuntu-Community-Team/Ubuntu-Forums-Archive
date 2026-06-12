---
title: "Ubuntu 8.04 Xen Guest Kernel"
date: 2010-05-15
forum: Virtualisation
---

### Post by billy_rud10 on 2010-05-15
Hey,
   I currently have an ubuntu 8.04 guest running in PV mode through XenServer using 2.6.24-27-xen as the kernel. I need to recompile this kernel but cant seem to get the correct source. I tried doing "apt-get source linux-image-2.6.24-27-xen", copying the config and doing a make oldconfig which displays:

> .config:37:warning: trying to assign nonexistent symbol X86_NO_TSS
.config:38:warning: trying to assign nonexistent symbol X86_NO_IDT
.config:136:warning: trying to assign nonexistent symbol X86_XEN
.config:145:warning: trying to assign nonexistent symbol X86_64_XEN
.config:187:warning: trying to assign nonexistent symbol X86_XEN_GENAPIC
Does anyone have pointers on how to compile a guest xen kernel?

---

### Post by tgalati4 on 2010-05-15
Hardy has xen 3.2 built for it.  What version of the hypervisor are you running?

apt-cache search xen

Methinks the guest xen OS kernel and the hypervisor must be the same version.

[http://wiki.xensource.com/xenwiki/InstallationNotes](http://wiki.xensource.com/xenwiki/InstallationNotes)

Here's an older howto:

[http://www.howtoforge.com/perfect_setup_xen3_debian_p3](http://www.howtoforge.com/perfect_setup_xen3_debian_p3)

---

### Post by billy_rud10 on 2010-05-15
> **tgalati4 said:**
> Hardy has xen 3.2 built for it.  What version of the hypervisor are you running?

apt-cache search xen

Methinks the guest xen OS kernel and the hypervisor must be the same version.

[http://wiki.xensource.com/xenwiki/InstallationNotes](http://wiki.xensource.com/xenwiki/InstallationNotes)

Here's an older howto:

[http://www.howtoforge.com/perfect_setup_xen3_debian_p3](http://www.howtoforge.com/perfect_setup_xen3_debian_p3)


The Ubuntu guest is working just fine. I just need to recompile the xen kernel on the guest OS.

---

### Post by tgalati4 on 2010-05-15
Did you install xen-docs-3.2 and look at the howtos?

What xen compiling tutorial are you following?

---

### Post by billy_rud10 on 2010-05-16
I did install xen-docs-3.2 it doesn't seem to contain any documentation, unless theres something I'm missing.
> root@server05:/usr/share/doc/xen-docs-3.2# ls
changelog.Debian  copyrightI'm not following a guide specifically aimed at xen compiling because I was unable to find one. I'm following [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile).

---

### Post by tgalati4 on 2010-05-16
I'm in the process of building a xen server using Hardy on an old poweredge, so it will take me a few days to put together a working procedure.

---

### Post by TheFu on 2010-05-16
Or you could use this Hardy Xen from Repositories HowTo - [http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories](http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories)

---

### Post by billy_rud10 on 2010-05-16
> **TheFu said:**
> Or you could use this Hardy Xen from Repositories HowTo - [http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories](http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories)


I don't want to install xen on ubuntu. I want to recompile the linux-image-xen GUEST kernel.

---


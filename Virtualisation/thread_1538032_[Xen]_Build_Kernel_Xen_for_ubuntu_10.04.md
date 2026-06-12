---
title: "[Xen] Build Kernel Xen for ubuntu 10.04"
date: 2010-07-24
forum: Virtualisation
---

### Post by drbazz on 2010-07-24
Hi all,
I'm trying to install xen 4.0on my ubuntu 10.04 (64 bit version)

I followed some guides found on the internet, but I got no result :(

I followed this guide to compile kernel 2.6.32 for xen 4.0:
[http://bderzhavets.wordpress.com/2010/07/08/set-up-xen-4-1-unstable-2-6-32-16-pvops-dom0-on-top-of-ubuntu-10-04-server/](http://bderzhavets.wordpress.com/2010/07/08/set-up-xen-4-1-unstable-2-6-32-16-pvops-dom0-on-top-of-ubuntu-10-04-server/)

After the download using git, entering the menuconfig of the kernel, the guide tells to enable the xen support and the backend, that is:
 - I have to anable the option: Enable Xen Compatible Kernel , but I can't find it... I realized that it depends on which "subarchitecture" i choose for my Processor, but I can't find this option either....

What am I doing wrong? ](*,)

Thank you for your support!
:popcorn:

---

### Post by TheFu on 2010-07-24
Someone else suggested to use the Debian upstream Xen kernel. Much easier than building it yourself.

Sorry, I'm not much help with your kernel compiling question.

---

### Post by drbazz on 2010-07-25
Thank you for your answer..
what kind of package do you suggest? should I get the stable 2.6.26 or unstable 2.6.32?
What are the differences?

Anyway if someone can give me hints on how to build it, it's appreciated :P

---

### Post by juancarlospaco on 2010-07-26
kvm*(?)*

---

### Post by drbazz on 2010-07-27
I need xen to try the difference with kvm :P 
I need it as a hypervisor of UEC (Eucalyptus)

---


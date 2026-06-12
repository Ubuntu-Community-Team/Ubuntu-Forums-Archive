---
title: "KVM and WinXP on Ubuntu 10.04 x86_64"
date: 2011-01-17
forum: Virtualisation
---

### Post by Brad wilkinson on 2011-01-17
Hello,

I am trying to get a Windows XP (32 bit) instance to run as a guest OS on my current Ubuntu 10.04 x86_64 system. I've read around a bit, but I suspect my questions are a bit basic - please bare with me.

1) If I want to install WinXP to run games & stuff, is KVM the virtualisation tool to use (I noticed something about KVM being not for graphical installs, but I could have been getting confused with the graphical install tool).

2) Once I have installed KVM and the Virtual Machine Manager (through the repos and synaptic)- Am I suppose to install from a XP disk the same way I would for a new PC (going through setup-install and so on, then registering the product key) or do I need an image of a pc that is already set up and running? (and if so, where do I get one of those that is set up for my machine? I built this Ubuntu PC 'cause my old Windows Athlon XP machine was to flaky for words).

3) Will I still need some sort of anti-virus on the WinXP if I intend to go onto the internet with it? (I assume so - just checking).

Cheers,

Brad

---

### Post by Brad wilkinson on 2011-01-30
Yeah, so it really helps if you have Virtualization turned on in the BIOS before you start trying to install a guest OS......

Anyway, thanks to all those who PM'd me with help.

Cheers,

Brad

---

### Post by Brad wilkinson on 2011-01-30
so I thought I had it all figured out last night. But today when I try to run my guest WinXP (that I thougt was installed and working before I knocked off) I get the error message:

> Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/engine.py", line 588, in run_domain
    vm.startup()
  File "/usr/share/virt-manager/virtManager/domain.py", line 150, in startup
    self._backend.create()
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 300, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: monitor socket did not show up.: Connection refused

Can anyone suggest what is wrong?

---


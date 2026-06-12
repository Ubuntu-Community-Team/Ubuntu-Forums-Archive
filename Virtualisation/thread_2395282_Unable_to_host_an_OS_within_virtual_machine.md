---
title: "Unable to host an OS within virtual machine"
date: 2018-06-29
forum: Virtualisation
---

### Post by _Makke_ on 2018-06-29
Hi, 

It's been a few years since I've worked with Ubuntu. I want to give it another go, but I'm stumbling over an irritating problem. I need to have a virtual machine to host a W10. But I can't run both VirtualBox and VMWare. I can install it, but when starting a VM I receive an error on both VirtualBox and VMWare.

It's a clean install. I've tried multiple times with Ubuntu and ElementaryOS, but I keep having the same issues. I've uploaded the error messages.

I've been searching on Google, but nothing seems to help. But I'm obviously doing something wrong, why would VirtualBox and VMWare not work on a freshly installed Linux distro?

Does someone know what I'm doing wrong?

Thanks in advance :-)

---

### Post by QIII on 2018-06-29
Moved to Virtualisation.

Are you attempting to run them both at the same time?

---

### Post by _Makke_ on 2018-06-29
No. I first tried Virtualbox. Searched for help via Google and while I wasn't succeeding I wanted to try VMWare. But again, the errormessage. :-(

---

### Post by TheFu on 2018-06-30
I don't think that multiple hypervisors  can be installed on the same physical machine without lots of manual management of which kernel extensions are loaded.  I've seen VMware engineers running other hypervisors in a VMware virtual machine to show that nested virtualization was possible, but they suggested it wasn't something they suggested to anyone.

But really, have you considered using the native Linux hypervisor, KVM?  It is built into the kernel.  Just be certain you remove the other hypervisors before installing, if you choose to go that way.

Both your images show error messages that have corrective actions to take.  Did you try those? What happened?

---

### Post by The Cog on 2018-06-30
I would suggest KVM as well, if only because it is built in. Sudo apt install virt-manager.

---


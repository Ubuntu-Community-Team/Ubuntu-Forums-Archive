---
title: "How much to install/configure for VM to work well?"
date: 2011-12-30
forum: Virtualisation
---

### Post by louarnold on 2011-12-30
I wanted to try installing a VM system on my PC. However, I'm not sure just how much of Ubuntu should be installed (as a host) to make things work. I assume I'll be able to install Ubuntu or Windows into the VM. Should I leave the host as a bare-bones system, or install servers such as Apache or Samba? What about partitions, boot managers. old kernals, data drives, etc.?

---

### Post by Dangertux on 2011-12-30
There are a couple of questions you need to answer to help you make that decision. 

The first is, are you virtualizing systems just for desktop use, or are you wanting to create virtual servers?  For desktop play, you can pretty much do whatever you want with the host. I usually virtualize most of the OS'es I play in, and use a pretty bare bones host system, though that is entirely by preference. For desktop usage I would recommend VMware or VirtualBox. If you are virtualizing older OS'es you may wish to use KVM, for instance I know RHEL 3 won't run in Vbox. 

If you want to create virtual servers I would recommend KVM or Xen Hypervisor. And really nothing installed on the host.

Truthfully, you don't need additional software other than the hypervisor installed to virtualize, so that may be the ultimate answer to your question.

Hope this wasn't too convoluted.

---

### Post by louarnold on 2011-12-31
> **Dangertux said:**
> There are a couple of questions you need to answer to help you make that decision. 

The first is, are you virtualizing systems just for desktop use, or are you wanting to create virtual servers?  For desktop play, you can pretty much do whatever you want with the host. I usually virtualize most of the OS'es I play in, and use a pretty bare bones host system, though that is entirely by preference. For desktop usage I would recommend VMware or VirtualBox. If you are virtualizing older OS'es you may wish to use KVM, for instance I know RHEL 3 won't run in Vbox. 

If you want to create virtual servers I would recommend KVM or Xen Hypervisor. And really nothing installed on the host.

Truthfully, you don't need additional software other than the hypervisor installed to virtualize, so that may be the ultimate answer to your question.

Hope this wasn't too convoluted.
I think I want a bare-bones host and then to add a Linux guest that runs Samba and Apache. But on that same guest i need to do development. The VM is attractive because if I make a mistake with what I add or remove in development tools, I can simply go back to what was earlier. At least I hope that VM can help me with that.

Having said that, I might need to run Win XP and 7 as guests, but not old versions of Linux.

---


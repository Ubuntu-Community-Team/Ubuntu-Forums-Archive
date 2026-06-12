---
title: "virtualization support in 8.04"
date: 2008-03-28
forum: Virtualisation
---

### Post by esj on 2008-03-28
I'm trying to run 8.04. as a guest in VM Ware server.  I installed the virtual support kernel, open-vm-tools and open-vm-tools-gui.    Two problems I've encountered so far.  The first is that there doesn't seem to be any "clean shutdown" code.  with VM ware tools, you can enter your own script to do whatever you want on shutdown.  The default case is a clean shutdown as if you typed "shutdown -h".  The other problem is that the GUI tool won't run over the network to a remote X11 server.  It's apparently dependent on some form of special case code on a local to it X11 server.

I'm assuming that the GUI tool is a dead loss for the time being and I can live without it but, I do need clean shutdown capability.  Since the VM ware tools complains about the pre-existing virtual machine modules in the virtual kernel, do I need to go to a nonvirtual kernel and install VM ware tools or is the clean shutdown capability available elsewhere?

---

### Post by dcstar on 2008-03-29
> **esj said:**
> I'm trying to run 8.04. as a guest in VM Ware server.  I installed the virtual support kernel, open-vm-tools and open-vm-tools-gui.    Two problems I've encountered so far.  The first is that there doesn't seem to be any "clean shutdown" code.  with VM ware tools, you can enter your own script to do whatever you want on shutdown.  The default case is a clean shutdown as if you typed "shutdown -h".  The other problem is that the GUI tool won't run over the network to a remote X11 server.  It's apparently dependent on some form of special case code on a local to it X11 server.

I'm assuming that the GUI tool is a dead loss for the time being and I can live without it but, I do need clean shutdown capability.  Since the VM ware tools complains about the pre-existing virtual machine modules in the virtual kernel, do I need to go to a nonvirtual kernel and install VM ware tools or is the clean shutdown capability available elsewhere?

I run the 8.04 beta (actually a massively upgraded alpha) in a standard Ubuntu VM with the normal kernel with no problems at all.

---


---
title: "Virtual Host OS"
date: 2008-04-16
forum: Virtualisation
---

### Post by astabeno on 2008-04-16
Does anyone know of a Linux distro that would function only as a host for virtual guest desktops.  Server visualization is great, but I want a desktop that I can boot up with a minimal gui that lets you launch multiple desktops right off that computer instead of having a host running vmware or virtual box.

---

### Post by Bosk22 on 2008-04-18
Xen Express by Citrix may do what you want if I have understood your question correctly!!!!

Bosk

---

### Post by HermanAB on 2008-04-18
VMware ESX

---

### Post by astabeno on 2008-08-22
We are using VMWare infrastructure at my work and its very cool.  What I am thinking of is a product that uses hypervisor technology but for a desktop.  You could boot into a host OS that displays a menu that lets you launch guest OS's right on top of the hypervisor host OS.  It would be ESX or Xen with a simple gui lets you view the guest OS's instead of over using a client on another computer to get to the terminal of the guest.  That way you could run a few virtual on a laptop with the host having a very small footprint, instead of having to run a full blown Ubuntu OS or Windows OS to run guest of that.

---


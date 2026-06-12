---
title: "free hypervisors"
date: 2011-11-17
forum: Server Platforms
---

### Post by Vegan on 2011-11-17
At the moment I am using Server 2008 R2 Hyper-V which is free for my hypervisor.

I was wondering what are the best options for Linux in a data center.

I have used Ubuntu Linux Server  for a long time so I have a strong familiarity on how to use the command line and the major components.

I have Ubuntu install as a VM on my server but its not being used for web hosting at the moment. I am using IIS for now and wondering how long before it blows up and I post "You're Fired".

:guitar:

---

### Post by rubylaser on 2011-11-17
[ESXi]("https://www.vmware.com/tryvmware/index.php?p=free-esxi5&lp=default"), [Xen]("http://www.citrix.com/lang/English/lp/lp_1688615.asp"), or [Proxmox]("http://pve.proxmox.com/wiki/Main_Page") are all great, free Virtualization platforms.

With Hyper-V, you'd need to purchase a Server 2008 license, so not exactly "free", although the hypervisor itself is :)

---

### Post by spynappels on 2011-11-18
I have traditionally used ESXi, but am now looking at KVM on a barebones Linux server, seems to be a viable option.

There is another option, use virtualbox on a Linux machine and run it headless, VirtualBox is now a robust and reliable product, but I have no experience running it headless.

---


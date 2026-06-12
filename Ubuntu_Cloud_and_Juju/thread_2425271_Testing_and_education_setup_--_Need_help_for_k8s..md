---
title: "Testing and education setup -- Need help for k8s."
date: 2019-08-22
forum: Ubuntu Cloud and Juju
---

### Post by 1clue on 2019-08-22
Hi all,

I'm trying to get my head around kubernetes. I have microk8s installed but I want to also have a pseudo cloud to emulate a real production environment.

My plan is to install VMs on KVM/QEMU to act as nodes, and then have the 9 nodes (3x worker nodes, 3x etc/backplane nodes, and possibly 3x rancher nodes) to test things out on.

I was hoping to use the smallest VM image I could find for the VMs. Which apparently would be RedHat's bare metal build? Not sure that's right, it doesn't seem consistent with what I know about prior builds of theirs.

So hardware. I have 2 pieces of hardware to play with here:
[LIST=1]
[*]An older i7, 24GiB RAM and lots of disk space. This is my workstation.
[LIST=1]
[*]Running Ubuntu 18.04.
[*]Has virt-manager on it and libvirt.
[/LIST]

[*]A SuperMicro 8-core atom build: [https://www.supermicro.com/en/products/motherboard/A1SRM-LN7F-2758](https://www.supermicro.com/en/products/motherboard/A1SRM-LN7F-2758) with currently 16 GiB RAM and probably adequate disk space.
[LIST=1]
[*]This is EXTREMELY close to an Antsle One. Only I built mine before I was aware of Antsle.
[*]It supports hardware virtualization but can't donate a NIC directly to a guest.
[*]Running Gentoo.
[*]Has libvirt
[*]Command-line system, no GUI.
[/LIST]
[/LIST]

Both systems have an SSD and at least one spinner.

The questions:
[LIST=1]
[*]What's the best OS to put on the guests? These will be my "nodes" on the kubernetes command line.
[*]How do I hook them up? "juju clouds" does not seem to have a happy option.
[/LIST]

Thanks.

---

### Post by digikin on 2020-01-19
So, I own an Antsle and its extremely difficult to run containers on their machine.  It is possible to run docker without an issue but you are running it on the base operating system of Antsle.  Using their machine you do not have the option to spin up a Ubuntu virtual machine and install docker even if you manually assign a physical NIC to it.  So to run kubernetes I didn't get that far because of the limitations.  
In my opinion, your easiest option is to build MAAS virtually somewhere and add your older i7, 24GiB RAM and lots of disk space as a KVM host.  Once that is configured it becomes your private cloud and you can run juju commands against it to build a full kubernetes cluster.  
Currently in my lab I have:

Workstation/Main PC
36core/64gb for running docker, lib-virt and lxc virtualization.  
Dell Server:
48core/96gb connected to MAAS as KVM host for private cloud to run anything.  

Unfortunately my Antsle sits not powered on right now.  I should turn it back on it was a quick way to get simple testing done.

---


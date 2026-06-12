---
title: "Installing open-vm-tools on Ubuntu Server 14.04 LTS"
date: 2016-12-06
forum: Virtualisation
---

### Post by ckreuth44 on 2016-12-06
Hi, I have a VMWare 3 node cluster running ESX 5.5.0, 4345813 running a bunch of Windows VM's.  I've had reason to add a Linux server for Rocket Chat.  I've selected Ubuntu 14.04 LTS per the documentation for rocket chat and deployed the VM and now I'm trying to get the VMWare tools installed.  As many of you know VMWare does not recommend using their tools but rather open vm tools.  

When I run sudo apt-get install open-vm-tools the following output is returned:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package open-vm-tools is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'open-vm-tools' has no installation candidate


I also read somewhere to try sudo apt-get install open-vm-tools-lts-trusty

When I do this the following output is returned:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package open-vm-tools-lts-trusty

Now I need the tools on there as this will inevitably be a production product.  Any suggestions?

Thanks in advance.

---


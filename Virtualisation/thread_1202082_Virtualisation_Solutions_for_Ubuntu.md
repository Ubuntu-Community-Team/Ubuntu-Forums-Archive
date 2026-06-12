---
title: "Virtualisation Solutions for Ubuntu"
date: 2009-07-01
forum: Virtualisation
---

### Post by stefanadelbert on 2009-07-01
I'm looking for an alternative to VMWare for virtualisation of 32bit Ubuntu, initially on Ubuntu 64bit host, but also on Windows XP and other hosts at some later point. It would also be nice to put work into creating VM's could be run in a cloud much further down the line.

VirtualBox seems very mature with version 3.0.0 released recently, although there are some (Enterprise) features that are closed-source.

I realise that kvm is the Ubuntu supported virtualisation platform, but is kvm a replacement for VMWare or VirtualBox? I've also read that kvm requires the host (CPU?) have virtualisation compatible hardware. Is this an absolute requirement or just for support of certain features in the guest (3D graphics, etc.)?

Any recommendations on virtualisation solutions would be welcome.

Thanks
Stef

---

### Post by juancarlospaco on 2009-07-01
KVM replaces VMWare.

kvm requires the host CPU have virtualisation compatible hardware for good performance.
CPU virtualisation extensions brings up 3D graphics, full performance, M$ Windows support.

for desktop use Virtualbox 3
for server use KVM+SSH and Convirt 1.1 for centralized managment

---

### Post by scorp123 on 2009-07-02
> **stefanadelbert said:**
> Any recommendations on virtualisation solutions would be welcome. If you really really want or need "Enterprise" features that are otherwise only found in really expensive products such as "VMWare Infrastructure" I'd go with this:

"ProxMox Virtual Environment"
[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

"ProxMox VE" is in principle a Debian with OpenVZ + KVM virtualisation built-in. Very awesome. It can be clustered. And virtual machines can be moved between cluster members without downtime. Basically this is like a free "VMware ESX" clone.

So if you really want Enterprise-level features without that perversely hefty price tag that VMware puts on their products, go for ProxMox.

---

### Post by juancarlospaco on 2009-07-02
but he said FOR Ubuntu, and Proxmox is a stand-alone entire OS
*I dont find features on Proxmox that Convirt 1.1 don't have *
:)

---

### Post by scorp123 on 2009-07-02
> **juancarlospaco said:**
> but he said FOR Ubuntu, and Proxmox is a stand-alone entire OS Ah bummer, I seem to have missed that "for Ubuntu" part ... thanks for pointing that out. Yes, you are right :D

---

### Post by stefanadelbert on 2009-07-02
Thanks for the replies. I reckon I'll give KVM a go.

For those reading this post, this is a good [resource]("https://help.ubuntu.com/community/KVM") for installation and info on KVM in Ubuntu.

Stef

---


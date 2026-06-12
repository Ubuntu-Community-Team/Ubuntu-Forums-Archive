---
title: "Xen frontend web GUI tool?"
date: 2008-09-22
forum: Virtualisation
---

### Post by quad3d@work on 2008-09-22
Looking for a "working" solution but couldn't find any...

My company is starting to deploy Xen to replace VMware free. I am 100% comfortable working with Xen on CLI, but upper management is requesting if any GUI tool can be installed along side CLI. Mainly for the Windows team to manage Windows server domUs.

There are three tools I'm currently looking at and here is my findings.

** 1) Enomalism**
Seems to be a good tool but I cannot get it working under Ubuntu nor CentOS. Even the developers stated Ubuntu's Xen is broken (which is not), and Ubuntu is moving toward KVM. They mentioned RHEL/CentOS have "near perferct" Xen implementation and recommends using CentOS+Xen+Enomalism.

I've deployed couple Linux/Windows/Solaris(OpenSolaris) domUs for past few months and the Ubuntu server is getting hammered. Not a single issue.

I find Enomalism just too broke to be usable. I followed their installation on Wiki to the dot.


** 2) Bixdata**
It's not really a Xen/VMware management tool. More like a generic system management/monitoring tool. Not suitable in my case.


** 3) Virtual Machine Manager (virt-manager)**
I tried to get it working 3-4 months ago, never worked. I think it was the libvertd being broken. Sun xVM uses this and my company's Solaris team have decent amount of success with it.



I would need something matching the following,
1) Detailed resource monitoring, something uses RRDTool I guess. CPUs, HD, network... etc.

2) Complete domU management. This includes new domU creation, resource assignements, snapshot (with LVM would be nice :) ).

3) Backend management for HVM guests. This is more of VNC connection, in case RDP/FreeNX don't work.



I also are interested in Zentific, but they are not released yet. I'm wondering if anyone done a working Ubuntu+Xen 3.2+Enomalism successful installation? Thanks in advance for any advices/tips! :guitar:

---

### Post by kameleon25 on 2008-11-10
I too have been looking into something very similar. This is the only thing keeping me from rolling out xen on a few servers to consolidate machines. Like you, upper management is requesting a GUI.

---

### Post by Vadi on 2008-11-10
I'd recommend virt-manager, as the gui was quite well designed when I was trying it out. I think it's limited to kvm though from what I remember.

---

### Post by Hibbelharry on 2008-11-12
virt-manager also handles xen. Simple console logins via ssh serve also well for most things. you've got the xen tools and virsh.

---


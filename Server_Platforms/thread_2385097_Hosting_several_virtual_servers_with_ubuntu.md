---
title: "Hosting several virtual servers with ubuntu"
date: 2018-02-16
forum: Server Platforms
---

### Post by defreeze on 2018-02-16
Hi all

I have tried to find easy, yet detailed how to for hosting virtual servers with ubuntu, but to no avail. 

If you know a good one that could be shared here that would be excellent!

Also, it would be great if you could post a short description of how things are usually done to achieve running several servers on one physical ubuntu server. I am aiming to have nextcloud, apache, collabora and possibly another groupware running on Lenovo TS.


defreeze

---

### Post by TheFu on 2018-02-16
Welcome to the forums.

vmware player
virtualbox
kvm+libvirt+virt-manager <--- the only non-proprietary solution.
XenServer

And those are just the ones off the top of my head that provide HW virtualization.  There are probably 20 that do Cgroup-based "containers" like docker.

There are hundreds of how-to videos on youtube for each of those, if you learn by watching.

There's also **Proxmox**, but it takes over a system, completely. Very handy if you want to wipe a system completely and dedicate it for virtual machines.  I've never used it, but know a few small businesses (and large) that use it extensively.

I use:
* Ubuntu Server - that's the base OS.
* LVM for storage management - 50 reasons why this is smart for servers, but you don't have to use LVM.
* bridge-utils - I prefer manually creating a few lilnux bridges on my VM servers because the automatically made versions were less-than-great in the past. Never got out of that habit and haven't tested to see whether they corrected the performance and disconnect issues from 2010.
* kvm / qemu - really kvm. This is the kernel module doing all the type-1 hypervisor work.
* libvirt - this is a middleman library that lets different GUIs have access to the KVM tools, bridges, storage, remote managers, and different user-based tools, like .... 
* virt-manager (GUI), virsh (CLI)

Libvirt prefers to work using ssh tunnels for remote management, so having ssh setup between the VM management client (no necessarily any VM "guest" machine) and VM server is my first step before doing anything else.  ssh is THE way that unix system admins manage systems, at least initially.

So all that writing just provides the parts.  Because virtualization on Linux is 10000x more flexible than on the other popular platforms, there is a trade off in complexity and simplicity.  

Linux storage can be bonehead or very complicated.  The hypervisor generally doesn't care, but **might** care about the storage.  For example, if you want clustering for the storage, you can include Sheepdog as the storage management. This let's the admin control how many copies of every file are maintained across a storage cluster.  It could be 1 or 1,000 copies. You choose.

Linux networking can also be bonehead or very complicated.  If it can be done in networking, then Linux can do it.  For example, for very high-performance networks, the normal linux bridge-utils might not provide sufficient throughput.  Other tools can be used instead like openvswitch, which is recommended for 10Gbps networking.

Flexible. Powerful.

But if you just want to install a package or two and point-n-click your way to an ok virtual machine solutions, then there is virtualbox.  Many people here find it acceptable.  Be careful to read the license carefully for each component.  Some parts aren't as "free" as they seem. The core vbox system is GPL, so no worries there, but when the guest additions ... be certain to review the license.

Lastly, I find the Ubuntu Community docs for KVM to be overly complex, especially for a single system setup.
* check that your system can use KVM with HW acceleration. **kvm-ok** will answer that. If yes, 
* **sudo apt install kvm virt-manager ssh fail2ban bridge-utils** - should install everything you need on a desktop
* logout, then login. No reboot should be needed - this gets your ID to see the new group.  Any libvirt admin should be in the libvirtd group.
* check that your userid is in the libvirtd group - **id**
* Run **virt-manager** as your normal userid. DO NOT use root.
... from this point on, it should appear pretty much like any other GUI virtual machine tool - vsphere, VMware Workstation/Player, virtualbox .... create a new HW platform and install into it using an ISO.

Defaults are good for compatibility, but not performance.  Get something working first.  Stay away from heavy GUI/GPU stuff.  For example, don't load Ubuntu Desktop or Kubuntu.  Use Lubuntu, Xubuntu or Ubuntu Server.  GUI stuff can work, but it is non-trivial to get acceptable performance.

---

### Post by LHammonds on 2018-02-16
libvirt and KVM are extremely popular.  It is the basis for Nutanix Acropolis which is due to surpass the virtualization leader VMware soon.

There are a lot of tutorials/articles out there.  I'd suggest reading as many as possible and take notes while you do it.  When you are well-versed in what others have wrote about it, you can form your own opinion on how to do it for your specific use-case and write your own how-to once you get it figured out (documenting what you do will help you later when you need to do it again or upgrade)

Here are a few results from my Google-Fu

[LIST]
[*][Ubuntu Dox - Libvirt]("https://help.ubuntu.com/lts/serverguide/libvirt.html") 
[*][Ubuntu Dox - VirtManager]("https://help.ubuntu.com/community/KVM/VirtManager") 
[*][How to install KVM on Ubuntu 16.04 LTS Headless Server]("https://www.cyberciti.biz/faq/installing-kvm-on-ubuntu-16-04-lts-server/") 
[*][Setup Headless Virtualization Server Using KVM In Ubuntu]("https://www.ostechnix.com/setup-headless-virtualization-server-using-kvm-ubuntu/") 
[*][Simple Virtualization With Ubuntu 16.04 Linux and KVM]("https://linuxconfig.org/simple-virtualization-with-ubuntu-16-04-and-kvm") 
[*][How to Install KVM and Create Virtual Machines on Ubuntu]("https://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/") 
[*][Install KVM (QEMU) on Ubuntu 16.04 / Ubuntu 14.04]("https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/install-kvm-qemu-on-ubuntu-14-10.html") 
[*][Ubuntu server 16.04 as a Hypervisor using KVM and Kimchi for VM Management]("http://www.ubuntuboss.com/ubuntu-server-16-04-as-a-hypervisor-using-kvm-and-kimchi-for-vm-management/") 
[/LIST]


LHammonds

---

### Post by defreeze on 2018-02-16
Thank you for your answers! This is really what I needed for some clarifications.

Any ideas on using LXD? Or is KVM the way to go? Seems at least the clearest solutions to start with.

---

### Post by LHammonds on 2018-02-16
> **defreeze said:**
> Thank you for your answers! This is really what I needed for some clarifications.

Any ideas on using LXD? Or is KVM the way to go? Seems at least the clearest solutions to start with.
I have not used LXD nor have I talked to anyone that has.  It sounds neat but I don't believe in magic and what they claim sounds like magic or something not practical.  I don't see LXD as a replacement to OS virtualization...more like a special use-case for specific application scenarios.

But if you are curious, the awesome things is that you can spin up a virtual environment and try it out to see what its all about.

**EDIT:** Looks like you can try LXD containers online here: [https://linuxcontainers.org/lxd/try-it/](https://linuxcontainers.org/lxd/try-it/)

LHammonds

---


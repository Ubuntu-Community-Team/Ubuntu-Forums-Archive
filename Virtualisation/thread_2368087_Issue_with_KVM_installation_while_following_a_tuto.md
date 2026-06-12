---
title: "Issue with KVM installation while following a tutorial"
date: 2017-08-06
forum: Virtualisation
---

### Post by lendon210 on 2017-08-06
I am currently following this [tutorial]("https://www.ostechnix.com/setup-headless-virtualization-server-using-kvm-ubuntu/") guide in order get a virtual machine set up on my Ubuntu Server 16.04.

After entering in this command
> sudo virt-install --name Ubuntu-16.04 --ram=512 --vcpus=1 --cpu host --hvm --disk path=/var/lib/libvirt/images/ubuntu-16.04-vm1,size=8 --cdrom /var/lib/libvirt/boot/ubuntu-16.04-server-amd64.iso --graphics vnc

It would get stuck with this response. Even after waiting for an hour it would still say the same thing.

> WARNING Graphics requested but DISPLAY is not set. Not running virt-viewer.
WARNING No console to launch for the guest, defaulting to --wait -1

Starting install...
Creating domain... | 0 B 00:00:01 
Domain installation still in progress. Waiting for installation to complete.
Can somebody please guide me on how to solve this issue?

---

### Post by deadflowr on 2017-08-07
*Thread moved to **Virtualization** *

---

### Post by TheFu on 2017-08-07
I have never used virt-install.  Do you have another linux desktop from which to connect and manage the kvm server?
If so, there are much, much easier methods.

* setup ssh connectivity between the desktop and server; use ssh-keys. That is important.
* install libvirt, kvm, and bridge-utils on the KVM server
* setup a bridge. I prefer a manually created bridge over the automatic ones libvirt provides
* add your userid to the libvirtd group
* on the desktop, install libvirt and virt-manager
* Run virt-manager and use the GUI to create the virtual machine to be run.  For less than 50 VMs, this is a nice management solution. virt-manager is very much like virtualbox, VMware Workstation, etc.  
* If you need more than 50 VMs, something like oVirt would be better, but with much more complexity.

If no remote desktop is needed, each VM is accessed over ssh.  ssh is the normal management tool for all Unix OSes.

I prefer to use SPICE+QXL for the remote displays if on the same LAN. It is faster, but not so good for internet use.  Over the internet, I prefer x2go for a remote desktop. These are seldom used.

Anyway, hope this helps.  Besides the package and bridge setup, no sudo/root is needed to create VMs, start/stop them.  Being a member of the libvirtd group (on the client and server) solves that.

---

### Post by Doug S on 2017-08-08
The [Ubuntu Serverguide]("https://help.ubuntu.com/lts/serverguide/libvirt.html") has some relatively recent stuff on using virt-install.

---

### Post by lendon210 on 2017-08-09
Thank you for your very informative post, I will have to take a look into using this solution.

In the last few days I have experimented with using phpvirtualbox and virtualbox in order to create and manage VMs on my server. However, it seems like phpvirtualbox had not been updated in over a year and is yet to official support the latest version of virtualbox 5.1. 

Overall, how do you feel about the performance of the VM compared to something like VMWare Workstation? Would it be able to render 3D graphics?

---

### Post by TheFu on 2017-08-09
Virtualbox is used for desktop-on-desktop virtualization, not for production servers. KVM is maintained as part of the Linux kernel and is extremely stable.  

Graphics?  If that is your primary consideration, you need GPU passthru. That won't work over the network, so only local access is possible.  I run all my VMs on headless systems, no GUI, no local access.  They are only accessed via ssh or X11 over the network or with a remote desktop.  No 3d graphics with those.

BTW, mentioning 3d graphics in the initial post would have been helpful.
The best solution for your needs depends on the problem you are trying to solve.

---

### Post by lendon210 on 2017-08-10
My ultimate goal would be to install an OSX guest on the KVM server and to remote into that VM in order to do some iOS programming. In terms of remote I am thinking of doing it locally and not over the internet. Would using the KVM with GPU passthru be enough to run the simulator smoothly and display it onto remote desktop?

---

### Post by heiko_s on 2017-08-27
In order to do 3D graphics, you'd need to have GPU acceleration in your VM. To get GPU acceleration, you can use a dedicated GPU for your VM. The problem is that you can't really remote that output, at least not in a simple way.
Some high end graphics cards can process graphics and make the output available via remote desktop protocols. Steve Perlman (if I remember correctly) actually started a company to offer remote gaming services. In any case, this technology is used to provide remote desktops to zero clients in a corporate environment, replacing fat clients (PCs) with thin or zero clients.

KVM VGA passthrough can get you the 3D performance in the VM, but getting the output on a remote display is another issue. If you know how to configure a remote desktop on your OSX machine that would deliver the goods (that is performance), you should be able to get this to work with VGA passthrough.

Hope this helps.

---

### Post by TheFu on 2017-08-28
Just saw that virt-manager v1.4 added opengl support for VMs. It isn't clear if that is local only or will also work over a network.  [https://www.phoronix.com/scan.php?page=news_item&px=QEMU-3D-Windows-Guests](https://www.phoronix.com/scan.php?page=news_item&px=QEMU-3D-Windows-Guests) - this is about code for Windows guest. Linux guests should already work, from my reading. I just don't have a new enough libvirt/virt-manager to see.

---


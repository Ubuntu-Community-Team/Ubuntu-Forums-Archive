---
title: "KVM/Virtlib - Ready for prime time?"
date: 2010-12-31
forum: Virtualisation
---

### Post by HDave on 2010-12-31
I have about 35 VMs running on VMWare Server 2.x.  While I've never been happy with it, it has done a reasonable job.  About 18 months ago I took a hard look at KVM, but found the qemu screen emulation to be slow and the libvirt tools to be buggy and lacking functionality.

I am thinking of rebuilding my virtualization server and still really like the idea of KVM.  I really prefer being able to ssh into my virtualization server and treat it like a real machine...something I can't do with ESXi.

So I ask, has KVM/qemu/libvirt progressed must in the past year?  Is it worth a week's time to re-evaluate?

---

### Post by ortayus on 2011-01-02
A year ago I started at a new organization and one of my first projects was to take some machines and get some KVM VMs up and running.  Since then I have stood up just under 50 machines.  All production machines are non-MS machines but I do run some wn7 test machines here and there.  Some VMs I started from scratch and others were vmware transplants.  

I don't really use any qemu commands (except for qemu-img here and there) but mostly use libvirt and virsh tools.  As for user access they only get ssh and sometimes they get no-machine remote access.

---

### Post by bodhi.zazen on 2011-01-03
> **HDave said:**
> I have about 35 VMs running on VMWare Server 2.x.  While I've never been happy with it, it has done a reasonable job.  About 18 months ago I took a hard look at KVM, but found the qemu screen emulation to be slow and the libvirt tools to be buggy and lacking functionality.

I am thinking of rebuilding my virtualization server and still really like the idea of KVM.  I really prefer being able to ssh into my virtualization server and treat it like a real machine...something I can't do with ESXi.

So I ask, has KVM/qemu/libvirt progressed must in the past year?  Is it worth a week's time to re-evaluate?

It depends on what you want to do exactly. If you are running servers, without X, yes KVM will do just fine.

Personally I suggest Fedora as IMO they are pushing the envelope more then Ubuntu in terms of KVM.

In terms of graphical tools, you virt-manager. You can ssh into virt-manager.

There are several web interfaces available for KVM, everything from Proxmox to others.

If you are wanting to run graphical applicateions with desktop integration, stay with VirtualBox.

Personally if I use graphical apps at all with KVM, I connect on a LAN to the built-in VNC server (which I find superior to the default).

HTH

---

### Post by HDave on 2011-01-03
> **bodhi.zazen said:**
> There are several web interfaces available for KVM, everything from Proxmox to others.

I was unaware of Proxmox...it looks good.  Does it use libvirt on the back end?

Any experience with virt-manager?  It was really flaky about a year ago...

---

### Post by HDave on 2011-01-03
> **ortayus said:**
> As for user access they only get ssh and sometimes they get no-machine remote access.

How do you get into the Win7 machines?  We have a few desktops being virtualized as well...though most are servers...

---

### Post by bodhi.zazen on 2011-01-03
> **HDave said:**
> I was unaware of Proxmox...it looks good.  Does it use libvirt on the back end?

Any experience with virt-manager?  It was really flaky about a year ago...

virt-manager is much better supported in RHEL / Fedora and if you have only used it on Ubuntu that may be the problem.

With Proxmox, they have a web interface to configure guests, either with openvz or kvm and I am not sure of what they user for a back end for KVM.

---


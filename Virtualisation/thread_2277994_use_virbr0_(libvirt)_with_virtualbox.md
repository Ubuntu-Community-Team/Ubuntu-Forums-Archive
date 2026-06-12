---
title: "use virbr0 (libvirt) with virtualbox"
date: 2015-05-13
forum: Virtualisation
---

### Post by odror on 2015-05-13
I have lxc and virtualbox running on the same machine. Because of a bug in virtualbox They cannot run simultaneously unless they a bridged to different interfaces.
The lxc is bridged to eth0 (my LAN).

I would like to bridge virtualbox to virbr0. I place virbr0 (routed mode)  as the attached adapter in in the network setting. The problem is that altough virbr0 is a associated with a dhcp  service the virtualbox is not assigned an IP and I cannot ping from the virtualbox to the local network.


Is it possible to have virtualbox setup with libvirt and if so how.

---

### Post by TheFu on 2015-05-13
Don't know the answer to your last question. Sorry.

I strongly suspect that virbr0 is attached to eth0 already.  Don't believe it is possible to connect another bridge to the same device. I could be wrong. Never seen it done that way and I've never tried it.

However ... 
you can run lxc containers inside a vbox VM that runs Linux.  Doing this is actually a best practice to avoid security issues in containers (of any sort) allowing easy compromise to the hostOS running all the other VMs. Does that make sense?

Or you can drop virtualbox and use KVM which works nicely with libvirt.  I don't know if or whether vbox works with libvirt, though I have read places where it seems to have that support. Just never tried it since switching to KVM a few yrs ago.

Anyways, you have many options.

---

### Post by odror on 2015-05-13
I have not experience with KVM. Can KVM run a virtualbox (w7) VM

---

### Post by TheFu on 2015-05-13
> **odror said:**
> I have not experience with KVM. Can KVM run a virtualbox (w7) VM

KVM can run Windows inside a VM. Use virt-manager for a GUI like vbox has, if that's your desire. virt-manager can be run local or remote thru normal ssh connectivity.

Honestly, I would just create another VM with vbox to put the LXC stuff inside.  Even with KVM, you'd still be smart to create a VM to put the LXC (or any containers like Docker) inside.
[containers and security]("http://marc.info/?l=openbsd-misc&m=119318909016582")

---

### Post by odror on 2015-05-13
I like the low overhead of lxc. I do not want to tie it to a virtual machine.  My problem is that I need a different NIC so that I can run both at the same time. I  would like to avoid using additional hardware NIC. I have tried vlan (did not work) I have tried different virtual interfaces that I found on my system (like virbr0) all did not work.  By did not work I mean that virtualbox was not assign an IP and I was not able to "see" my local net from virtualbox. I do not think that it is a firewall issue.

I do not want to use KVM unless it can use an existing (licensed windows) VM (created by virtual box)

---

### Post by TheFu on 2015-05-13
[http://siphon9.net/loune/2015/03/bridging-virtualbox-and-lxc/](http://siphon9.net/loune/2015/03/bridging-virtualbox-and-lxc/) seems to have an answer.
Manually create a bridge to be used by vbox - then both lxc and vbox can use it. Do not use the automatic bridges created by the vboc installation process.

This [http://ubuntuforums.org/showthread.php?t=1480138](http://ubuntuforums.org/showthread.php?t=1480138) says something similar, if I'm reading it correctly. Looks doable.

---

### Post by odror on 2015-05-13
Thank you. I used the first link with modification (use bridge instead of host only in vbox). Now I can have lxc and vbox on the same network WITHOUT crashing the system.
In the meantime I lost the connectivity to  the WAN from the LAN (except the server). I think is is The NetworkManager interfering.

---

### Post by TheFu on 2015-05-13
Yeah - you need to remove/disable network manager. For stuff like this, it gets in the way.

Also - make certain there is a **default route** for any VM you want to talk with the WAN. It should point to the network router/gateway.

---


---
title: "Server as VM host"
date: 2014-03-11
forum: Virtualisation
---

### Post by christossmail on 2014-03-11
Hi everyone,

I am trying to set up Server 12.04 as a VM host.  install went smooth, when I was asked what type of server it would be I selected VM host. I loaded VMware player everything went fine with that.  when i try to run VMplayer I get an error: "DISPLAY is not set, unable to open the VMware Player user interface."  I installed X server but still now love.  Im not sure where to set DISPLAY or what it should be set to.  I just want the vm's to be run on the local machine for right now.  I would like to keep the server as light as possible.  

Thanks for the help

---

### Post by wildmanne39 on 2014-03-11
*Thread moved to **Virtualisation**.*

---

### Post by CharlesA on 2014-03-11
How are you connecting to the machine?

---

### Post by christossmail on 2014-03-11
I am local,  connected directly to the server

---

### Post by 1clue on 2014-03-11
VMware Player is a desktop app.  It's intended to run while a user is logged in and requires a user interface.

What is it exactly that you intend to do?  VMs that start up on system start, or just occasional use?  Tell us about it.

There are a bunch of virtualization solutions out there, each has its strengths and weaknesses.  VMware Player does not fit with Ubuntu Server very well.

If you want your box to run a bunch (or a few) VMs which start up and stay running, then I would recommend you look at QEMU, which is probably what installed when you clicked VM Host on the install.  This is a typical solution.

If you really need VMware then I would recommend you get the ESXi hypervisor, the free one if your needs are small.  But if you do that, it wants to be on the bare metal and so you won't have Ubuntu anymore.

---

### Post by christossmail on 2014-03-11
I want to have about 4 vms running one windows 7, one ubuntu desktop,  etc.  the reason I want to use vmplayer is because i used vm converter to copy my windows 7 physical machine.  (previously i was duel booting windows 7 and ubuntu desktop.)  I tried to run ESXi but there is not driver for my NIC so the install fails.  I know I can get vmplayer running on Ubuntu desktop but that is a much heavier OS.  I would like the VM host to be as light as possible so the VM's can take up the resources.

---

### Post by CharlesA on 2014-03-11
You can run VMware VMDK's in VirtualBox or you can convert them to row/qcow2 to use with quem/KVM.

I've done that many, many times.

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02946277&cc=us&dlc=en&lc=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02946277&cc=us&dlc=en&lc=en)

For VirtualBox, just point it to the vmdk file.

---

### Post by christossmail on 2014-03-11
Ok I think I'm getting this.  so I can copy the VMware VDMK to my server and use virt-manager and virt-viewer to run the VM?

---

### Post by CharlesA on 2014-03-11
Yep. You just have to convert it from vmdk to qcow2, but the link above shows how to do that.

---

### Post by christossmail on 2014-03-11
great Ill try this now thanks for all the help

---

### Post by 1clue on 2014-03-11
OK that's another thing:  If you want all the features you're familiar with regarding snapshots,  then you should use cqow2, but if you want the fastest you can get then I would recommend raw format.

Otherwise, you seem to have the idea now.

---

### Post by CharlesA on 2014-03-11
Yeah, raw doesn't support snapshots, but I haven't really noticed much of a difference in performance between the two.

---


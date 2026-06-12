---
title: "Root on USB flash: Performance issues?"
date: 2013-05-07
forum: Virtualisation
---

### Post by 1clue on 2013-05-07
Hi,

I just installed a VMware ESXi free hypervisor on my box just to see what it's about, and now I'm replacing it with an Ubuntu for KVM.

The thing is, the HOWTO I used for ESXi said to put the ESXi on a USB stick, and leave the "real" drives for virtual machines.

Does this work for Ubuntu well enough to recommend it?

First thing, I'm not exactly planning to use this in the same way you would use ESXi.  I want a developer-oriented box which also hosts VMs, some of which start on system boot.  I want the VMs to work with low latency but they will not as a general rule use a lot of CPU.

I have a 256g SSD, a 750g spinning disk and can easily come up with more spinners.  It's an i7 920, so it's not exactly new but it's fit for some experiments.

Thanks.

---

### Post by heiko_s on 2013-05-12
In answer to your question: Unless you find a tutorial on how to run Ubuntu/kvm from USB, I wouldn't go this way. You would need to prepare a custom USB stick with kvm and your guest configurations. My guess is that VMware uses this for security reasons, perhaps also to increase uptime.

Here some related stuff that you may find of interest:
Not sure you need it, but VGA passthrough (and PCI passthrough) is real cool: [http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/600#post_19770787]("http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/600#post_19770787").

I use Xen with LVM drives and backup/restore is working very well with the LVM snapshot option, then dd in combination with pigz (a parallel gzip version). Here are two scripts I wrote to backup/restore a VM: [http://forums.linuxmint.com/viewtopic.php?f=42&t=133089](http://forums.linuxmint.com/viewtopic.php?f=42&t=133089). I use RAW storage on LVM for my VMs.

Hope its useful.

---

### Post by SmithJames2013 on 2013-05-12
I guess raw storage on LVM shows quite fantastic results..I am amazed by it's security and durability too.


[bulk flash drives](http://www.alpha-usb.com/)

---

### Post by 1clue on 2013-05-12
Thanks.  I already put the OS on LVM, haven't gone to the point of VMs yet.

---


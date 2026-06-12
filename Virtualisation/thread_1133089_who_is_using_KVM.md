---
title: "who is using KVM?"
date: 2009-04-22
forum: Virtualisation
---

### Post by pytheas22 on 2009-04-22
My boss has asked me for a list of organizations using KVM in production environments, in order to reassure him that KVM is a viable and stable alternative to expensive proprietary virtualization technology.  I was wondering if anyone here knows of such a list, or can at least say something like "I work for XXX Inc. and we use KVM in a production environment for..."

---

### Post by parkland on 2009-04-22
KVM and virtualization systems have pros and cons like anything else.

I'd push for virtualbox, run it in ubuntu and I'm certain you'll be astounded how much you can do.

It comes down to what you are trying to accomplish, but you shouldn't even consider s KVM solution until you push the limits of the hardware.

As an example, I scan lots of hard disk for spyware. 1 computer with ubuntu, virtualbox, and 8 microxp installations can scan many hard disks at once, since hard drive scanning only usually uses 5-20% CPU a computer, thus the "monster scanner" is able to scan more disks faster with the footprint of only 1 PC.

Now, I will also be using a KVM system to install OS's on multiple machines at once, since a VM wouldnt be realistic to do so, and should save having 8 monitors and keyboards and larger deskspace.

It all boils down to your situation.

---

### Post by parkland on 2009-04-22
OK, sorry, I just realized that you werent talking about a KVM switch....stupid me.

What can a kernel virtual machine do?

I'm interested to learn about it...

---

### Post by bodhi.zazen on 2009-04-22
Check out Proxmox :

[http://www.montanalinux.org/proxmox-ve-review.html](http://www.montanalinux.org/proxmox-ve-review.html)

[http://www.proxmox.com/](http://www.proxmox.com/)

[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

As to if it is appropriate to your environment, that is a mater of opinion, lol.

---

### Post by parkland on 2009-04-22
Alright, i checked out those sites and concluded that I am aboout 20 hours of reading to actually understanding what it is. LOL.


So, it runs VM,s has no graphical interface, and so what the VM is the only GUI on the machine?

My train of thought is boarding at the station.

---

### Post by bodhi.zazen on 2009-04-22
Proxmox is a Debian Host with OpenVZ and KVM, and a web interface.

See this video tutorial (as an example of what can be done):

[http://pve.proxmox.com/wiki/Hardware_setup_for_KVM_guests_%28Video%29](http://pve.proxmox.com/wiki/Hardware_setup_for_KVM_guests_%28Video%29)

---

### Post by parkland on 2009-04-22
So comparing this to running virtualbox on a ubuntu host... what are the pros and cons??

In the video, is he accessing a headless machine over a network?

Trying to understand... trying....

---

### Post by Yann2 on 2009-04-24
I work for Oxford Archaeology and we use KVM on production on 3 hosts and over 40 virtual machines :) (using Hardy)

New technology, but very exciting. Some small glitches, been able to workaround all of them so far. Not regretting my choice so far :P

---

### Post by pytheas22 on 2009-04-24
bodhi.zazen: Proxmox looks a lot like VMware ESX.  That could be useful, but I'd probably just stick with running KVM on generic Ubuntu server, since that's what I know best, and because we can purchase support for it.

parkland: Proxmox (which is basically just a specialized Linux distribution intended for easy deployment of KVM-based virtual machines, from what I understand) is probably faster than VirtualBox, but VirtualBox is more user-friendly at this point.  Proxmox is indeed headless; the only way to manage it is from a remote machine via a web interface (and maybe ssh too; I don't know).

Yann2: thanks for the reply--that's the kind of stuff I'm looking for.  I've done a lot of experimenting with KVM and have been impressed as well.  I have encountered a few odd bugs, but nothing I couldn't work around.  The other option is VMware, which costs an utterly astonishing amount of money (which I guess is not actually surprising, given that VMware has enjoyed a near-monopoly in the virtualization market for several years), is not particularly resource-efficient (in my experience) and is more difficult to manage (especially without running the Windows management console, which VMware has not bothered porting to Linux). So I'd really like to stick with KVM, and testimonies like yours help me make my case.

---

### Post by parkland on 2009-04-25
i downloaded it and tried to run it in virtualbox, but i cant even figure out how to log in to the interface.

SO, exacly what would this system be ideal for accomplishing...

??????

---

### Post by bodhi.zazen on 2009-04-25
Proxmox is used mainly for servers.

---


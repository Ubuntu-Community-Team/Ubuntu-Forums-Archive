---
title: "VirtualBox on Ubuntu Server 12.04"
date: 2014-05-25
forum: Server Platforms
---

### Post by Marc-NJ on 2014-05-25
I installed VirtualBox on my Ubuntu 12.04 LTS server and it works pretty well (along with phpvirtualbox for managing it).  However, whenever I reboot/shut down my server, I get this:

```
Stopping VirtualBox kernel modules ...failed!
(Cannot unload module vboxdrv) 
```

It doesn't seem to have any impact, but I just wanted to see if this was an issue, and if so, how I could solve it?  Thanks!

---

### Post by CharlesA on 2014-05-25
You'd have to check the system or kernel log to see why it fails to unload the kernel module.

---

### Post by nerdtron on 2014-05-26
Why use virtualbox on the server for managing virtual machines? You'd be better off just install a desktop version of ubuntu and then install virtual box.
A better way to create and manage virtual machine is to install the ubuntu-virt-server on the server. Then on you desktop computer, install the the ubuntu-virt-manager to have a GUI way to manage the virtual machines.
See this link [http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/](http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/)

---

### Post by CharlesA on 2014-05-26
> **nerdtron said:**
> Why use virtualbox on the server for managing virtual machines? You'd be better off just install a desktop version of ubuntu and then install virtual box.
A better way to create and manage virtual machine is to install the ubuntu-virt-server on the server. Then on you desktop computer, install the the ubuntu-virt-manager to have a GUI way to manage the virtual machines.
See this link [http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/](http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/)

Or one of the variety of web based KVM management stuff. :p

I use Proxmox myself, but I'm a but.. unconventional.

---

### Post by Marc-NJ on 2014-05-26
> **CharlesA said:**
> You'd have to check the system or kernel log to see why it fails to unload the kernel module.

I know some Linux/Ubuntu stuff relatively well, and some stuff I don't know at all - could you provide some add'l information on how to do this (and what I should be looking for) or maybe point me in the right direction for some add'l guidance online?  Thanks!

---

### Post by Marc-NJ on 2014-05-26
> **nerdtron said:**
> Why use virtualbox on the server for managing virtual machines? You'd be better off just install a desktop version of ubuntu and then install virtual box.
A better way to create and manage virtual machine is to install the ubuntu-virt-server on the server. Then on you desktop computer, install the the ubuntu-virt-manager to have a GUI way to manage the virtual machines.
See this link [http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/](http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/)

The reading I did online seemed to indicate that Windows OS's (as guest machines) worked better when run on VirtualBox (on an Ubuntu server) than anything else - is that not accurate?

I also don't use Ubuntu Desktop OS anywhere - just the server OS for some specific software and Windows OS for my workstations.  Would you still recommend I get rid of VirtualBox and use ubuntu-virt-server?  Can I run ubuntu-virt-manager on my Windows workstation?

Thanks!

---

### Post by Marc-NJ on 2014-05-26
> **CharlesA said:**
> Or one of the variety of web based KVM management stuff. :p

I use Proxmox myself, but I'm a but.. unconventional.

When you say web-based KVM management, you mean an alternative to [COLOR=#000000]ubuntu-virt-manager (presumably something I could run through a web browser on my Windows workstation) that ties into [/COLOR][COLOR=#000000]ubuntu-virt-server?  [/COLOR]

---

### Post by CharlesA on 2014-05-26
> **Marc_Bressman said:**
> I know some Linux/Ubuntu stuff relatively well, and some stuff I don't know at all - could you provide some add'l information on how to do this (and what I should be looking for) or maybe point me in the right direction for some add'l guidance online?  Thanks!

Check /var/log/kern.log or /var/log/syslog

It might tell you what happened but I'm not sure if the system logger was stopped before the error occurred or not.

> **Marc_Bressman said:**
> The reading I did online seemed to indicate that Windows OS's (as guest machines) worked better when run on VirtualBox (on an Ubuntu server) than anything else - is that not accurate?

I also don't use Ubuntu Desktop OS anywhere - just the server OS for some specific software and Windows OS for my workstations.  Would you still recommend I get rid of VirtualBox and use ubuntu-virt-server?  Can I run ubuntu-virt-manager on my Windows workstation?

Thanks!

I migrated away from Virtual Box a couple years ago on the server side of things even tho I still use it for Desktop virtualization at times. I haven't noticed any real performance difference between it and KVM, but my Win7 VM is usually just sitting idle.

I would say use what works for you. I mostly migrated away because phpvirtualbox was no longer being developed but it looks like that has changed.

> **Marc_Bressman said:**
> When you say web-based KVM management, you mean an alternative to [COLOR=#000000]ubuntu-virt-manager (presumably something I could run through a web browser on my Windows workstation) that ties into [/COLOR][COLOR=#000000]ubuntu-virt-server?  [/COLOR]

Yes. It would interact with kvm directly. Unfortunately I don't know enough about the different interfaces to tell you which to use if you really want to migrate away.

I've been using Proxmox: [http://proxmox.com/](http://proxmox.com/) for a while now and it's been fine for me.

Personally if VirtualBox works, stick with it.

---


---
title: "truly headless windows kvm?"
date: 2010-11-12
forum: Virtualisation
---

### Post by pereclies on 2010-11-12
First: Apologies if I'm violating some forum protocol here, I've searched the various threads on this topic, but they don't seem to either completely answer my question, or be detailed enough for me to understand exactly how to get started.

Setup:
I have a dedicated linux box, running Ubuntu Server 10.10, clean install with mediatomb all set up and working over the gigabit ethernet to my ps3, and that's fine. I modify the settings on the linux box using my macbook and ssh. My /etc/network/interfaces has been setup for static IP and is prepped for kvm with a bridge as described in the Ubuntu Server Guide.

Goal:
I'd like to have file sharing set up over samba, connected to a domain controller running as a virtual machine using Windows Werver 2008 R2 (I have legal serials for both 2008 and 2008 R2). I would like to be able to use this windows server for network windows installations and IIS7 testing. As far as the linux box, I'd like for it to remain truly headless (for the purpose of remote management and not having all sorts of gobbldygooky configuration files all over the place), if possible, and be able to use vnc to look at the guest VMs when I need to make a change.

Questions:
-It it even possible to not install X11 on the host and still accomplish the goals?
-If I do need to install X11, do I need much of a gui to get minimal functionality (do I need to install the whole ubuntu-desktop package group, or can I get away with just __(fill in blank)__?) and then steps to accomplish?
-I read about the need for tunneling vnc through ssh to access Windows enough to finish the install, how do I do this and why is this needed?

Finally, thanks if you read all of this.

---

### Post by gdahlm on 2010-11-12
Running X on a KVM host is not a requirement but a lot of the tools have dependencies that will force you to install several of the X packages.

If you don't mind them being on disk I would just do a normal install and then disable X on boot by running the following command.

sudo update-rc.d -f gdm remove

If you do not want dependencies installed you will need to compile from source which is much more complex as the debian qemu-kvm package it's self depends on libx11-6.

---

### Post by pereclies on 2010-11-13
Thanks for responding. I think you're right about it being either really complex or inevitable.

On a side note, I think I answered my own question, though in a different way. It seems (I still haven't been able to successfully install, and therefore, test) that vmware-server has this capability built in, using webhosting as the gui interface. It would have been nice to get an opensource solution that's also user-friendly.

---

### Post by gdahlm on 2010-11-13
try installing virt-manager on the host

then from another machine run ssh -X root@hostname

when you log in and type in virt-manager

That may be what you are looking for.

---

### Post by pereclies on 2010-11-13
> **gdahlm said:**
> try installing virt-manager on the host

then from another machine run ssh -X root@hostname

when you log in and type in virt-manager

That may be what you are looking for.

Thank you, I had no idea one could do that! My (perhaps dumb) goal was to not install X on the first place.

---

### Post by gdahlm on 2010-11-13
If you are not tied to ubuntu you can run proxmox

[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

it has a web interface but I haven't tried it, being an old unix hack I do almost everything at the command line.

---

### Post by pereclies on 2010-11-13
That's exactly what I'm looking for.  That Proxmox looks incredibly sexy.  Thanks!!

---

### Post by sh1ny on 2010-11-15
You can run any OS on ubuntu with KVM on a "headless" server. You don't need X for that. Ofcourse, switching to an out-of-the-box virtualization solution, is easier :) Because choosing the "Virtual Machine Host" task selection during the ubuntu install is too hard ;)

---

### Post by pereclies on 2010-11-15
> **sh1ny said:**
> You can run any OS on ubuntu with KVM on a "headless" server. You don't need X for that. ... Because choosing the "Virtual Machine Host" task selection during the ubuntu install is too hard ;)

Have you tried this yourself? You're right about choosing the option and getting the packages installed; it's not hard. The hard part comes with trying to make it work. Read up on the solutions given for viewing the VM, and you'll see that most involve installing X.

On a side note, I did try Proxmox, and it's a dream come true. I've got 4 virtual machines running and functional: Ubuntu 8.04, Ubuntu Server 10.04, Windows Server 2003 R2, and Windows Server 2008 R2. It uses the same technology available from the Ubuntu Server Virtual Machine Host, except it works, and it's all open source, and running on the latest version of Debian.

---

### Post by sh1ny on 2010-11-15
You can run the graphical tools on another host, so the server won't ever need X. I run about 50+ vm's on around 15-20 servers, never had or needed X on the servers. And yes, i do have win servers running like that. Again, no X needed.

---


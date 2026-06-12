---
title: "Virtualizing existing installation"
date: 2008-08-07
forum: Virtualisation
---

### Post by TorchlightJay on 2008-08-07
hello,
   So i have an installation of Windows XP with a setup on it. I was wondering if it was possible to somehow copy that installation into an image or something then setting it up on a VM of some sort.

---

### Post by HermanAB on 2008-08-07
Yes, some Googling will find the manual method to do that, but VMware has special tools for the purpose on their web site and it doesn't cost much - well worth the money.

Basically, you create a VM with an empty disk image, then copy the whole thing over exactly as if you are copying two real disk drives.

---

### Post by TorchlightJay on 2008-08-07
Cool, can you do this with virtually any hypervisor? I am using the XEN kernel but sometimes I utilize Parallels or VirtualBox depending on what I am trying to accompish. Will it work regardless of what I use. 

What's the name of that VMWare product and what else do I need from VMWare to get it all done? What would I need from others?

---

### Post by HermanAB on 2008-08-07
Xen is not a full virtualizer.  Xen is similar to BSD Jails.  Each Xen 'VM' is a only a subset of the system and all 'VM' share services of the main system.  That is why Xen can only run Linux VMs.

You can copy XP into VMware or Virtualbox VMs, but you first have to change some drivers to generic ones, before you copy it, since the VM is like a different piece of hardware.  The problem is similar to taking a HDD from a Dell PC and sticking it into a HP PC - it ain't gonna work unless you change some drivers first - notably the screen and the HDD driver.

---

### Post by HermanAB on 2008-08-07
Dup

---

### Post by TorchlightJay on 2008-08-07
Cool,
  So what is the process to get the OS off of my hard drive and turn it into some kind of image that I can then load into Vbox? Is there a special program I need or anything?

---

### Post by y@w on 2008-08-07
> **TorchlightJay said:**
> Cool,
  So what is the process to get the OS off of my hard drive and turn it into some kind of image that I can then load into Vbox? Is there a special program I need or anything?

VMware has a tool:

[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

---

### Post by tuxxy on 2008-08-07
You could jsut access the existing XP install through virtualbox if its on a seperate hard drive?

---

### Post by TorchlightJay on 2008-08-07
It's on a different hard drive on a different computer. That's the main problem. I installed this setup for a database on an HP running Windows XP. Well I decided that it would be best to move this to a virtual environment on our server running Linux and use the HP as just a desktop. I guess I can use that converter. 

What other ideas do you have? Maybe I can move the hard drive to the linux server and copy it off of vbox?

---

### Post by tuxxy on 2008-08-07
If you can move the hard drive to the same machine then yes it will be accessible through virtualbox in ubuntu.

---

### Post by TorchlightJay on 2008-08-08
Cool, so when i move the hard drive to my pc, what do i do? I can't keep the hard drive in that machine, it needs to go back. What do I do to get the non-virtualized install onto a vbox vm?

---


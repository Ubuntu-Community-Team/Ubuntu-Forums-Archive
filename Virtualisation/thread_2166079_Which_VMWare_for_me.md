---
title: "Which VMWare for me?"
date: 2013-08-07
forum: Virtualisation
---

### Post by Julian1968 on 2013-08-07
Hello

I have been running Virtual box on Ubuntu 13 and although slow I like the ability to nip into Windows to use some software there. I have tried the VMware player but could not download the tools, even after searching for the solution (Im not bright with all the codes and probably missed something)

But I am not surte which VMware version maybe good for my needs even.

So, for me to use Windows XP, maybe Win 7, Adobe After Effects and Photoshop, what do you think I need.

Im pretty new to this really so any help will be good

Thanks

---

### Post by MrManican on 2013-08-07
IMO, I am using virtual box by Oracle. I have made many a dual-boot computers in my past but for the newbs (been playing around on here for 6 years and I still think of myself as a newb) I would definitely recommend creating a virtual box and testing it out on here. If you break it, you don't break your system. If you need any help installing, let me know and I'll walk you through what I can.

---

### Post by MrManican on 2013-08-07
FYI: I am currently using Oracle Virtual Box v4.2 and Ubuntu 13.04. I'll update you with any issues I find/resolve.

---

### Post by Julian1968 on 2013-08-08
Thanks

Im already set up with the same Virtualbox and Ubuntu version. Is slow and clunky at times. maybe it just needs tweaking

---

### Post by TheFu on 2013-08-08
> **Julian1968 said:**
> Thanks

Im already set up with the same Virtualbox and Ubuntu version. Is slow and clunky at times. maybe it just needs tweaking

[http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox) explains how to optimize VM settings for fastest performance. It uses VirtualBox terms, but the ideas apply to any VM hypervisors.  ESX, ESXi, Player, Workstation, KVM, Xen ... doesn't matter.

I see now that you want to run Photoshop?  Well, where I live, Photoshop is a $700+ program, so running it inside a VM seems completely crazy to me.  $700+ programs are meant to have dedicated computers used just for that single purpose. Also, since photoshop is highly graphics oriented and virtualization is weakest when it comes to virtualizing GPUs, that is another _nail in the coffin_ for using any VMs with photoshop.

I know that professionals will say that **The Gimp** is not a replacement for Photoshop - but if you aren't earning money with any Adobe product, then you should avoid using them completely from a lock-in and security standpoint - including Acrobat and Photoshop.  This is a hard pill to swallow for hobbyists - but it is best to learn ANY other tool over the adobe suites sooner than later.

I am not a photoshop user, but I do use MS-Visio. There simply is no replacement for Visio... to me. It is such a cornerstone in my consulting business that switching to other alternatives just isn't possible.  I know that the company is being reamed on license costs, but even at those prices, we earn so much money due to the pictures that is just doesn't matter. Painful to admit, but true. Anyway - I understand the photoshop stance, as you can see.  BTW, I'm always looking for replacements to MS-Visio and have seen a few $300 challengers recently ... they those still only work on Windows and will not run in WINE + LibreOffice.

Since I doubt anyone will actually give up photoshop, they should at least give up running it inside a VM.

---

### Post by Julian1968 on 2013-08-08
Thanks Fu

---

### Post by Kalibur on 2013-08-08
I think you need to try out Virtual Machine Manager (virt-manager) its in the Ubuntu Software Centre its simple to use and has virtually no limitations, I started using in virtual-box when I was transitioning into Linux but I ditched soon after discovering virt-manager.  Fast foward to today my vms are hosted on a server in the spare room at home and I connect and run them from anywhere in the world with a decent network connection or from the leaving room. :)

---

### Post by TheFu on 2013-08-08
> **Kalibur said:**
> I think you need to try out Virtual Machine Manager (virt-manager) its in the Ubuntu Software Centre its simple to use and has virtually no limitations, I started using in virtual-box when I was transitioning into Linux but I ditched soon after discovering virt-manager.  Fast foward to today my vms are hosted on a server in the spare room at home and I connect and run them from anywhere in the world with a decent network connection or from the leaving room. :)

virt-manager completely rocks for KVM. I've never used it for any other VM technology.  KVM is fantastic for server-on-server VMs and it is getting better for desktop-on-server use via remote access (Spice or NX).  Plus virt-manager uses ssh connections, so non-local management of the VMs doesn't require a GUI desktop on the VM host / server.

As for having remote access from anywhere in the world, I'd rather NOT have my hypervisor available that way.  I use NX - FreeNX server and NoMachine's nx-client on Linux or Windows.  The FreeNX server runs only inside a clientOS, not on the hypervisor.  NX uses ssh for the remote connection, so no extra VPN or ports need to be opened beyond ssh. The ssh port is still used for normal ssh too.  The remote desktop feels 2-3x more efficient than RDP or VNC solutions - plus both of those require a VPN to be secure.  Setting up FreeNX is a little more complex than most applications, but worth it.  Google "ubuntu freenx" for instructions and be certain to follow them extremely carefully. Don't skip around and be certain you understand what each step does.

I've used NX from 5 continents. It works.  The only strong recommendation is to use a router port translation to listen on port 443 on the public internet side, so businesses and hotels don't block the connection. It is surprising how many places block "non-standard" ports ... basically, if it isn't web or email traffic, most places filter it.

---

### Post by Kalibur on 2013-08-08
Thanks TheFu, I have never come across FreeNX it seems like something I should toy with a bit definately.

About my KVM environment its quite advanced actually.  I do not make my hypervisor open to the public at all, my VMs are basically on the same subnet as my phyisical machines and each VM has one or more ip address on the physical network.  So I do not have to connect to the host machine to work on a VM and so using router/firewall port redirection I can dedicate each service to a particular VMs ip address.  I can virtually do everything that products like VMware ESI offer including live migrating VMs from one Virtual Host to another but you have to get you hands a bit dirty to setup the servers and network level storage.  From public network I use ssh or get my laptops VMM to connect to my home VM host (ssh in the background).

---


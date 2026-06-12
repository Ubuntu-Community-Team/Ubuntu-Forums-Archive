---
title: "server width 2 virtual machines"
date: 2008-12-29
forum: Server Platforms
---

### Post by sartic on 2008-12-29
I will play width this idea. 
1 Ubuntu server (file server and pop3 mail server)
2. two virtual machines: pfsense and mikrotik
Server will have 1 lan, Pfsense 2 LANs and mikrotik 2 LANs

Suggestions?
Server 32bit or 64bit? Machine will be AMDx2,2GB,320GBx2 HD, 1LAN onboard and 4xLAN on PCI.
What virtual software? VBox, Zen, Wmware... ? 32 or 64 bit (if OS is 64bit?)
What software has option to start multiple virtual OS from command line?
Any hints or url to start before?
Thx...

---

### Post by Drezard on 2008-12-29
Im running 8 Virtual machines (all used for testing) on a Core Duo 2 32bit 2.5Ghz, 2GB ram, 250GB harddrive machine. 

I would advise using Vmware, its really easy for newbies to learn, its a point an click environment. 

Make sure you use jeos as your basic

Daniel

---

### Post by sartic on 2008-12-31
Jeos is only server 4 virtual appliance or... ?

---

### Post by windependence on 2009-01-01
No, you don't have to use Jeos, he is just suggesting it for Ubuntu stuff since it's small and made for appliances. If you are going to use pfsense, I have had great luck with Vmware ESXi (free) and VMware Server. If you can use ESXi, it needs no underlying OS, and runs on bare metal.

-Tim

---

### Post by sartic on 2009-01-03
Thx 2 both, i will get my machine next week. I dl esxi and jeos.

---

### Post by albinootje on 2009-01-03
> **sartic said:**
> 
What virtual software? VBox, Zen, Wmware... ?

Personally I find the free of charge VMWare server a pain to work with.

I like VirtualBox much better when it comes to the user interface and command line options, installing/upgrading/configuring (and the license!).
VirtualBox now has host interface support in version 2.1

Why don't you test VMWare and VirtualBox and see which one you prefer.

Concerning Xen.
I've always found Xen very interesting, but it's not so easy to set up and work with in Ubuntu or Debian.
My impression is that in e.g. Fedora or CentOS it's a bit easier and more integrated.
A friend of mine recommended me to forget about Xen, and go for KVM, the rather new hardware based Linux virtualisation.

---

### Post by windependence on 2009-01-03
You may not be aware that VMware now has two products that are free (as in beer). There is VMware Server, which requires an underlying host OS, and VMware ESXi which requires no host and has just a 32MB footprint. ESXi is a much better product and install is much much easier. Administration also uses a nicer interface.

I agree, if Xen would get their act together and make it simpler to set up it would be a great product and I would be using it in production. Unfortunately, right now, VMware is the most mature solution out there for production use.

-Tim

---

### Post by albinootje on 2009-01-03
> **windependence said:**
> You may not be aware that VMware now has two products that are free (as in beer). There is VMware Server, which requires an underlying host OS, and VMware ESXi which requires no host and has just a 32MB footprint. ESXi is a much better product and install is much much easier. Administration also uses a nicer interface.

Interesting.
Unfortunately VMWare wants a registration before downloading the "free" of charge ESXi. 
But thanks for this information anyhow! :)

> 
I agree, if Xen would get their act together and make it simpler to set up it would be a great product and I would be using it in production. Unfortunately, right now, VMware is the most mature solution out there for production use.

Well, there's Xenexpress :
[http://www.howtoforge.com/virtualization_with_xenexpress](http://www.howtoforge.com/virtualization_with_xenexpress)

-> Correction... After Citrix bought "Xen", it's no longer available as a download, it's now called Xenserver.

And some interesting GUI interfaces for Xen.
There are also some interesting howtos for Xen and clusters.

I think the PR management of Xen could have been a bit better ;-)

---

### Post by windependence on 2009-01-03
Thanks for the Xen stuff. I am always looking for a more open solution for my clients.

You know, having to sign up for a download is really not a horrible requirement if the product is free and is half decent. ESXi was over $500 before august of this year. they only made it free because of Micro$oft's VM software.

-Tim

---

### Post by namaku0 on 2009-01-08
> **windependence said:**
> You may not be aware that VMware now has two products that are free (as in beer). There is VMware Server, which requires an underlying host OS, and VMware ESXi which requires no host and has just a 32MB footprint. ESXi is a much better product and install is much much easier. Administration also uses a nicer interface.

I agree, if Xen would get their act together and make it simpler to set up it would be a great product and I would be using it in production. Unfortunately, right now, VMware is the most mature solution out there for production use.

-Tim

I am new to ESXi, but if I am not wrong the tool to administrate
the ESXi is not free. So if you want to create VM, manage VM, etc
you still need to buy it.

---

### Post by Masuran on 2009-01-08
> **namaku0 said:**
> I am new to ESXi, but if I am not wrong the tool to administrate
the ESXi is not free. So if you want to create VM, manage VM, etc
you still need to buy it.

If you want VirtualCenter to manage your VM's you need to buy a license. You can easily create VM's and manage them via remote command line.

---

### Post by windependence on 2009-01-08
> **namaku0 said:**
> I am new to ESXi, but if I am not wrong the tool to administrate
the ESXi is not free. So if you want to create VM, manage VM, etc
you still need to buy it.

This is one problem I have as a VMware partner. They really suck at telling people how to use their product.

The Virtual Infrastructure Client (VIC) is free. Once you get ESXi set up, it tells you right on the setup screen to go to the server's IP address to download the management tool. Also, there is a web based management tool, but it's not as full featured as the VIC. There are also many third party tools for managing VMware VMs since it's by far the most used virtualization software out there. As was stated, you can also use the RCLI if you want to manage it totally from the command line. There are tons of options available to you. If you have any qauestions I would be happy to help you. VMware also supports the largest number of guest OSs on the planet. That's why I don't use Virtual Box. I need FreeBSD support.

-Tim

---

### Post by windependence on 2009-01-08
> **Masuran said:**
> If you want VirtualCenter to manage your VM's you need to buy a license. You can easily create VM's and manage them via remote command line.

Yes, but you don't NEED virtual center to run your VMs. You can use the VIC, the web interface, or a third party tool to manage your VMs.

-Tim

---

### Post by albinootje on 2009-01-08
> **windependence said:**
>  That's why I don't use Virtual Box. I need FreeBSD support. 

FreeBSD doesn't run well in VirtualBox ? 
As a (plain) FreeBSD user I'm curious to hear more details.

---

### Post by windependence on 2009-01-08
Says "works partially" on their site and 6.2 has problems which is what most of my production boxes are. Also, it's not a bare metal hypervisor, still requires a host OS and I don't see where you could use FreeBSD for the host. Open Solaris would be OK, but I like the bare metal stuff as you can run it off a compact flash card, and there is no additional layer there. Trust me, I have checked them all out and they all have something I don't like. KVM requires VT enabled hardware. Xen is just screwy to set up and Citrix has now crapped on the OSS version. Virtual Box doesn't run on bare hardware and I am not sure it supports FreeBSD in a production environment. See what I mean? VMware fits what I need, and I know how to do it free. Most people have all the common misconceptions in this thread and more because of course VMware wants you to buy the paid product so they bury the details of the good free stuff.

I would gladly try anything else with great features and good OS support if there was one. ESXi is a great product and runs really really rock solid. You do not need to pay for any licenses to get it working and use a complete GUI for administration.

-Tim

---

### Post by Masuran on 2009-01-09
> **windependence said:**
> Yes, but you don't NEED virtual center to run your VMs. You can use the VIC, the web interface, or a third party tool to manage your VMs.

-Tim

I know, guess my explanation wasn't too clear :)

Are you sure ESXi has the web interface? VMware claims it doesnt. Wouldn't know cause I'm used to setting up ESX and VC only.

---


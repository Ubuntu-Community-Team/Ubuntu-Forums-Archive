---
title: "Benefits of VMWare Tools in JeOS?"
date: 2009-03-29
forum: Server Platforms
---

### Post by misza1313 on 2009-03-29
Hello.
I've been recently testing the JeOS Server distribution under VMWare Server 2.0.
I was pleasantly surprised after the first installation - the system fits nicely into a 0.5G disk image, and the memory usage of the guest (on idle) clocked around 30M, which gives hopes for deploying a numer of small (say, 128M) specialised vmachines.

I remembered from my previous experiments (mostly with desktop guests) that VMWare Tools provide a significant boost to the guest when installed, so I went ahead and tried that too.

This is when things start looking grim. First of all, I had to resize the machine's disk in the process: A) the tools themselves stated a requirement of 200M space for installation (on top of the .tar.gz requiring about as much to just unpack the installer!), then B) I had to apt-ize linux-headers and build-essential. In the end, it hardly fits into a 1G disk (and I still haven't installed any applications yet!). Second, the memory usage is now around 70M, which is no longer a "tiny" footprint (again, no actual applications yet).

To the point, a big question to people with more experience in this matter: what are the MEASURABLE GAINS from installing VMWare Tools on a Ubuntu JeOS guest? Maybe it's entirely a waste (the "juice" is supposed to be optimized already)?

Regards,
Misza

PS: I am currently testing this inside VMWare Server 2.0 under WinXP on a laptop, but ultimately planning to deploy on a minimal "netinst" Debian on a dedicated machine.

---

### Post by windependence on 2009-03-30
It's a total waste to do this because the only thing gained is usually on Windows machines, and on Linux it's mostly on the graphical side. I don't personally see the point in doing this. Also, tools should be in the VMware system. It's usually just a virtual CD that needs to be mounted and you use a command to install it from there. There should be nothing to download or change in order to install them.

If you want small, why don't you use the ESXi bare metal hypervisor? It's footprint is only 32MB, and no host OS is needed. It's free too. 

If it's the guest you want small, I would suggest taking a look at FreeBSD or OpenBSD. What are you running on the guests?

-Tim

---

### Post by misza1313 on 2009-03-30
Thanks for the reply. I figured that Tools had mostly to do with performance of the graphical environment, ie useless to install on server guests, but really needed confirmation.

On a side note, indeed the VMWare Server allows me to mount an install CD inside the guest, but there are two files there: an .rpm and a .tar.gz. The latter has to be uncompressed first, which requires extra temporary space (plus, it will need even more of that to build all the necessary modules).

I wondered if the ESXi suggestion would come up. :D
As much as I love the bare-metal idea, that is ruled out for the time being. As it is not truly free - management is best done using the VI Client, which costs a lot for a starter company (additionally, VI runs only on Windows). Without it, you are left with a clunky text console. I'm not giving up the brilliant web-based management in VMWare Server 2.0 for that.

The size of the host is not as important as its performance - I want a minimal overhead and the Debian netinst with no services installed seems to fit the purpose (don't you love apt?). Unless you have other suggestions?

My guest OS of choice is the [JeOS Ubuntu Server](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos), a cut-down version of the main Server Edition, supposedly optimised for being a guest. We are already using several Ubuntu servers (based on the full edition), so that's less likely to change (we'd like a uniform architecture across our servers).

--Misza

---

### Post by windependence on 2009-03-30
I'm familiar with JeOS. 

You are incorrect about the VI. It is not apparent from the documentation, but after you install ESXi, you bring up the server IP address in a browser, and then you can download the FREE VIC (Virtual Infrastructure Client). I could even send you the executable. It IS indeed free and very nice. You could still run Ubuntu JeOS as guests. Performance would be MUCH better on the bare metal hypervisor.

I'm still curious as to what application you are running on the guests. 

-Tim

---

### Post by misza1313 on 2009-03-31
You're correct that it's not apparent from the documentation - only things I ever saw mentioned were the complete VMWare Infrastructure or a telnet-like console (or was that ssh?). I might give it a shot when I get my hands on some more hardware - I'm afraid though that ESXi might whine about unsatisfied hardware requirements - what we're using for now are (don't laugh!) PCs retired from desktop usage - at least VMWare Server is not picky about what's it run on.

Plus, VIC still only runs on Windows, doesn't it? In a company trying to pull itself from scraps we use whatever we have; one particular admin only uses Mac, for example - with a web interface, he'd at least have a chance.

If you're wondering about particular applications, I can name a few needed ones: web server (virtualized for short RTO), LDAP server (virtual for HA), file server (possibly; maybe the host OS would fit better in this role), mail server, IRC server.

--Misza

---

### Post by dreamgear on 2009-09-23
The VMware tools do a few more things for (or to) a linux guest that are relevant to server use.  For one the vmware-guestd can shut the guest systems down gracefully when the host is being shut down.  Without this, if you forget and shut the host down first, the guests experience an abrupt halt.  That could be bad.

There's also the vmware-memctl driver, which (roughly speaking) allows the host to give memory to and take memory away from the guests dynamically.  This might be valuable on your older hardware.

---

### Post by t3r0 on 2009-09-23
> **dreamgear said:**
> The VMware tools do a few more things for (or to) a linux guest that are relevant to server use.  For one the vmware-guestd can shut the guest systems down gracefully when the host is being shut down.  Without this, if you forget and shut the host down first, the guests experience an abrupt halt.  That could be bad.

There's also the vmware-memctl driver, which (roughly speaking) allows the host to give memory to and take memory away from the guests dynamically.  This might be valuable on your older hardware.

Yes, and in addition to that it includes the drivers for all the vmware virtual hardware like for example the vmxnet NICs.. 

So if you really want to get all out of your VMs its a must to install ;) 

- Tero

---

### Post by windependence on 2009-09-23
It contains WINDOWS drivers. Linux drivers are contained in the linux kernel. Drivers in Linux are NOT like drivers in Windows. You usually don't have to specifically load a driver in any form of 'nix unless they are not already in the kernel. 

That being said, I load tools on all my servers if I can. Many of the FreeBSD guests I use cannot load tools so they run without, and I might add there have been no problems (under ESXi).

-Tim

---

### Post by t3r0 on 2009-09-24
> **windependence said:**
> It contains WINDOWS drivers.

VMware tools for Linux contains the Linux drivers.
> **windependence said:**
> 
Linux drivers are contained in the linux kernel. 

Yes, some of them are build in to the kernel.
> **windependence said:**
> 
Drivers in Linux are NOT like drivers in Windows. 

Yep.

> **windependence said:**
> You usually don't have to specifically load a driver in any form of 'nix unless they are not already in the kernel. 

Yes, and in this case for eaxample vmxnet3 is one of those drivers that dosent come with any Linux distro so you have to load the module   into the running kernel to use the NIC.

---


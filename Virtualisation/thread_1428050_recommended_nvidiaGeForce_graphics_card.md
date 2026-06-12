---
title: "recommended nvidia/GeForce graphics card?"
date: 2010-03-12
forum: Virtualisation
---

### Post by Beowulf.1000 on 2010-03-12
Any recommendations for an nvidia (GeForce) graphics display card to use for virtualization with Virtualbox (Ubuntu hosting a virtual Windows) in order to get the best graphics possible in the virtualized Windows?

I have currently have an nvidia Geforce 7900 256MB ram. A pretty good car, but I am more than willing to shell out the pesos for a butt-kicking screaming nvidia card that would bump up my graphics performance a few notches.

---

### Post by dcstar on 2010-03-13
> **Beowulf.1000 said:**
> Any recommendations for an nvidia (GeForce) graphics display card to use for virtualization with Virtualbox (Ubuntu hosting a virtual Windows) in order to get the best graphics possible in the virtualized Windows?

I have currently have an nvidia Geforce 7900 256MB ram. A pretty good card, but I am more than willing to shell out the pesos for a butt-kicking screaming nvidia card that would bump up my graphics performance a few notches.

VMs use their own 3D drivers in their own environment. While some VM environments support 3D it still has to go through the console video hardware of the system that you are accessing the VM on and that will be the limiting factor.

Just find something that is fully Ubuntu compatible for your Ubuntu host system.

---

### Post by Cato2 on 2010-03-15
There are some early attempts in Virtualbox and VMware at DirectX virtualization, e.g. [http://www.snoopyonskittles.com/2009/06/18/virtualbox-30-with-theoretical-directx/](http://www.snoopyonskittles.com/2009/06/18/virtualbox-30-with-theoretical-directx/) and [http://pubs.vmware.com/ws7_ace26/ws_user/ws_vidsound_d3d_enabling_guestos.html](http://pubs.vmware.com/ws7_ace26/ws_user/ws_vidsound_d3d_enabling_guestos.html)  Haven't used these,  but I would expect that more games run well using WINE (ideally the Crossover Games version for easy setup) than with VMware or Virtualbox, as the VM platforms are newer to the DirectX emulation game.

Translation from DirectX to OpenGL is required in the VM, and the underlying host and card must support enough features - not unlike what WINE does with DirectX in fact, where it runs a lot better on NVidia cards. The VM engines may even be using some WINE code, translating to OpenGL just like WINE does - sort of paravirtualization.

[http://www.dedoimedo.com/computers/virtualization-3d-support-virtualbox.html](http://www.dedoimedo.com/computers/virtualization-3d-support-virtualbox.html) has some setup details for Virtualbox and VMware. [http://vmetc.com/2009/07/18/video-of-working-windows-directx-games-in-virtualbox-302-on-ubuntu-904/](http://vmetc.com/2009/07/18/video-of-working-windows-directx-games-in-virtualbox-302-on-ubuntu-904/) has some more details for Virtualbox.

Some DRM may not work in a VM, by design (e.g. Metaboli, which lets you rent Windows games) - see [http://www.adventuregamers.com/forums/showthread.php?t=23531](http://www.adventuregamers.com/forums/showthread.php?t=23531).  Steam's DRM works fine under WINE, but many newer games sold through Steam also add their own DRM on top.  So you will need to check on the DRM schemes of games you want to play - all fairly horrible...

My experience on WINE is that some older games work well, particularly Half Life 2 and others supported by [Crossover Games]("http://www.codeweavers.com/products/cxgames/") (who employ some of the WINE developers).  However, features such as graphics card antialiasing (4xMSAA etc) are very hard to get working, and in fact I've given up on my setup (NVidia GTX260 with 195.x drivers and Crossover Games 8.1.4).  Also, WINE doesn't support 5.1 surround sound at all.  However, if you buy Crossover Games you do get good support which can help with games that almost work.

There is some work by Xen on PCI Express direct mapping but that's mostly intended to allow efficient access by VM guests to a real NIC, it seems, so I would focus on VMware, Virtualbox and/or WINE/Crossover.

You would need to research your whole setup very carefully to have a chance of this working, but I'd be very interested to hear how you get on!

For Windows games, I'm looking at using an Ubuntu VM hosted on Windows, with most of the games running natively in Windows, and rebooting into the real Ubuntu (same raw disks as the VM) for games that do work under WINE.  See [http://ubuntuforums.org/showthread.php?t=1430279](http://ubuntuforums.org/showthread.php?t=1430279)

---


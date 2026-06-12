---
title: "Old Toshiba -- need Linux"
date: 2005-12-03
forum: The Cafe
---

### Post by greenwom on 2005-12-03
Well I'm working with a buddy of mine on bringing life to an old laptop - and I'm having trouble.

It's a Toshiba Satalite Pro 430CDT, a Pentium 1, 4 gig hard drive and only 32 megs of ram.  The problem is it has a 16 bit pcmcia port and no network port.

We have a 16-bit D-link card that needs hostap to load firmware. 

I need a good distro to get that wireless card working.
I've tried knoppix and damn small linux.  Both of these live CD's run great on the machine and install smoothly to the hard drive.  I was just having all sorts of problems getting all of the hostap utils and drivers working. (mis matches of kernel and packages, things of that nature.  Kernel patches not working...)  

Any buddy get something like this running. 

(Don't ask why we want to get this running, we've already forgot.) :)

---

### Post by aysiu on 2005-12-03
Are you sure Ubuntu will work better with the wireless card? If so, 32 MB of RAM is pretty modest and officially below the Ubuntu minimum requirements. Maybe Ubuntu-Lite or Mini-RAM might help?

[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

---

### Post by Iandefor on 2005-12-03
My suggestion is to get a regular pcmcia network card, not a wireless nework card. Wireless is usually spastic under just about *any* Linux distro.

---

### Post by greenwom on 2005-12-03
I wouldn't say wireless is spastic, I've configured 3 laptops (ndiswrapper) and one wireless desktop with hostap.  Everything has worked great for me.

The problem with this old laptop is I can't get it online for anything.  My guy does have a old pcmcia modem but no one has dial-up.  We could install and then dial in (if the disrto has some sort of software for that).

Damn Small Linux has a great wireless tools app

---

### Post by N8K99 on 2005-12-06
I have a Toshiba Tecra 500CDT that has a PCMCIA ethernet/modem card. I have installed the server version of Breezy and it works fine - I did have full on 5.04 installed on it at one point. But the running battle I have had as a n00b to linux ( <6 months experience) is that getting that dang card to work. I know that there is something I can type in at CLI and would be happy to do that, just so that the card is seen by the software ( I know it worked under NT before I switched over) but I need to find the proper command and my search thus far has not yielded a solution. Help! Please.

---

### Post by az on 2005-12-06
My Toshibe 460 CDT with the same 16-bit pcmcia slot uses the same kind of wireless card (prism) and by default, hotplug will load orinoco drivers.  They work fine.  I think the hostap drivers are also available in the stok kernel, but Imay be wrong.  Anyway, there are three different drivers that work with prism chipsets.

I filed a bug report about pcmcia not being loaded (i83265 module) by the kernel in Hoary.  Laptop-detect was hacked for breezy to detect whether you have a battery present or not.

If you install the ubuntu-desktop package, it will bring in all the apm stuff required for hotplug to be able to find the pcmcia slot and load the drivers.  Otherwise, you have to load i83265 by hand (or put it in /etc/modules)

---

### Post by greenwom on 2005-12-06
Well Thanks for the input.   I tried the iso from ubuntu-lite.  It was a hoary release and I had dependancy troubles trying to install debs that burned to a CD (gcc, make, build-essential).  I'm not an super-linux-user but I thought bringing these debs would be easy.

Azz> hotplug will load orinoco drivers. They work fine. I think the hostap drivers are also available in the stok kernel, but Imay be wrong. Anyway, there are three different drivers that work with prism chipsets.

If you install the ubuntu-desktop package, it will bring in all the apm stuff required for hotplug to be able to find the pcmcia slot and load the drivers. Otherwise, you have to load i83265 by hand (or put it in /etc/modules)
How do I install from the breezy cd and get hostap running (if it's in the kernel) and how any guidance on the ubuntu-desktop package?

I'm trying to do the 'server' install with swap turned on so I can make it throught the install.  This worked for the ubuntu-light iso should I try it with the breezy cd?  Is there anything special I would need to do at install to get hostap / pcmcia going?  I'm on the last straw with helping on this old laptop. :)

---

### Post by az on 2005-12-06
Install using the server option.

During the network detection part, Got to virtual console 2
CTRL-ATL-F2

modprobe i83265

The pcmcia card's light should come on.  The card should be activated by hotplug and you should be able to configure your network with it.  Once you install, then think about running hostap.

---

### Post by greenwom on 2005-12-13
I haven't gotten the chance to run that option yet .

I'm going to try it tonight and I'll post the findings

---


---
title: "Emulating Ubuntu"
date: 2007-05-31
forum: The Cafe
---

### Post by Dark-Ace on 2007-05-31
I really don't wanna install anything and i already have Microsoft Virtual PC 07 and i was wondering if there were any links to somewhere where i can get a .vmc file for a Ubuntu Emulation?

---

### Post by starcraft.man on 2007-05-31
> **Dark-Ace said:**
> I really don't wanna install anything and i already have Microsoft Virtual PC 07 and i was wondering if there were any links to somewhere where i can get a .vmc file for a Ubuntu Emulation?

Uh... not off the top of my head (i'm certain MS wouldn't distribute a linux ready package). I also don't think virtual PC a very good VM IMO... but to each his own. I'd just download the live CD and boot into it, thats the shortest path with least effort to a functional desktop of Ubuntu. I'd also recommend VMware server/Virtual Box over Virtual PC but thats up to you I suppose.

---

### Post by matthinckley on 2007-05-31
Last I knew Microsoft Virtual PC wouldn't run linux

---

### Post by maniacmusician on 2007-05-31
yeah, sorry, virtual pc is quite horrid. virtualbox is probably your best bet.

---

### Post by Dark-Ace on 2007-05-31
Well anyopne know where to find some Linux software for Virtualbox?

---

### Post by Cyvros on 2007-05-31
> **matthinckley said:**
> Last I knew Microsoft Virtual PC wouldn't run linux

It can, but very, very badly. Xserver doesn't start properly, the VPC window goes out of proportion and sometimes it doesn't even get to the GRUB menu... on a Live CD.


> **Dark-Ace said:**
> Well anyopne know where to find some Linux software for Virtualbox?

What do you mean? VirtualBox is an emulator, much like Virtual PC, but free and open-source and with better Linux support, so you should be able to install Ubuntu in it rather easily.

You can always use a free (beer) version of VMware and get an Ubuntu appliance off the VMware website.

---

### Post by Dark-Ace on 2007-05-31
Can someone tell me how to install ubuntu on it then, i already made an instalation cd from the site so how do i get it on VirtualBox?

---

### Post by Cyvros on 2007-05-31
> **Dark-Ace said:**
> Can someone tell me how to install ubuntu on it then, i already made an instalation cd from the site so how do i get it on VirtualBox?

After you've launched VirtualBox, click on the New icon - it'll start a wizard taking you through the steps of making a new virtual machine. Depends on your hardware, you'll need to do some tweaking (if you have 512 megs of RAM, I wouldn't recommend giving the VM more than 256 megs - for 1 gig physical RAM, I don't let a VM use more than 512 megs, etc.).

Once you get through the Wizard, start the virtual machine - there should be a menu (second from the left, I can't remember the name - it's something like Hardware) that allows you to manage the hardware mounted by the VM. There should be a CD-ROM sub-menu - go into there and select the option that says something like "Use Physical Drive".

If need be, restart the VM through the File menu and wait for the Live CD to boot. The rest is just the (well-documented) install sequence.

Hope it helps. :)

---

### Post by Dark-Ace on 2007-05-31
Yay, i don't see that Hardware menu and i don't see use Physical drive either...i'm using VirtualBox not Virtual PC anymore.

---

### Post by doogy2004 on 2007-06-01
Use VMware server it is free and runs on windows and linux.  Then download the ubuntu ISO and use it in a virtual machine.  Install Ubuntu on the vm and you are done.

---

### Post by petersjm on 2007-06-01
I came across this the other day. It's called Wubi. It's an unofficial installer for Ubuntu on Windows - runs, apparently, like any other program in Windows and doesn't require HDD partitioning or anything. Haven't used it, though, as I don't have Windows anymore, but might be worth checking out... [http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)

---


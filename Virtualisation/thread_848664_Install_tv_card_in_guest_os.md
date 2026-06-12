---
title: "Install tv card in guest os ?"
date: 2008-07-03
forum: Virtualisation
---

### Post by Drakkor on 2008-07-03
I'm trying to install a tv card,but the guest os (XP) fails to see the hardware (card) says it's not installed. :confused:

---

### Post by funkydan2 on 2008-07-04
Which virtual machine software are you using?

Is the card working under the host OS (Ubuntu)?

---

### Post by Drakkor on 2008-07-05
Yeah,thanks,funkydan2, I'm using VirtualBox and in Ubuntu the host it plays fine with tvtime, but it seems that XP guest does not see the tv card.

---

### Post by funkydan2 on 2008-07-05
Is your TV card USB or PCI?

If it's PCI, I don't think that it's possible to access it from the guest OS.  
If it's USB I think that if you install the closed source edition of VirtualBox you can allow the guest OS to access USB devices directly.  (I think there's info about this in the ubuntu wiki.)

---

### Post by Drakkor on 2008-07-05
Yeah,it's a pci card internal, that's kinda what I thought, actually trying to help a friend out with this,but he has an ATI card, which is not linux friendly,so I figured we could get it on VB XP,lol, and it won't work with Vista either,guess he's gonna have to get another TV card :mad:

---

### Post by igwk on 2008-07-05
Current virtual machine software does not allow the guest operating systems to directly access hardware like a TV card.  They virtualize an entire machine and all of the hardware in it.  If you want to make something like a PCI TV card work, you'll have to wait until one of the virtual machine monitors adds support for Intel VT-d technology.

---


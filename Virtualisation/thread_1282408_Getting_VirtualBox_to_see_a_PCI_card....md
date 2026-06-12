---
title: "Getting VirtualBox to see a PCI card..."
date: 2009-10-04
forum: Virtualisation
---

### Post by Marlonsm on 2009-10-04
I have a (cheap and very weird) PCI TV tuner card that I can't get it to work in Ubuntu, I've tried everything.
So thought that it could work in a virtual Windows XP, just like it works in the real Windows XP. Problem is: so far I haven't found a way to make the virtual machine see the card. Is it really possible or is the guest OS limited to the virtual hardware?

---

### Post by howefield on 2009-10-04
> **Marlonsm said:**
> Is it really possible or is the guest OS limited to the virtual hardware?

Pretty much a waste of time, if it doesn't work in Ubuntu, you're not likely to get it to work in Virtualbox.

---

### Post by Marlonsm on 2009-10-04
The card does work in Windows XP when it's not running in a VM.

---

### Post by howefield on 2009-10-04
You're stuck with the virtual drivers. 

The problem is there are none for tv tuners.

---

### Post by Marlonsm on 2009-10-04
Ok, then, I should have known that buying that cheap card was not a good idea...

---

### Post by Perryg on 2009-10-06
AFAIK there are no virtualizers out yet that can capture PCI cards.

---

### Post by starfry on 2009-10-13
As far as I know, KVM supports PCI card assignment. I haven't tried it though. Unfortunately for KVM you need to have hardware virtualisation in your CPU.

---


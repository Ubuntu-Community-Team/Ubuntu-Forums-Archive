---
title: "How to add an ATA PCI card?"
date: 2010-03-11
forum: Server Platforms
---

### Post by Donny Bahama on 2010-03-11
I need to add a 2 port ATA PCI card to my (headless/no-GUI) server. I'm still pretty new to Ubuntu/Linux so I have no idea what's involved in getting the card to be recognized, installing drivers, etc. I suppose it would be easy to just install the card then reinstall the OS and start over, but that seems rather extreme. What's the proper way of going about this?

---

### Post by NullHead on 2010-03-11
I can't say I've seen a Sata raid card that doesn't support linux. I'd assume that you can purchase one, turn off the PC, slap it in there, turn the computer back on and all will be well. 

Depending on what kind of card, a simple connect card, virtual raid, hardware raid, you'll need software to set it up, or to configure hard drive(s) in a bootup bios type menu before your OS loads. 

It all depends on what card you but, but I'd think about any card you buy would work fine.

---

### Post by Donny Bahama on 2010-03-13
It was a PATA card, but it didn't matter; you were right, Recognized at boot after installation and working great. Thanks!  *This is the second time I've assumed things would be a lot harder than they are. Maybe this time I'll learn the lesson!*

---


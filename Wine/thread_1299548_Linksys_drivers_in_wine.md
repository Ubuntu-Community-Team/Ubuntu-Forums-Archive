---
title: "Linksys drivers in wine?"
date: 2009-10-24
forum: Wine
---

### Post by nevets04 on 2009-10-24
I searched for linux drivers for linksys wireles adapter I have, but I couldn't find any. Can I run the drivers through wine?

---

### Post by Dark_Stang on 2009-10-24
No, the card is probably made by broadcom anyway. Almost all linksys network adapters are. Is it a USB, PCI, PCMCIA, PCMCIA Express card?

---

### Post by nevets04 on 2009-10-24
> **dark_stang said:**
> no, the card is probably made by broadcom anyway. Almost all linksys network adapters are. Is it a usb, pci, pcmcia, pcmcia express card?

usb

---

### Post by Dark_Stang on 2009-10-24
Run "lsusb" to see which card it is and post it. Post the entire output if you need help identifying it.

---

### Post by nevets04 on 2009-10-24
> **Dark_Stang said:**
> Run "lsusb" to see which card it is and post it. Post the entire output if you need help identifying it.

its a dual-band wireles-N usb network adapter model no. wusb600n

---

### Post by Dark_Stang on 2009-10-24
> **nevets04 said:**
> its a dual-band wireles-N usb network adapter model no. wusb600n

That's cool, but we need to know what the actual model number is. For example, my wireless card's model number is a BCM4311. So if you run "lsusb" in a terminal you should see it listed there, along with your other USB devices.

---

### Post by nevets04 on 2009-10-24
> **Dark_Stang said:**
> That's cool, but we need to know what the actual model number is. For example, my wireless card's model number is a BCM4311. So if you run "lsusb" in a terminal you should see it listed there, along with your other USB devices.

Im that usb at the moment, because I get the drivers. But isnt the model number wusb600n?

---

### Post by Dark_Stang on 2009-10-24
> **nevets04 said:**
> Im that usb at the moment, because I get the drivers. But isnt the model number wusb600n?
The linksys model number, sure. But linksys probably didn't actually make that card. Most belkin network cards are made by broadcom as well. So we need to figure out who actually made it and what the real model number of the card is.

---

### Post by nevets04 on 2009-10-24
nevets04@nevets04-laptopmain:~$ isusb
bash: isusb: command not found

I'm on ubuntu 9.04

---

### Post by Dark_Stang on 2009-10-24
> **nevets04 said:**
> nevets04@nevets04-laptopmain:~$ isusb
bash: isusb: command not found

I'm on ubuntu 9.04

lsusb (LSUSB, but lowercase, not ISUSB)

---


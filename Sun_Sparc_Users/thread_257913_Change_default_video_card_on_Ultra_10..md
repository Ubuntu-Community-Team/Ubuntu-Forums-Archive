---
title: "Change default video card on Ultra 10."
date: 2006-09-15
forum: Sun Sparc Users
---

### Post by chris_andrew on 2006-09-15
Hi,

I am currently using the built-in video card, on my Ultra 10.  I have fitted a better PCI card, and would like OpenPROM to "see" this as the default video output.

Anyone know how I do this?

Thanks,

Chris.

---

### Post by kmantronix on 2006-09-17
You just have to do this :

- type 

Ok> show-devs

Thid Will give you the device tree.

- Try to isolate the device path for the new Graphic Card.
I m not sure of what it should be, but you can ".properties" to get a bunch of information regarding the device you have moved to with "cd". Tip : At first use "cd" with no parameters to jump to the root of the device tree then move with "cd /pci@..."
up to what you think is the graphic Card. then do ".propoerties". there should be enough information to confirm what is the graphic card. You can also copy/past the show-devs in the forum. i could then tell you what is your graphic card.

- create a new alias for this graphic card
OK> devalias new-screen new_graphic_card_path 

- modify output-device

OK> setenv output-device new-screen

HTH,

---


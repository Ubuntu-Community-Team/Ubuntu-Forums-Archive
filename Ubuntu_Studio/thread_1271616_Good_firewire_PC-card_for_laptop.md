---
title: "Good firewire PC-card for laptop?"
date: 2009-09-21
forum: Ubuntu Studio
---

### Post by cbope on 2009-09-21
First of all, sorry for the cross-post, but I wasn't getting any responses in the hardware & laptops section. Here we go:

I have a Dell M70 Precision laptop which I intend to use for music production and editing. I will be purchasing an external firewire interface (most likely Edirol as they seem to be well supported) in the near future, but the laptop does not have a built-in firewire interface. So I need to purchase a good PC-card-based firewire card. Who makes a good card and/or chipset that is well-supported and known to work well with the apps in Studio? (Jack, Ardour, etc.) I want drivers in binary form, I have no desire to play around with source for this.

I have Studio 9.04 up and running well on the laptop and all built-in hardware is working, so the firewire interface is the last piece I need to get going.

TIA

---

### Post by kayosiii on 2009-09-22
Texas Instruments (TI) chipsets are generally concidered the best performing firewire chipsets under Linux (and for audio in general). Sourcing them is not particularly easy as very few vendors list what firewire chipset they are using. Though if you shop on line you can probably find what you are looking for though.

---

### Post by trulan on 2009-09-22
+1 for the TI chipset.

That being said, I have had zero success with using an express card for this purpose.  I purchased one (with a TI chip no less) because I thought the Ricoh chipset in my laptop's built-in firewire setup was bad (I've read many places that the Ricoh firewire chips are the worst for this.  But, the express card is useless and the built-in Ricoh chip works like a charm.  But since you have a PC Card you should be fine.

Here's a hardware compatibility doc from Presonus - you may find this helpful:
[http://www.presonus.com/media/pdf/hardware_compatibility.pdf](http://www.presonus.com/media/pdf/hardware_compatibility.pdf)

---

### Post by kayosiii on 2009-09-25
yeah I had the same problem with express card (unfortunately) it seems that expresscard can be built on top of PCI-x or it can be built on top of USB-2 in the later case it's pretty much worthless

---

### Post by texla on 2010-07-25
> **trulan said:**
> +1 for the TI chipset.

That being said, I have had zero success with using an express card for this purpose.   But, the express card is useless and the built-in Ricoh chip works like a charm.  But since you have a PC Card you should be fine.


So are the older PCI I and II expansion ports preferable over the more common express54 or express34 ports in choosing a laptop to add firewire to?  Or are you talking about something else? I'm having some questions about this in choosing a recording laptop with or with adding firewire. 

:-k

---

### Post by mango42 on 2010-07-26
> **texla said:**
> So are the older PCI I and II expansion ports preferable over the more common express54 or express34 ports in choosing a laptop to add firewire to?

No, Expresscard seems to work for most people, if it's going to work at all. TI chipsets can be found in the **Belkin** & **Lindy** offerings but that's only half the story as some laptops' card slots (eg: *some* Ricoh PCI chips) just don't seem to able to communicate with firewire i/fs at all. IBM Thinkpads being one of them, in my experience.

I often wonder how many of us here and over at **ffado.org** have redundant ExpressCards lying around collecting dust - perhaps we need to adopt the mythical ancient Greek witches approach, 3 of whom shared one eye... ;)

---
[http://soundcloud.com/bass-akwardz/](http://soundcloud.com/bass-akwardz/)

---


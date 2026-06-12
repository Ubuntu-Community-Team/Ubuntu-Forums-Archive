---
title: "Temperature collection with ext. probe for PCI slot"
date: 2010-06-30
forum: The Cafe
---

### Post by e24ohm on 2010-06-30
Folks:
I am looking for PCI hardware that has the ability to collect temperature readies from external probes. I would like the interface to be something simple, say via the cli that updates similar to the top command.

The idea is to make a cheap box that can monitor temperature. 

Thanks.

---

### Post by McRat on 2010-06-30
> **e24ohm said:**
> Folks:
I am looking for PCI hardware that has the ability to collect temperature readies from external probes. I would like the interface to be something simple, say via the cli that updates similar to the top command.
 
The idea is to make a cheap box that can monitor temperature. 
 
Thanks.
 
Thermocouples are analog devices that generate microvolts of electricity.  So they need a specific amplifier, then an analog-to-digital converter.  Most sensors are NOT like thermocouples.
 
National Instruments makes exactly what you are looking for, but $$.  They are the biggest name in digital data instrumentation.
 
I normally use a USB device (box) that is a 16 channel A/D converter but I need to buy thermocouples with amplifiers, about $100 for the pair.
 
I hook this kind of stuff up for racing and bench experiments, but I'm using DOS or Windows to save the data.

---


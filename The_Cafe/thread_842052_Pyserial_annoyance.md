---
title: "Pyserial annoyance"
date: 2008-06-27
forum: The Cafe
---

### Post by mattva01 on 2008-06-27
I'm attempting to use pyserial to control two solid state relays which each control capacitor discharge to a coil of an electromagnet. To accomplish this I am toggling  the logical value of the RTS and DTR pins  to set each solid state relay.The issue is the opening a serial device using pyserial causes both values to be set to an initial state of 1 , causing both banks of capacitors to be discharged at the same  time, which in my case can lead to a dangerous situation. Is there anyway to change this behavior?

---


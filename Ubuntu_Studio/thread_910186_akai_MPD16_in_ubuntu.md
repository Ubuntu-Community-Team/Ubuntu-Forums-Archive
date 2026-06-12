---
title: "akai MPD16 in ubuntu?"
date: 2008-09-04
forum: Ubuntu Studio
---

### Post by Dan Johns on 2008-09-04
I have recently purchased an akai MPD16 Midi controller. It works flawlessy under win XP on my studio's desktop, but hardy is not recognizing the device via usb on my laptop. (dell latitude d810) 

Is there any way to fix this? My next course of action is to buy a Midi to usb cable, but I don't want to waste money if that won't work either. Any help is appreciated.

---

### Post by Dan Johns on 2008-09-15
Hello all. I still need help with this issue. Thanks in advance.

---

### Post by Stochastic on 2008-09-15
Can you see it in the output of ```
lsusb
```

What about in the soundcards section of qjackctl's settings window?

A MIDI to USB cable will allow you to use the device, but if you can avoid spending extra money...

---

### Post by Dan Johns on 2008-09-15
yep, it's listed as follows 

> dan@magnum-mobile:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 09e8:0062 AKAI  Professional M.I. Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


---

### Post by Stochastic on 2008-09-15
> **Stochastic said:**
> What about in the soundcards section of qjackctl's settings window?

?

---

### Post by Dan Johns on 2008-09-16
No, not listed under qjackctl, or under sound preferences. lsusb is the only place that it shows up....

---

### Post by lordmyth on 2008-09-22
you might have to load the snd-seq module i think
"sudo modrpobe snd-seq"

---


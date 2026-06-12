---
title: "Lightsnake drivers"
date: 2008-06-03
forum: Ubuntu Studio
---

### Post by saphil on 2008-06-03
I have a Soundtech Lightsnake mic-to-usb cable.  I wanted to be able to record hi-quality audio from a real studio mic to my Ubuntu 8.04 box.  The thing comes with M$ drivers.  Has anybody had any   luck getting a usable Linux driver from that?

---

### Post by Stochastic on 2008-06-03
If you plug it into you computer then do ```
lsusb
``` what's the output?

---

### Post by saphil on 2008-06-03
This is what shows up when it isn't plugged in:
```

Bus 001 Device 004: ID 045e:0024 Microsoft Corp. Trackball Explorer
Bus 001 Device 003: ID 04f3:0103 Elan Microelectronics Corp.
Bus 001 Device 002: ID 03eb:0902 Atmel Corp.
Bus 001 Device 001: ID 0000:0000

```

This is with..
```
wolf@prospero:~$ lsusb
**Bus 001 Device 017: ID 1940:ac02**
Bus 001 Device 004: ID 045e:0024 Microsoft Corp. Trackball Explorer
Bus 001 Device 003: ID 04f3:0103 Elan Microelectronics Corp.
Bus 001 Device 002: ID 03eb:0902 Atmel Corp.
Bus 001 Device 001: ID 0000:0000

```

There is a usb hub, a keyboard and a trackball.

---

### Post by prismatic7 on 2008-06-04
From what i can make out, the Lightsnake is class-compliant, so it should Just Work (TM) with the usb-audio driver.  Does

```
cat /proc/asound/cards
```

show anything?

---

### Post by saphil on 2008-06-04
Wouldn't that be cool!

```

wolf@prospero:~$ cat /proc/asound/cards
 0 [Live           ]: EMU10K1 - SB Live [Unknown]
                      SB Live [Unknown] (rev.5, serial:0x2f1102) at 0xdc00, irq 12
 1 [U0x19400xac02  ]: USB-Audio - USB Device 0x1940:0xac02
                      USB Device 0x1940:0xac02 at usb-0000:00:07.2-2.1, full speed

```

So it shows up as a sound card, but I have no controls on it...

---

### Post by Stochastic on 2008-06-04
What program are you using to record?  It should be selectable in preferences inside that program (or qjackctl for that matter).

---

### Post by saphil on 2008-06-04
krecordmydesktop is supposed to be pulling audio from somewhere

gnome-sound-recorder 2.22.0 has all sorts of inputs from the regular SBLive card

kmix is the audio in and out program but none of the input channels seem to be this lightsnake.

---

### Post by kpaden on 2008-12-22
I found that my lightsnake is being held hostage by the usbhid module. I am trying to figure out how to separate them.

---

### Post by bodymind on 2009-02-07
which is lightsnake state now?

---

